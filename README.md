# AMQ Online Hackfest

This repository contains resources used in the AMQ Online Hackfest. 

## Scenarios

The Hackfest is prepared with 2 scenarios that highlight important use cases for AMQ Online:

* [Scenario 1 - Hackfest Services](scenario1.md)
* [Scenario 2 - FestHack Technologies](scenario2.md)

## Installing AMQ Online

The `templates` folder contains all the YAML files you need to install AMQ Online. Look at the AMQ Online documentation for instructions on how to install AMQ Online:

* [Installing and Managing AMQ Online on OpenShift Container Platform](https://doc-stage.usersys.redhat.com/documentation/en-us/red_hat_amq/7.2/html-single/installing_and_managing_amq_online_on_openshift_container_platform/)
* [Using AMQ Online on OpenShift Container Platform](https://doc-stage.usersys.redhat.com/documentation/en-us/red_hat_amq/7.2/html-single/using_amq_online_on_openshift_container_platform/)

### Installing plans

We provide example configs and plans for AMQ Online to be used as a starting point for the
scenarios. These can be found in the `plans` folder. Once AMQ Online is
installed, they can be applied by running:

```
oc apply -f plans
```

Run the following commands to verify that they are installed:

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

# Uninstalling 

```
oc delete rolebindings -l app=enmasse -n kube-system
oc delete clusterrolebindings -l app=enmasse
oc delete crd -l app=enmasse
oc delete clusterroles -l app=enmasse
oc delete apiservices -l app=enmasse
oc delete oauthclients -l app=enmasse
oc delete project amq-online-infra
```
