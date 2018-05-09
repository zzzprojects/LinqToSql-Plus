---
permalink: installing
---

**LinqToSql Plus** can be installed through NuGet.

This library is **NOT FREE**

The latest version always contains a trial that expires at the end of the month. You can extend your trial for several months by downloading the latest version at the begining of every month.

## Step 1 - NuGet Download

Go to the download page and choose the right Entity Framework version for your project.

<a class="btn btn-lg btn-z" role="button" href="/download" onclick="ga('send', 'event', { eventAction: 'download'});">
	<i class="fa fa-cloud-download" aria-hidden="true"></i>
	Download
	<i class="fa fa-angle-right"></i>
</a>

## Step 2 - Done

**LinqToSql Plus** doesn't require any configuration by default.

All bulk operations extension methods are automatically added to your DbContext:
- BulkInsert
- BulkUpdate
- BulkDelete
- BulkMerge
- BulkSynchronize

{% include template-example.html title='Bulk Operations Examples'%} 
{% highlight csharp %}
// Bulk Operations
context.BulkInsert(list);
context.BulkUpdate(list);
context.BulkDelete(list);
context.BulkMerge(list);
context.BulkSynchronize(list);
{% endhighlight %}

All batch operations extension methods are automatically added to your Queryable:
- DeleteFromQuery (Coming Soon)
- UpdateFromQuery (Coming Soon)

{% include template-example.html title='Batch Operations Examples'%} 
{% highlight csharp %}
// Batch Operations (Coming Soon)
context.Customers.Where(x => !x.IsActif).DeleteFromQuery();
context.Customers.Where(x => !x.IsActif).UpdateFromQuery(x => new Customer {Actif = true});
{% endhighlight %}
