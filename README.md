# AMQ Online Hackfest

This repository contains resources used in the AMQ Online Hackfest. 

## Scenarios

The Hackfest is prepared with 2 scenarios that highlight important use cases for AMQ Online:

* [Scenario 1 - Hackfest Services](scenario1.md)
* [Scenario 2 - FestHack Technologies](scenario2.md)

## Cluster setup

The `templates` folder contains all the YAML files you need to install AMQ Online. Documentation for
installing is provided at [linktodocs].

### Example plans

Example infrastructure configs and plans can be found in the `plans` folder. Once AMQ Online is
installed, they can be applied by running `oc apply -f plans`. Run the following commands to verify
that they are installed:

```
oc get standardinfraconfigs
oc get brokeredinfraconfigs
oc get addressspaceplans
oc get addressplans
```

## Example clients

Provided are examples you can use as base for your client code to access AMQ Online. Any
client supporting the standard protocols used by AMQ Online (AMQP, MQTT etc), so these clients should
only be considered an example of the different ways you can retrieve endpoint information and access
the endpoints automatically.

There are currently 2 Java-based clients:

* vertx-example-client - Vert.X based client configured using a properties file, shows how to access EnMasse externally
* jms-example-client - JMS-based configured to read AddressSpace info and use service account for authentication.

Both examples come with resources that you deploy to provision messaging.
