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
