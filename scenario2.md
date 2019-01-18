# AMQ Online Hackfest
## Scenario 2

FestHack Technologies are a company that build applications which use messaging.  They have many teams of application developers who need to be quickly develop and test their applications which include a messaging component.  FestHack deploy all their applications to OpenShift both on-premise and in the cloud.

FestHack developers are currently constrained by how long it takes to configure and deploy messaging, and are looking to automate this.  Further they wish to be able to declaratively specify the messaging requirements of their applications, and have these met _automagically_ when their applications are deployed.  FestHack uses OpenShift for all development and production deployments of their applications.

FestHack currently maintain 15 distinct applications that make use of messaging.  There are around 70 engineering and 20 QE resources who work on these applications.  

FestHack applications are written to use the JMS APIs, and make extensive use of (local) transactions.  They have a mixture of AMQP and OpenWire clients.

For engineering work it is sufficient to restrict the messaging infrastructure to support storage of no more than 1000 messages of ~1KB size, processing no more than 10 msg/s, with up to 10 queues and topics.  There is no need for messages in an engineering environment to survive cluster or even node failure.  For general QE work, support for storage of 5000 messages (of up to 10KB) and processing at the rate of 5000 msg/s is required.  For production installations, storage of up to 100,000 messages (each of up to 15KB) and processing at the rate of 20,000msg/s is required.  For production installations, the message data must survive individual node failure.


It must be impossible for one installation of an application to “cross-talk” to another.  Connections from outside the cluster must also be prevented.

In order to simplify the deployment of applications FestHack want to avoid hardcoding credentials into their application deployments - they wish their JMS based applications to be able to “automagically” find the credentials and messaging endpoints from their environment when they are deployed.

In using OpenShift in the past FestHack have experienced issues where too many applications have been deployed to the cluster and key containers have been evicted.  To mitigate the effects of this, they desire to ensure that messaging infrastructure and application containers are deployed to distinct nodes within the cluster, and ideally that engineering deployments are evicted in preference to qe deployments and only as a last resort should production deployments be evicted.

It is required that sufficient monitoring and alerting is set up such that the FestHack Technologies team can detect issues with the messaging infrastructure and take action

## Task:

Create the necessary AMQ Online addressspace plan(s), address plan(s), infrastructure configs, and scripts to meet the given requirements.  Create a PoC installation.  Verify that the performance/volume requirements can be met.  Provide guidance on sizing of clusters / how many clusters might be required to meet their requirements.

