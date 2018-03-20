---
layout: default
permalink: index
---

<!-- hero !-->
{% include component-rotator-dark-begin.html %}
<div class="hero">
	<div class="container">
		<div class="row">
		
			<div class="col-lg-5 hero-header">
			
				<h1>
					<div class="display-4">LINQ To SQL</div>
					<div class="display-1">PLUS</div>
				</h1>
				
				<div class="wow zoomIn">
					<a class="btn btn-xl btn-z" href="{{ site.github.url }}/download"
							onclick="ga('send', 'event', { eventAction: 'download'});">
						<i class="fa fa-cloud-download" aria-hidden="true"></i>
						NuGet Download
						<i class="fa fa-angle-right"></i>
					</a>
				</div>
				
				<div class="font-italic">
					*Free monthly trial available
				</div>
				
				<div class="download-count">
					<div class="item-text">Download Count:</div>
					<div class="item-image wow lightSpeedIn">
						<img src="https://zzzprojects.github.io/images/nuget/linq-to-sql-plus-big-d.svg" />
					</div>
				</div>

			</div>
			
			<div class="col-lg-7 hero-examples">
			
				<div class="row hero-examples-1">
				
					<div class="col-lg-3 wow slideInUp"> 
						<h3 class="wow rollIn">Save<br />10x to 50x<br />Faster</h3>
						<div class="hero-arrow hero-arrow-ltr">
							<img src="images/arrow.png">
						</div>
					</div>

					<div class="col-lg-9 wow slideInRight">
						<div class="card card-code card-code-light">
							<div class="card-header"><h5>Zero configuration required</h5></div>
							<div class="card-body">
{% highlight csharp %}
// Bulk Operations
context.BulkInsert(list);
context.BulkUpdate(list);
context.BulkDelete(list);
context.BulkMerge(list);

// Batch Operations (Coming Soon)
context.Customers.Where(x => !x.IsActif)
       .DeleteFromQuery();
context.Customers.Where(x => !x.IsActif)
       .UpdateFromQuery(x => 
            new Customer {IsActif = true});
{% endhighlight %}
							</div>
						</div>
					</div>
					
				</div>
				
				<div class="row hero-examples-2">
				
					<div class="col-lg-3 order-lg-2 wow slideInDown">
						<h3 class="wow rollIn">Overcome<br />LinqToSql<br />Limitations</h3>
						<div class="hero-arrow hero-arrow-rtl">
							<img src="images/arrow.png">
						</div>
					</div>
					
					<div class="col-lg-9 order-lg-1 wow slideInLeft">
						<div class="card card-code card-code-light">
							<div class="card-header"><h5>Over 100 customizations available</h5></div>
							<div class="card-body">
{% highlight csharp %}
// Use custom key
context.BulkMerge(customers, options => {
   options.ColumnPrimaryKeyExpression = 
        customer => customer.Code;
});
{% endhighlight %}
							</div>
						</div>
					</div>						
				</div>
				
			</div>
			
		</div>
	</div>	
</div>
{% include component-rotator-dark-end.html %}

<!-- featured !-->
<div class="featured">
	<div class="container">

		<h2 class="wow slideInUp">Improve SubmitChanges <span class="text-z">Performance</span></h2>
		<div class="row">
			<div class="col-lg-5 left wow slideInLeft">
				<p>
					Perform save operations <span class="text-z">10 to 50 times</span> faster.
				</p>
				<p>
					Provider supported:
				</p>				
				<ul class="list-checked">
					<li>SQL Server 2008+</li>
					<li>SQL Azure</li>				
				</ul>	
			</div>
			<div class="col-lg-7 right wow slideInRight">
				<table>
					<thead>
						<tr>
							<th>Operations</th>
							<th>1,000 Entities</th>
							<th>2,000 Entities</th>
							<th>5,000 Entities</th>
						</tr>
					</thead>
					<tbody>
						<tr>
							<th>SubmitChanges</th>
							<td>1,000 ms</td>
							<td>2,000 ms</td>
							<td>5,000 ms</td>
						</tr>
						<tr>
							<th>BulkInsert</th>
							<td>6 ms</td>
							<td>10 ms</td>
							<td>15 ms</td>
						</tr>
						<tr>
							<th>BulkUpdate</th>
							<td>50 ms</td>
							<td>55 ms</td>
							<td>65 ms</td>
						</tr>
						<tr>
							<th>BulkDelete</th>
							<td>45 ms</td>
							<td>50 ms</td>
							<td>60 ms</td>
						</tr>
						<tr>
							<th>BulkMerge</th>
							<td>65 ms</td>
							<td>80 ms</td>
							<td>110 ms</td>
						</tr>
					</tbody>
				</table>

				<p class="text-muted">* Benchmark for SQL Server</p>

			</div>
		</div>
	</div>
</div>

<div class="testimonials">
{% include component-rotator-dark-begin.html %}
	<div class="container">
		<h2>Trusted by thousands around the world!</h2>
		
		<div class="row">
			<div>
				<h3 class="text-center">More than <span class="text-z">2000</span> satisfied customers spreaded across over <span class="text-z">75</span> countries </h3>
				
				<hr />
				
				<blockquote class="blockquote text-center" style="visibility: visible; animation-name: slideInLeft;">
					<p class="mb-0 wow slideInLeft">That's really cool! I didn't actually expect you to build a new release in just a day, to be honest, but this is really awesome</p>
					<footer class="blockquote-footer wow slideInRight" style="visibility: visible; animation-name: slideInRight;">
						Kimwan Ogot, USA, Minneapolis
						<div><a href="https://magenic.com/" target="_blank">Magenic</a></div>
					</footer>
				</blockquote>
				
				<blockquote class="blockquote text-center" style="visibility: visible; animation-name: slideInLeft;">
					<p class="mb-0 wow slideInLeft">I would absolutely recommend your product. It is  simple, cheap, effective.</p>
					<footer class="blockquote-footer wow slideInRight" style="visibility: visible; animation-name: slideInRight;">
						Marc Zabal, USA, Arkansas
						<div><a href="http://instanext.com/" target="_blank">InstaNext Inc.</a></div>
					</footer>
				</blockquote>

				<div class="more">
					<a href="http://www.zzzprojects.com/testimonials/" target="_blank" class="btn btn-lg btn-z" role="button"
							onclick="ga('send', 'event', { eventAction: 'testimonials'});">
						<i class="fa fa-comments"></i>&nbsp;
						Read More Testimonials
					</a>
				</div>
			</div>
		</div>
	</div>
{% include component-rotator-dark-end.html %}
</div>

<!-- features !-->
<div class="features">

	<div class="container">

		<!--Bulk SubmitChanges  !-->
		<h2 class="wow slideInUp"><span class="text-z">Bulk</span> SubmitChanges (Coming Soon)</h2> 
		<div class="row">
			<div class="col-lg-5 wow slideInLeft">
				<p class="feature-tagline">Make your applications 10x to 50x times more <span class="text-z">scalable</span> without any configuration and effort.</p>
				<ul class="list-checked">
					<li>Easy to use</li>
					<li>Easy to customize</li>
					<li>Easy to maintain</li>
				</ul>
				<!--<div class="more-info">
					<a href="{{ site.github.url }}/tutorial-bulk-SubmitChanges" class="btn btn-lg btn-z" role="button">
						<i class="fa fa-book"></i>&nbsp;
						Read More
					</a> 
				</div>	!-->
			</div>
			<div class="col-lg-7 wow slideInRight">
				<div class="card card-code card-code-dark">
					<div class="card-header"><h5>Bulk SubmitChanges Examples</h5></div>
					<div class="card-body">
{% highlight csharp %}
// Easy to use (Coming Soon) 
context.BulkSubmitChanges(); 

// Easy to customize (Coming Soon) 
context.BulkSubmitChanges(options => options.BatchSize = 1000);
{% endhighlight %}
					</div>
				</div>
			</div>
		</div>

		<hr class="m-y-md" />
		
		<!-- Bulk Operations  !-->
		<h2 class="wow slideInUp"><span class="text-z">Bulk</span> Operations</h2>
		<div class="row">
			<div class="col-lg-5 wow slideInLeft">
				<p class="feature-tagline">Add <span class="text-z">flexibility</span> to your toolbox to cover your scenarios with the best performance.</p>
				<ul class="list-checked">
					<li>Bulk Insert</li>
					<li>Bulk Update</li>
					<li>Bulk Delete</li>
					<li>Bulk Merge</li>
					<li>Bulk Synchronize</li>
				</ul>
				<div class="more-info">
					<a href="{{ site.github.url }}/tutorial-bulk-operations" class="btn btn-lg btn-z" role="button">
						<i class="fa fa-book"></i>&nbsp;
						Read More
					</a>
				</div>	
			</div>
			<div class="col-lg-7 wow slideInRight">
				<div class="card card-code card-code-dark">
					<div class="card-header"><h5>Bulk Operations Examples</h5></div>
					<div class="card-body">
{% highlight csharp %}
// Include childs entities
context.BulkMerge(customers, 
	options => options.IncludeGraph = true);
});

// Use custom key
context.BulkMerge(customers, options => {
   options.ColumnPrimaryKeyExpression = 
        customer => customer.Code;
});
{% endhighlight %}	
					</div>
				</div>
			</div>
		</div>
		
		<hr class="m-y-md" />
		
		<!-- Batch Operations !-->
		<h2 class="wow slideInUp"><span class="text-z">Batch</span> Operations (Coming Soon)</h2> 
		<div class="row">
			<div class="col-lg-5 wow slideInLeft">
				<p class="feature-tagline">Perform your operations from LINQ Query without loading entities in the context.</p>
				<ul class="list-checked">
					<li>DeleteFromQuery</li>
					<li>UpdateFromQuery</li>
				</ul>
				<div class="more-info">
					<a href="{{ site.github.url }}/tutorial-batch-operations" class="btn btn-lg btn-z" role="button">
						<i class="fa fa-book"></i>&nbsp;
						Read More
					</a>
				</div>	
			</div>
			<div class="col-lg-7 wow slideInRight">
				<div class="card card-code card-code-dark">
					<div class="card-header"><h5>Batch Operations Examples</h5></div>
					<div class="card-body">
{% highlight csharp %}
// DELETE all inactive customers  (Coming Soon)
context.Customers.Where(x => !x.IsActif)
       .DeleteFromQuery();
	   
// UPDATE all inactive customers (Coming Soon)
context.Customers.Where(x => !x.IsActif)
       .UpdateFromQuery(x => new Customer {IsActif = true});
{% endhighlight %}	
					</div>
				</div>
			</div>
		</div>
		
		<!-- more-feature  
		<div class="more">
			<a href="{{ site.github.url }}/tutorials" class="btn btn-z btn-xl" role="button">
				<i class="fa fa-book"></i>&nbsp;Read Tutorials
			</a>
		</div>
		!-->
	</div>
</div>

<div class="testimonials about-us">
{% include component-rotator-dark-begin.html %}
	<div class="container">
		<h2>About ZZZ Projects</h2>
		<hr />
<!--
We are different
	- Free and open source
	- Prime ->  redonner
	- Customer service

<!--
		<p class="text-center">
			ZZZ Projects is a new kind of company
		</p>!-->
		<p class="text-center">
			Our mission is to <span class="text-z">add value</span> to the <span class="text-z2">.NET Community</span> by supporting some of the most popular free & open source libraries.
		</p>
		<p class="text-center">
			Hundreds of thousands of people visit us every month, and we count over <span class="text-z">10 million</span> downloads.
		</p>
		<hr />
		<div class="row">
			<div class="col-lg-2"></div>
			<div class="col-lg-4">
				<h3>Summary</h3>
				<ul>
					<li>Founded: 2014</li>
					<li>Founder: Jonathan Magnan</li>
					<li>Customers: 2000+</li>
					<li>Countries: 75+</li>
					<li>Closed Request: 3000+</li>
					<li>Projects: 20+</li>
				</ul>
				
			</div>
			<div class="col-lg-5">
				<h3>Free Projects</h3>
				<ul class="list-underline list-light">
					<li><a href="http://entityframework-plus.net/">Entity Framework Plus</a></li>
					<li><a href="http://entityframework-dynamicfilters.net/">Entity Framework Dynamic Filters</a></li>
					<li><a href="http://entityframework-effort.net/">Entity Framework Effort</a></li>	
					<li><a href="https://github.com/zzzprojects/EntityFramework.Extended">Entity Framework Extended</a></li>
					<li><a href="http://entityframework.net/">Entity Framework FAQ</a></li>	
					<li><a href="https://github.com/zzzprojects/GraphDiff">Entity Framework GraphDiff</a></li>
					<li><a href="http://www.zzzprojects.com/">View More...</a></li>
				</ul>
			</div>			
		</div>
		<!--
		<div style="padding-left: 450px; padding-top: 60px;padding-bottom: 60px;">
			<a href="http://www.zzzprojects.com/testimonials/" target="_blank" class="btn btn-lg btn-z" role="button"
					onclick="ga('send', 'event', { eventAction: 'testimonials'});">
				<i class="fa fa-comments"></i>&nbsp;
				More Projects
			</a>
		</div>
		!-->

	</div>
{% include component-rotator-dark-end.html %}
</div>
