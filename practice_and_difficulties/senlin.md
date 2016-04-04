# Senlin
Senlin is a clustering service for OpenStack clouds. It creates and operates clusters of homogeneous objects exposed by other OpenStack services. The goal is to make the orchestration of collections of similar objects easier.

Senlin provides RESTful APIs to users so that they can associate various policies to a cluster. Sample policies include placement policy, load balancing policy, health policy, scaling policy, update policy and so on.

Senlin is designed to be capable of managing different types of objects. An object's lifecycle is managed using profile type implementations, which are themselves plugins.

##Senlin部署
http://docs.openstack.org/developer/senlin/install.html


