docker-mongodb
===========

A MongoDB Dockerfile to spin up a mongodb container.

Quickstart
----------

This image is available as a trusted build on the docker index. The easiest way to get it on your server is using ``docker pull``:

.. code-block:: bash

    $ docker pull swcc/docker-mongodb

Alternatively, you can clone this repository and build the image yourself:

.. code-block:: bash

    $ docker build -t=swcc/docker-mongodb .

Using this image
----------------
After building/retrieving the Docker container:

.. code-block:: bash

    # Run the docker container
    docker run -p 27017:27017 -name mongodb -d swcc/docker-mongodb /sbin/my_init --enable-insecure-key # Give container a name in case it's linked to another app container


* `docker run` - starts a new docker container
    * `-p 27017:27017` - Optionnal: binds the local port 27017 to the container's port 27017, so a local.
    * `-d swcc/docker-mongodb` - Use the image tagged "swcc/docker-mongodb" if you need to link it to another container for instance.
    * `-name mongodb` - Give it a name to easily linked it to another container.
    * `/sbin/my_init` - Run the init scripts used to kick off long-running processes and other bootstrapping, as per [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker)
    * `--enable-insecure-key` - Enable a generated SSL key so you can SSH into the container, again as per [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker). Generate your own SSH key for production use.
* If you use this with [phusion/passenger-ruby20](https://registry.hub.docker.com/u/phusion/passenger-ruby20/) or [phusion/passenger-nodejs](https://registry.hub.docker.com/u/phusion/passenger-nodejs/), then naming this container via `-name mongodb` will allow you to [link it](http://docs.docker.io/en/latest/use/working_with_links_names/) with the web-app.
