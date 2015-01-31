---
layout: page
title: Installation
permalink: /install/
---

For development purposes, a pre-built CentOS 7.0 virtual machine is available
which uses Puppet and a Vagrantfile to build, install and run a working
Alexandria CMDB instance.

For more information see the [alexandria-vagrant](https://github.com/cavaliercoder/alexandria-vagrant)
project on GitHub.

If you'd like to build it yourself or use another platform please see the 
following instructions.

## Linux/OS X

* Install Go as per https://golang.org/doc/install

* Ensure your `GOPATH` environment variable is set correctly

* Install MongoDB as per http://docs.mongodb.org/manual/installation/

* Install the API server

  * Install from source
  
    ```bash
    go get github.com/cavaliercoder/alexandria
    sudo mkdir /etc/alexandria
    sudo cp $GOPATH/src/github.com/cavaliercoder/alexandria/api.json /etc/alexandria/api.json
    ```

  * Edit `/etc/alexandria/api.json` and enter the correct details for:
 
    * TCP Port to listen on (default: `4123`)
    * Connection details for MongoDB (default: `localhost`)

  * Edit `$GOPATH/src/github.com/cavaliercoder/alexandria/answers.json` with
    your desired initial configuration, including username and password.

  * Bootstrap the API database:

    ```bash
    alexandria --answers $GOPATH/src/github.com/cavaliercoder/alexandria/answers.json
    ```

  * Start the server with: `alexandria`

* Install the CLI:

  * Install from source:

    ```bash
    go get github.com/cavaliercoder/alexandria-cli
    ```

  * Import API configuration environment variables and test:

    ```bash
    . ~/.alexrc
    alexandria-cli get users current
    ```

* Install the Dashboard console

  * Install from source
    ```bash
    go get github.com/cavaliercoder/alexandria-dashboard
    ```

    This will likely through an error when `go` attempts to build the sources.
    You may safely ignore this error.

  * Edit `$GOPATH/src/github.com/cavaliercoder/alexandria-dashboard/conf/app.conf`
    (for both `[dev]` and `[prod]` sections):

    * Set `api.url` to URL and TCP port for API server
    * Set `api.key` to the API Key generated from the database bootstrap step.
      This key can be found in the generated `~/.alexrc` file.
    * Set `http.port` to the desired listening TCP port

  * Start the dashboard web server with:
    
    ```bash
    revel run github.com/cavaliercoder/alexandria-dashboard
    ```

  * Test the Dashboard in your browser:

    * Navigate to `http://<hostname>:<port>`
      (typically `http://localhost:4124`)

    * Log in with the credentials provided in the API answer file (typically 
      `root@localhost` and `C0nf!g`)
