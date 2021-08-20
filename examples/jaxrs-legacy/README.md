# JAX-RS unpackaged EAP example

Build a server containing a JAX-RS resource, to be run on openshift.

Openshift OC command
==============

Make sure you are logged in to your OpenShift Cluster

* mvn clean package && mkdir -p target/openshift && mv target/server target/openshift
* oc import-image wildfly-s2i-jdk11 --from=quay.io/jfdenise/wildfly-s2i-jdk11:latest --confirm
* oc new-build --strategy source --binary --image-stream wildfly-s2i-jdk11 --name jaxrs-server-mode-legacy-app
* oc start-build jaxrs-server-mode-legacy-app --from-dir target/openshift
* Once the build is over...
* oc new-app jaxrs-server-mode-legacy-app
* oc expose svc/jaxrs-server-mode-legacy-app

access the endpoint at : openshift route/hello

JKube
====

WARNING, depends on SNAPSHOT Build of JKube based on branch
https://github.com/jfdenise/jkube/tree/wildfly-s2i-v2-new-generator

Make sure you are logged in to your OpenShift Cluster

The following command will create and deploy the Server on OpenShift:

`mvn clean oc:deploy`

