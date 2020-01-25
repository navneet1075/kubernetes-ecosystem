	• Control Plane
		• Pilot
		• Mixer
		• Citadel
		• Galley
	• Data Plane:
		• Envoy proxy -> A high performance , highly configurable proxy written in C++ at Lyft.

Functions of multiple components:
	• Pilot : Configures the envoy proxy for  traffic routing .
	• Galley: Supplies the configuration for all istio control plane components/mesh.
	• Mixer: 
		• Telemetry from envoy proxies
		• Policy checks on the envoy proxies
	• Citadel: Identity management for envoy proxies. Provides all the certificates to the sidecars.


**Istio Resources**
	
	• VirtualService
	
	• DestinationRule
	
	• Gateway
	
	• ServiceEntry
	
	
	• VirtualService: -> Defines how traffic is routed to all the service in the service mesh.
	• DestinationRule: -> Defines what happens /how traffic is handled when it reaches the destination.
	• Gateway: Defines how traffic enters into/outside the service mesh at the edge. 
	• ServiceEntry: -> Allows to add a external service into istio service registry . Once added the service behaves like any other service in istio service registry . We can apply all the istio rules for configuring and controlling the service.
	
	

What istio handles for us in Traffic Management . 

	• Routing  : -> Routing based on matching rules , weights etc.
	• Circuit Breaking :-> Allows to specify conditions after which the circuit will be open/closed .
	• Load Balancing according to different policies. -> By default the envoy proxies does the random load balancing to the instances backed by k8s service. Pilot allows to configure the policy on a per service basis to change the load balancing policy.
	• Fault Injection -> This is mainly used in testing to mimic scenarios of fault which we encounter in real production envs and identify the behavior of the system. For example : 
	• Retries: automatic retries to a service . This is useful in case if in some case the app is overwhelmed by too many requests and needs some time between to respond. The duration between 2 tries is calculated by envoy proxy. Timeout per retry can also be specified.
	• Timeouts : Timeout for a particular response to come from a particular service. Can be configured per service . The value is configurable and it should be adjusted according to the behavior of the application.
	• AB Testing:  Split traffic by percentage to different versions of the app .
