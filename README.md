# kubernetes-cluster-for-geomapping
A Kubernetes cluster diagram for geomapping service, as part of Helsinki Devops with Docker MOOC

<img width="1961" height="1333" alt="KubernetesCluster drawio" src="https://github.com/user-attachments/assets/01b71053-20f7-4d2a-81d6-2fe5c31e172e" />


## Component Breakdown -
localhost: Your own computer acting as the administrator. It uses kubectl to send deployment manifests to the cluster.
Cluster: The logical boundary containing all four worker nodes and the control plane components.
Pod: The smallest deployable unit. The diagram shows multiple Pods for both the GeoServer and the Mapping App distributed across different nodes for high availability.
Container: Located inside the Pods, these run the specific GeoServer and Mapping App software.
Service:
MappingApp-LB: Receives the incoming HTTP message from the internet and distributes it to the application Pods.
GeoServer-LB: An internal service that allows the Mapping App to reliably find and request map data from the GeoServer instances.
Volume: A Persistent Volume attached to Node 1, used by GeoServer to store and access geospatial data files.
External API: The "Geolocation Traffic Routing service" exists outside the cluster, demonstrating how Kubernetes apps interact with third-party web services.
