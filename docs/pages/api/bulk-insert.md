---
permalink: bulk-insert
---

## Definition
`INSERT` all entities in the database.

All entities are considered as new rows and are `INSERTED` in the database.

{% include template-example.html %} 
{% highlight csharp %}
// Easy to use
context.BulkInsert(list);

// Easy to customize
context.BulkInsert(list, options => options.BatchSize = 100);
{% endhighlight %}

## Purpose
`Inserting` thousand of entities for an initial load or a file importation is a typical scenario.

<!--`SubmitChanges` method makes it quite impossible to handle this kind of situation directly from Entity Framework due to the number of database round-trips required. 

!-->`SubmitChanges` requires one database round-trip for every entity to `insert`. So if you need to `insert` 10000 entities, then 10000 database round-trips will be performed which is **INSANELY** slow.!

`BulkInsert` in counterpart requires the minimum database round-trips as possible. By example under the hood for SQL Server, a simple`SqlBulkCopy` could be performed.

## Performance Comparisons

| Operations      | 1,000 Entities | 2,000 Entities | 5,000 Entities |
| :-------------- | -------------: | -------------: | -------------: |
| SubmitChanges   | 1,000 ms       | 2,000 ms       | 5,000 ms       |
| BulkInsert      | 6 ms           | 10 ms          | 15 ms          |

{% include section-faq-begin.html %}
## FAQ

### How can I specify more than one option?
You can specify more than one option using anonymous block.

{% include template-example.html %} 
{% highlight csharp %}
context.BulkInsert(list, options => {
	options.BatchSize = 100);
	options.ColumnInputExpression = c => new {c.Name, c.Description});
});
{% endhighlight %}

### How can I specify the Batch Size?
You can specify a custom batch size using the `BatchSize` option.

Read more: [BatchSize](/batch-size)

{% include template-example.html %} 
{% highlight csharp %}
context.BulkInsert(list, options => options.BatchSize = 100);
{% endhighlight %}

### How can I specify custom columns to Insert?
You can specify custom columns using the `ColumnInputExpression` option.

Read more: [ColumnInputExpression](/column-input-expression)

{% include template-example.html %} 
{% highlight csharp %}
context.BulkInsert(list, options => options.ColumnInputExpression = c => new {c.Name, c.Description});
{% endhighlight %}

<!--### How can I include child entities (Entity Graph)?
You can include child entities using the `IncludeGraph` option. Make sure to read about the `IncludeGraph` since this option is not as trivial as others.

Read more: [IncludeGraph](/include-graph) 

{% include template-example.html %} 
{% highlight csharp %}
context.BulkInsert(list, options => options.IncludeGraph = true);
{% endhighlight %} !-->

### Why BulkInsert doesn't use the ChangeTracker?
To provide the best performance possible!

Since using the `ChangeTracker` can greatly reduce performance, we chose to let `SubmitChanges` method handle the scenarios with `ChangeTracker` and `BulkInsert` the scenarios without it.

### Why BulkInsert is faster than SubmitChanges?
The major difference between both methods is `SubmitChanges` uses the `ChangeTracker` but not the `BulkInsert` method.

By skipping the `ChangeTracker`, some methods like `Add`, `AddRange`, `DetectChanges` are no longer required which greatly helps to improve the performance.
{% include section-faq-end.html %}

## Related Articles

- [How to Benchmark?](benchmark)
- [How to use Custom Column?](custom-column)
