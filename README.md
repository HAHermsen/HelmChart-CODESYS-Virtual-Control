This is a basic Helm chart structure for deploying your Codesys Edge Gateway and Virtual Control setup in Kubernetes 
on x86/x64 ased systems. It allows for flexible configuration through the values.yaml file, and Kubernetes resource definitions are templated 
for reuse and easier management. The helm charts are easily editable for your specific needs.

This helmchart currently uses

> runtimevictor/codesyscontrol_virtuallinux:v1.0.0        (runs codesyscontrol_virtuallinux_4.14.0.0_amd64)
> gsmartcodesys/codesysedge_edgeamd64                     (runs codesysedge_edgeamd64_4.10.0.0)

Run helm install to install the chart on your Kubernetes cluster.

> helm install HelmChart-CODESYS-Virtual-Control ./codesys-helm-chart

You can override values in values.yaml by using the --set flag during the install.
I personally run and expose the pod into my LAN, you can adjust the settings to your specific needs IP/Domain:

> helm install codesys-helm ./codesys-helm-chart --set service.loadBalancerIP=192.168.1.100
