# Helm
- package manager for kubernetes
- used for deploying the application in kubernetes
```bash

# install helm on ubuntu
sudo snap install helm --classic
helm version
```

## chart
- chart is a helm package which contains all the yaml files to deploy the application and its components
```bash

helm create <chart-name>
helm create frontend-chart

# remove everything from templates directory
# copy your yaml files (deployment.yaml and service.yaml) in templates directory

# install the chart
# note: execute this command from parent directory of chart
helm install <chart-name> <chart-path>
helm install frontend ./frontend-chart

```
