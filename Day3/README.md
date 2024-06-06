# Day 3

## Lab - Deploying multi-pod(wordpress & mariadb) wordpress application

![wordpress](wordpress-dep.png)

Let's deploy wordpress and mariadb 
```
cd ~/openshift-3june-2024
git pull
cd Day3/persistent-volume/wordpress

./deploy.sh
```

Expected output
![wordpress](wordpress1.png)
![wordpress](wordpress2.png)
![wordpress](wordpress3.png)
![wordpress](wordpress4.png)
![wordpress](wordpress5.png)
![wordpress](wordpress6.png)
![wordpress](wordpress7.png)

Once you are done with this exercise, you may clean up the resources
```
cd ~/openshift-3june-2024
cd Day3/persistent-volume/wordpress

./delete-all.sh
```

Expected output
![wordpress](wordpress8.png)

## Lab - Deploying mongodb with Persistent volume
```
cd ~/openshift-3june-2024
git pull
cd Day3/persistent-volume/mongodb

oc apply -f mongodb-pv.yml
oc apply -f mongodb-pvc.yml
oc apply -f mongodb-deploy.yml
```

Expected output
![mongodb](mongodb1.png)
![mongodb](mongodb2.png)
![mongodb](mongodb3.png)
![mongodb](mongodb4.png)
![mongodb](mongodb5.png)
![mongodb](mongodb6.png)

## Lab - Deploying redis database with persistent volume
```
cd ~/openshift-3june-2024
git pull
cd Day3/persistent-volume/redis

oc apply -f redis-pv.yml
oc apply -f redis-pvc.yml
oc apply -f redis-deploy.yml
```

Expectd output
![redis](redis1.png)
![redis](redis2.png)
![redis](redis3.png)
![redis](redis4.png)
![redis](redis5.png)

You may delete the redis deployment once you are done with this exercise.
```
cd ~/openshift-3june-2024
cd Day3/persistent-volume/redis

oc delete -f redis-deploy.yml
oc delete -f redis-pvc.yml
oc delete -f redis-pv.yml

oc get po,pv,pvc
```

Expected output
![redis](redis6.png)


## Lab - Using configmap and secrets to store configuration data and credentials in secrets

#### Things to note
<pre>
- config map is used to store non-sensitive data
- config map can store many key/value pairs
- For example
  - We can store the JAVA_HOME=/usr/lib/jdk11 path 
  - We can store application log path
- secret is also a map that can store several key pairs
- the only difference between configmap and secret is , the values stores in secrets is opaque, hence we can securely store passwords, retrieve them on need basis and use them in our application
</pre>

Let's understand how to practically use configmap and secrets in the wordpress & mariadb deployments
```
cd ~/openshift-3june-2024
git pull
cd Day3/configs-and-secrets/wordpress

./deploy.sh
oc get po,pv,pvc,svc,route
```

Expected output
![cm](cm1.png)
![cm](cm2.png)
![cm](cm3.png)
![cm](cm4.png)
![cm](cm5.png)
![cm](cm6.png)

Once you are done with this lab exercise, you may clean up the resources as shown below
```
cd ~/openshift-3june-2024
cd Day3/configs-and-secrets/wordpress

./delete-all.sh
oc get po,pv,pvc,svc,route
```

Expected output
![cm](cm7.png)


## Info - Helm Overview
<pre>
- Helm is a package manager that can be used to package your kubernetes/openshift cloud native applications
- Just like package managers like apt(apt-get), yum, rpm, dnf, npm, pip are used to install,uninstall, update/upgrade softwares, we can use Helm package manager to install/uninstall/upgrade applications into Kubernetes/Openshift
- Helm is also intergrated with Openshift
- Helm packaged applications are called Charts
- Helm chart is a tar.gz compressed that follows a specific folder structure within the compressed file
</pre>


## Lab - Creating a custom helm chart for our wordpress application deployment
```
cd ~/openshift-3june-2024
git pull
cd Day3/helm

helm version
helm create wordpress
tree wordpress

cd wordpress/templates
rm -rf *
cd ../..
cp manifest-scripts/*.yml wordpress/templates
cp values.yaml wordpress
tree wordpress
```

Let's create a wordpress helm chart package
```
cd ~/openshift-3june-2024
cd Day3/helm
ls
helm package wordpress
ls
```

Installing helm wordpress chart into openshift
```
cd ~/openshift-3june-2024
cd Day3/helm
ls
helm install wp wordpress-0.1.0.tgz
helm list
```

Expected output
![helm](helm1.png)
![helm](helm2.png)
![helm](helm3.png)
![helm](helm4.png)
![helm](helm5.png)
![helm](helm6.png)
![helm](helm7.png)

## Info - DaemonSet Overview
<pre>
- In case, we need one Pod deployed in every node we can choose to deploy the application as a DaemonSet
- The DaemonSet controller, check the number of nodes available in the openshift cluster accordingly it will create so many Pods and deploy them one Pod per node
- In case new nodes join the openshift cluster, the DaemonSet controller automatically add one Pod on that new node as well
- On the similar line, in case when nodes are removed from the openshift cluster, the Pods on those nodes are removed automatically
- We can't manually scale up/down a DaemonSet
- Examples
  - One kube-proxy Pod runs in every node which is a DaemonSet
  - default-dns Pod runs in every node, which is a DaemonSet
  
</pre>
