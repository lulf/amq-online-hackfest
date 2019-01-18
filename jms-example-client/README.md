# Qpid JMS example

This example clients demonstrates how you can connect to an AMQ Online messaging service running on the same OpenShift cluster,
and send/recv messages. This client is not intended to run outside the OpenShift cluster (see vertx-example-client for that), although it can be manipulated into doing so.

`src/main/resources/k8s` contains example YAML files for configuring an AMQ Online AddressSpace,
Address and MessagingUser. Run the following command to create them:

```
oc new-project myapp
oc apply -f src/main/resources/k8s
```

## Building and running client

```
mvn clean package
```

## Build and deploy:

```
mvn -Dfabric8.mode=openshift package fabric8:build
mvn fabric8:resource fabric8:deploy
```
