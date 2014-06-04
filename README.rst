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

    $ docker build -t=docker-mongodb .

Using this image
----------------
After building/retrieving the Docker container:

.. code-block:: bash
    # Run the docker container
    docker run -p 27017:27017 -name mongodb -d docker-mongodb /sbin/my_init --enable-insecure-key # Give container a name in case it's linked to another app container


* `docker run` - starts a new docker container
* * `-p 3306:3306` - Optionnal: binds the local port 3306 to the container's port 3306, so a local.
* * `-d mysql` - Use the image tagged "mongodb" if you need to link it to another container for instance.
* * `/sbin/my_init` - Run the init scripts used to kick off long-running processes and other bootstrapping, as per [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker)
* * `--enable-insecure-key` - Enable a generated SSL key so you can SSH into the container, again as per [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker). Generate your own SSH key for production use.
* * If you use this with [fideloper/docker-nginx-php](https://github.com/fideloper/docker-nginx-php), then naming this container via `-name mongodb` will allow you to [link it](http://docs.docker.io/en/latest/use/working_with_links_names/) with the web-app.
