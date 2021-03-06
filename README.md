About
-----

Examples for the project: https://github.com/shiwaforce/poco

Poco lets you catalogue and manage your Docker projects using
simple YAML files to shorten the route from finding your project to
initialising it in your local environment.

This helps you set up your local development environment and to run
demos.

Requirements
------------

-   Docker, version \> 17
-   Python, version \> 2.7

Quick start
------------

Note: do not clone this repository for the quick start. Poco will do it for you in step 2.

1. Install the latest poco:
	```shell
	$ pip install poco
	```

2. Add the [catalog](./poco-catalog.yml) to poco:
	```shell
	$ poco repo add catalog-example git@github.com:shiwaforce/poco-example.git
	```

3. List all projects in the catalogue and list all available plans of the example voting app:
	```shell
	$ poco catalog
	-------------------
	Available projects:
	-------------------
	nginx
	example-voting-app
	mysql

	$ poco plan ls example-voting-app
	---------------------------------------------------------------
	Available plans for project: example-voting-app
	---------------------------------------------------------------
	default
	javaworker
	simple
	```

4. Start and stop the Docker example voting app with the **default** plan:
	```shell
	$ poco start example-voting-app
	```
	This will download and build all the required Docker images and start them. The last step of the process will issue a "docker ps" command listing all the running containers.

	Visit http://localhost:5000 to see the application's main page.

	Since no plan was defined the application started with the default plan. This means the example-voting-app_worker_1 container runs .Net in the worker node.

	```shell
	$ poco down example-voting-app
	```
	This stops the containers.

5. Start and stop the Docker example voting app with the **javaworker** plan:
	```shell
	$ poco start example-voting-app/javaworker
	```
	Visit http://localhost:5000 to see the application's main page.

	The application was started in javaworker plan, so the example-voting-app_worker_1 container contains OpenJDK 1.8 to run the worker node.

	```shell
	$ poco down example-voting-app/javaworker
	```
	This stops the containers.

Other examples
----------------
- [example-voting-app](https://github.com/shiwaforce/poco-example/blob/master/example-voting-app/README.md)
- [nginx](https://github.com/shiwaforce/poco-example/blob/master/nginx/README.md)
- [mysql](https://github.com/shiwaforce/poco-example/blob/master/mysql/README.md)

License
-------

MIT

Contributors
------------

[ShiwaForce.com Inc.](https://www.shiwaforce.com/en/)
