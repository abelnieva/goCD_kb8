# goCD_kb8

deploying GoCD on kubernetes cluster (google cloud)

## SOFTWARE REQUIREMENTS

Make sure to get everything installed before to start
<pre>

* ruby
* terraform
* docker engine
* docker compose
* google cloud sdk
* kubectl

</pre>

## GOOGLE CLOUD AUTHENTICATION

Get your credentials from google cloud , then save it as credentials.json into root project directory

## DEFINING THE ENVIRONMENTS
here you can define your environments, it needs to be one file per env.

<pre>

/envs
      dev
      prod
</pre>


## CONTROLLER

converge.rb manages all operations

<pre>
./converge.rb path/to/env/file OPERATION
</pre>

### OPERATIONS
<pre>
* INIT
* CREATE
* DESTROY
* APPS
  * LIST
  * INSTALL
</pre>
## INITIALIZING TERRAFORM
This is the very first required operation, it needs to be done  once  
<pre>

  ./converge.rb path/to/env/file init

</pre>
## INSTALLING KUBERNETES CLUSTER

<pre>

./converge.rb path/to/env/file create

</pre>
make sure get all envs settings in /envs/*

## LISTING APPS AVAILABLE TO INSTALL
<pre>

./converge.rb ./envs/dev/dev1.tfvars apps list

</pre>
## BUILD & INSTALLING  GO CD
<pre>

./converge.rb ./envs/dev/dev1.tfvars apps install gocd

</pre>

## INSTALLING  GO CD
<pre>

./converge.rb ./envs/dev/dev1.tfvars apps deploy gocd

</pre>

## DESTROYING ENVIRONMENTS
<pre>

converge.rb ./envs/dev/dev1.tfvars destroy

</pre>

## TEST ENVIRONMENT

Chef recipe, kitchen and google cloud help to test the software .
Check out README for test (directory called gocd_test)
