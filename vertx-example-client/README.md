# VertX example

This example clients demonstrates how you can connect to an AMQ Online messaging service (or any
AMQP 1.0 based service in general) and send/recv messages. This client is not intended to run on
a OpenShift cluster (see jms-example-client for that), although it can by editing the configuration
manually.

`src/main/resources/k8s` contains example YAML files for configuring an AMQ Online AddressSpace,
Address and MessagingUser. Run the following command to create them:

```
oc new-project myapp
oc apply -f src/main/resources/k8s
```

Edit `src/main/resources/config.properties` with the connection info of your address space. To
retrieve the address space endpoint host, run:

```
oc get addressspace vertx-example -o jsonpath={.status.endpointStatuses[?(@.name==\'messaging\')].externalHost}
```

## Building and running client

```
mvn package
mvn exec:java
```
