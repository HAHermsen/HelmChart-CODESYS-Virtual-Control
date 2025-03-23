This is a basic Helm chart structure for deploying your Codesys Edge Gateway and Virtual Control setup in Kubernetes 
on x86/x64 ased systems. It allows for flexible configuration through the values.yaml file, and Kubernetes resource definitions are templated 
for reuse and easier management. The helm charts are easily editable for your specific needs.

This helmchart currently uses
> runtimevictor/codesyscontrol_virtuallinux:v1.0.0        (runs codesyscontrol_virtuallinux_4.14.0.0_amd64)
> gsmartcodesys/codesysedge_edgeamd64                     (runs codesysedge_edgeamd64_4.10.0.0)



  helm-chart/
  
  ├── Chart.yaml            # Metadata about the Helm chart
  
  ├── values.yaml           # Default configuration values for the chart
  
  ├── templates/            # Contains Kubernetes YAML templates
  
  │   ├── deployment.yaml   # Deployment configuration for CODESYS Virtual Control
  
  │   ├── service.yaml      # Service configuration to expose CODESYS Virtual Control
  
  │   └── ingress.yaml      # (Optional) Ingress configuration for web access
  
  └── README.md             # Documentation and instructions for using the Helm chart



Grab a copy of the helm chart
> git clone https://github.com/HAHermsen/HelmChart-CODESYS-Virtual-Control.git

Go into the directory
> cd HelmChart-CODESYS-Virtual-Control/helm-chart

Now execute the helm script
> helm install codesys-helm ./codesys-virtualcontrol-helm-chart -f values.yaml --namespace codesys

You can override values in values.yaml by using the --set flag during the install.
I personally run and expose the pod into my LAN, you can adjust the settings to your specific needs IP/Domain:
> helm install codesys-helm ./helm-chart --set service.loadBalancerIP=192.168.1.100
