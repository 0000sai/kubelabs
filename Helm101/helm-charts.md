# Helm Charts Deep dive

You already know what a Helm chart is. Now, we are going to see the structure of a Helm chart.

First, a folder must be created to house all the files pertaining to the Helm chart. This folder should be named the same as the chart itself. Drawing inspiration from the official Helm docs, let's imagine we are creating a Helm chart for Wordpress. The general file structure would look like this: 

```
📦Wordpress
 ┣ 📂charts
 ┣ 📂templates
 ┣ 📜Chart.yaml
 ┗ 📜values.yaml
```

First, let's consider the [Chart.yaml](./Wordpress/Chart.yaml). This is where **resources** are defined. Anything from a simple pod to a complex, full-blow web application can be defined here. The ```Chart.yaml``` provided here is taken from the Helm docs and describes the file in great detail. 

Next, let us consider the templates folder. Inside this folder, you may define as many Helm templates as you wish. In this case, I have added a template called [configmap.yaml](./Wordpress/templates/configmap.yaml). As you can see, the template uses a placeholder notation ```{{}}``` in order specify that these values can be dynamically changed later on, and this is where the ```values.yaml``` comes in.

The [values.yaml](./Wordpress/values.yaml) is, simply put, the place where the values passed into the Helm template are stored. The values stored within this file can then be accessed by templates using ```.Values.<value>```.

Finally, we have the the ```charts``` folder which holds the chart dependencies. If this chart defined within Chart.yaml depends on any other charts, that information would be stored here.

## Hands on lab

Firstly, you must have an active Kubernetes cluster. The easiest way to get this up and running is using Minikube. Please refer to the Minikube section of kubelabs for information regarding this.

If you have a Kubernetes cluster up and running, then it's time to install Helm. The installation is fairly straightforward, and the full installation steps can be found [here](https://helm.sh/docs/intro/install/). Run the Helm create command to get started:

```
helm create hands-on-helm
```

You will notice that the above directory structure has now been created. You will notices that these are not empty files, but have detailed descriptions and templates within them. If you need to dive deeper into any of these generated files, feel free to open them up and have a look!