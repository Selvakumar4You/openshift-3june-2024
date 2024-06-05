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
