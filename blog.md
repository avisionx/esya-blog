---
layout: default
title: Blog
permalink: /blog
---

<style type="text/css">
  body {
    background: url('{{ '/assets/coolBg.svg' | relative_url }}');
  }
</style>

<div class="loader">
	<img src="{{ '/assets/loader-white.svg' | relative_url }}" width="100px" height="100px" style="top: 50%; left: 50%; position: relative; transform: translateX(-50%) translateY(-50%);">
</div>

<div class="container" style="min-height: 100vh">	
	<div class="row" style="min-height: 100vh">
		<div class="col d-flex align-items-center">
			<div class="col">
				<div class="row text-center mt-4">
					<div class="col">
						<h1 class="text-center text-light font-weight-bold display-4">Blogs</h1>
					</div>
				</div>
				<div class="row">
					{% for post in site.posts reversed %}
					<div class="col-12 col-md-4 my-4 my-md-5">
						<a class="card rounded shadow-sm text-dark p-3" href="#{{ forloop.index }}" onclick="updateUrl(this.href)" data-toggle="modal" data-target="#{{ forloop.index }}" style="text-decoration: none;">
							<div class="card-body p-0 rounded">
								<img src="{{ '/assets/' | relative_url }}{{ post.img_url }}" class="card-img-top">
								<h5 class="card-title font-weight-bold text-dark pt-3 mb-1">{{ post.title }}</h5>
								{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        						<p class="card-title text-secondary small mb-1 font-weight-light" style="font-size: 10px"><i class="fas fa-calendar-day"></i> {{ post.date | date: date_format }}</p>
								<p class="font-weight-light mb-3">{{ post.excerpt | remove: '<p>' | remove: '</p>' | truncatewords: 25}}</p>
								<p class="font-weight-light text-info small mb-0 text-center">Continue Reading</p>
							</div>
						</a>
					</div>
					<div class="modal fade" id="{{ forloop.index }}" tabindex="-1" role="dialog" aria-hidden="true">
						<div class="modal-dialog modal-lg" role="document">
							<div class="modal-content">
					      		<div class="modal-body">
					        		<button type="button" class="close rounded-circle text-dark shadow-sm" style="position: fixed; top: -15px; right: -15px; z-index: 999; width: 30px; height: 30px; background: white; opacity: 1" data-dismiss="modal" aria-label="Close">
				          				<span aria-hidden="true">&times;</span>
				        			</button>
				        			<div class="row">
				        				<div class="col-12 col-md-6 order-2 order-md-1">
					        				<h4 class="font-weight-bold mt-4 mb-1">{{post.title}}</h4>	
        									<p class="small text-secondary font-weight-light mb-0">Author: {{ post.author }}</p>
        									<p class="small text-secondary font-weight-light mb-3">Date: {{ post.date | date: date_format }}</p>
        									<p class="font-weight-light mb-auto">{{ post.excerpt | remove: '<p>' | remove: '</p>' }}</p>
        									<hr class="mt-4 w-50 d-none d-md-block bg-secondary" style="transform: translateX(50%); opacity: 0.2">
				        				</div>
				        				<div class="col-12 col-md-6 order-1 order-md-2">
				        					<img src="{{ '/assets/' | relative_url }}{{ post.img_url }}">
				        				</div>
				        			</div>
				        			<div class="row">
				        				<div class="col">
				        					<p>{{ post.content | split:'<!--more-->' | last }}
				        				</div>
				        			</div>
					      		</div>
					    	</div>
					  	</div>
					</div>
					{% endfor %}
				</div>
			</div>
		</div>
	</div>

</div>

<script type="text/javascript">

	$(document).ready(function() {
		
		const element =  document.querySelector('.loader');
    	element.classList.add('animated', 'slideOutLeft');
    	element.addEventListener('animationend', function() { 
    		var url = document.location.href;
	    	$("#" + url.split("#")[1]).modal();
    	});
    	
	});

	function updateUrl(url) {

    	var webUrl = document.location.href;
		document.location.href = webUrl.split("#")[0] + "#" + url.split("#")[1];
	}

</script>