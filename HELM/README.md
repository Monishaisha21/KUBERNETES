## HELM

https://artifacthub.io/
- Helm is widely known as "the package manager for Kubernetes.
- Helm is an open-source project
- The original goal of Helm was to provide users with a better way to manage all the Kubernetes YAML files we create on Kubernetes projects.
- Helm Charts. Each chart is a bundle with one or more Kubernetes manifests
- You just have to run a single command to install your entire application, instead of listing the files to install via kubectl
![image](https://github.com/rizwan141/k8s/assets/103893307/097f13e8-1fcd-4cbc-9886-bfe14f283d97)

- Charts allow you to version your manifest files too
- Helm also keeps a release history of all deployed charts, so you can go back to a previous release if something went wrong

*`chart.yaml:`* This is where you'll put the information related to your chart

*`values.yaml:`* this is the main file that contains defaults for variables. ( it contains configurable parameters and their default values for a Helm chart. It allows users to customize the deployment of the chart by providing specific values for the defined parameters. )

*`templates (dir):`* This is the place where you'll put all your manifest files. Everything in here will be passed on and created in Kubernetes.

### Installing HELM

```
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```
### Helm Commands 

helm install: \
Description: Installs a chart onto the cluster. \
Example: `helm install my-release stable/nginx-ingress`

helm upgrade: \
Description: Upgrades a release to a new version of a chart. \
Example: `helm upgrade my-release stable/nginx-ingress`

helm uninstall: \
Description: Uninstalls a release from the cluster. \
Example: `helm uninstall my-release`

helm list: \
Description: Lists all installed releases. \
Example: `helm list`

helm status: \
Description: Displays the status of a release. \
Example: `helm status my-release`

helm rollback: \
Description: Rolls back a release to a previous revision. \
Example: `helm rollback my-release 1`

helm repo add: \
Description: Adds a chart repository. \
Example: `helm repo add stable https://charts.helm.sh/stable`

helm repo update: \
Description: Updates the local cache of available charts from the configured repositories. \
Example: `helm repo update`




### Example

```
# to add repo 
helm repo add <repo name>

# search nginx app
helm search repo nginx

# list repo in all ns
helm list -A

# to install 
helm install nginx bitnami/nginx --version 15.1.0
helm install nginx bitnami/nginx  -f values.yaml

# check release details
helm history nginx

# rollback to prev. version
helm rollback nginx 1 # here 1 is release version

# pull chart and values file
helm pull --untar bitnami/nginx

# to upgrade
helm upgrade nginx bitnami/nginx --version 14.2.2
```


**helm history eg :**

Description: View the release history of a deployed chart.

Example: `helm history my-release`

Output:

```perl
REVISION 	UPDATED                 	STATUS    	CHART       	APP VERSION   	DESCRIPTION
1        	Tue Aug 10 15:23:42 2023	DEPLOYED  	my-chart-1.0.0	1.2.3         	Initial install
2        	Tue Aug 12 09:17:58 2023	UPGRADED  	my-chart-1.1.0	2.0.0         	Upgrade to version 1.1.0
```



## Helm Cheat Sheet

![image](https://github.com/rizwan141/k8s/assets/103893307/d6485912-4b87-4ee1-9327-72a9f2c95538)

