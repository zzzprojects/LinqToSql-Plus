---
permalink: benchmark
---

## Problem
You perform benchmark tests for a method like BulkInsert, but you get very bad performance results.

### Solution
The performance issue may be caused by some common mistakes:

- Forget to JIT compile the library
- Include method not related to the test


## Forget to JIT compile the library
In C#, the code is compiled into IL by the compiler. Then when needed, the IL is compiled just-in-time (JIT) into the native assembly language of the host machine.

Additionally, some libraries like Entity Framework require some extra work like creating/reading the model. Some people report the first load taking several seconds
<!--
Entity Framework Extensions also takes some time to be compiled. It can take around 100ms the first time you use a method! So if you include it this time, your benchmark time is currently way higher than it should.!-->

### Solution
Invoke the method once before performing the benchmark tests

## Include method not related to the test
Someone once reported a performance issue and thought our BulkSaveChanges method was slow. We discovered he was including the time to Add every entity to the context.

The Add method was taking 99,9% of the total time while BulkSaveChanges only 0,1%.


| Operations | 100 Entities | 1,000 Entities | 10,000 Entities |
| :--------- | -----------: | -------------: | --------------: |
| Add        | 15 ms        | 1,050 ms       | 105,000 ms      |
| BulkInsert | 40 ms        | 90ms           | 400 ms          |


The Add method doesn't affect much the performance when adding 100 entities, but if you make your test with 10,000 entities:
 - Add: 99.6%
 - BulkInsert: 0,4%!

### Solution
Include only the method you want to benchmark.

## Good Example
Here is an example of how we normally do all our benchmarks tests

### Example
{% include template-example.html %} 
{% highlight csharp %}
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Diagnostics;
using System.Linq;

namespace BENCHMARK_Z.LinqToSql.Plus
{
    class Program
    { 
        static void Main(string[] args)
        {
             Benchmark benchmark = new Benchmark();
        }

        class  Benchmark
        {
            public string LinkToSQlConnectionString = "";
            public  Benchmark()
            {

                LinkToSQlConnectionString = ConfigurationManager.ConnectionStrings["LinkToSQlConnectionString"].ToString();

                // BENCHMARK using Stopwatch
                var clock_bulkInsert = new Stopwatch();
                var clock_SubmitChanges = new Stopwatch();

                var nbRecord = 1000;
                var nbTry = 5;

                var list = GenerateData(nbRecord);

                // BENCHMARK: JIT compile library first
                Test1(list, null);
                Test2(list, null);

                for (var i = 0; i < nbTry; i++)
                {
                    Test1(list, clock_bulkInsert);
                    Test2(list, clock_SubmitChanges);
                }

                var r1 = clock_bulkInsert.ElapsedMilliseconds / nbTry;
                var r2 = clock_SubmitChanges.ElapsedMilliseconds / nbTry;
            }

            public  void Test1(List<string> lines, Stopwatch clock)
            {
                using (var ctx = new CustomerContextDataContext(LinkToSQlConnectionString))
                {
                    var customers = new List<customer>();

                    foreach (var line in lines)
                    {
                        var customer = new customer();
                        // ...code...
                        customers.Add(customer);
                    }

                    if (clock != null)
                    {
                        // BENCHMARK: Only method we want to test
                        clock.Start();
                        ctx.BulkInsert(customers);
                        clock.Stop();
                    }
                    else
                    {
                        ctx.BulkInsert(customers);
                    } 
                }
            }

            public  void Test2(List<string> lines, Stopwatch clock)
            {
                using (var ctx = new CustomerContextDataContext(LinkToSQlConnectionString))
                {
                    var customers = new List<customer>();

                    foreach (var line in lines)
                    {
                        var customer = new customer();
                        // ...code...
                        customers.Add(customer);
                    }

                    ctx.customers.InsertAllOnSubmit(customers);

                    
                    if (clock != null)
                    {
                        // BENCHMARK: Only method we want to test
                        clock.Start();
                        ctx.SubmitChanges();
                        clock.Stop();
                    }
                    else
                    {
                        ctx.SubmitChanges();
                    }
                }
            }

            public  List<string> GenerateData(int nbRecord)
            {
                var list = new List<string>();

                for (var i = 0; i < nbRecord; i++)
                {
                    list.Add(i.ToString());
                }

                return list;
            }
        } 
    }
}
{% endhighlight %}

