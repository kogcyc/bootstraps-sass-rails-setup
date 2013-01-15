How to use the bootstrap-sass gem in Rails 3
=========

####1) Add the gem to the Gemfile (and then run bundle to install it)

    gem 'bootstrap-sass'
    
####2) Create a file called custom.css.scss in the ../assets/stylesheets directory that looks like this:

    @import "bootstrap";
    @import "bootstrap-responsive";
    body {
        padding-top: 40px;
    }
    .container {
	    background-color: #fa0;
    }
    .navbar .container {
	    background-color: #055;
    }
    
Add a @import for bootstrap

If you want to use the responsive feature, add an @import for it too

And then make any changes to your CSS or bootstrap SASS source below the @import(s)

####3) Add this line to bottom of ../assets/javascript/application.js:

    //= require bootstrap

####4) Go ahead and use bootstrap, here is an example ../views/layouts/application.html.erb:

    <!DOCTYPE html>
	<html>

	<head>
		<title>Title</title>
		<%= stylesheet_link_tag "application", :media => "all" %>
		<%= javascript_include_tag "application" %>
		<%= csrf_meta_tags %>
	</head>

	<body>

	<div class="navbar navbar-inverse navbar-fixed-top">
			<div class="navbar-inner">
				<div class="container">
					<button type="button" class="btn btn-navbar" data-toggle="collapse" data-target=".nav-collapse">
						<span class="icon-bar"></span>
						<span class="icon-bar"></span>
						<span class="icon-bar"></span>
					</button>
					<a class="brand" href="./index.html">Brand</a>
					<div class="nav-collapse collapse">
						<ul class="nav">
							<li class=""><a href="/">Home</a></li>
							<li class=""><a href="/">Something</a></li>
							<li class=""><a href="/">Another</a></li>
							<li class=""><a href="/">Contact</a></li>
						</ul>
						<form class="navbar-search pull-right">
							<input type="text" class="search-query" placeholder="Search">
						</form>
					</div>
				</div>
			</div>
		</div>

		<div class="container">
			<%= yield %>
		</div>

	</body>
	</html>
