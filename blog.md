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
						<h1 class="text-center text-light font-weight-bold">Blogs</h1>
					</div>
				</div>
				<div class="row">
					{% for post in site.posts %}
					<div class="col-12 col-md-4 my-4 my-md-5">
						<a class="card rounded shadow-sm text-dark p-3" href="{{ post.url }}" style="text-decoration: none; height: 445px;">
							<div class="card-body p-0 rounded">
								<img src="{{ '/assets/' | relative_url }}{{ post.img_url }}" class="card-img-top">
								<h5 class="card-title font-weight-bold text-dark pt-3 mb-1">{{ post.title }}</h5>
								{%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
        						<p class="card-title text-secondary small mb-1 font-weight-light" style="font-size: 10px">{{ post.date | date: date_format }}</p>
								<p class="font-weight-light mb-1">{{ post.excerpt | remove: '<p>' | remove: '</p>' }}</p>
								<p class="font-weight-light text-info small mb-0 text-center">Continue Reading</p>
							</div>
						</a>
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

	});
</script>