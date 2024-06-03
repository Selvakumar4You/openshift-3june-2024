## Cloning TekTutor Openshift Training Repository (RPS Cloud Linux Machine Terminal )
```
cd ~
git clone https://github.com/tektutor/openshift-3june-2024.git
cd openshift-3june-2024
```

## About our lab environment
- OnPrem Production grade Red Hat OpenShift setup 
- System Configuration
  - 48 virtual cores
  - 755 GB RAM
  - 17 TB HDD Storage
- CentOS 7.9.2009 64-bit OS
- KVM Hypervisor
- 7 Virtual machines
  - Master 1 with RHEL Core OS ( 8 Cores, 128GB RAM, 500 GB HDD )
  - Master 2 with RHEL Core OS ( 8 Cores, 128GB RAM, 500 GB HDD )
  - Master 3 with RHEL Core OS ( 8 Cores, 128GB RAM, 500 GB HDD )
  - Worker 1 with RHEL Core OS ( 8 Cores, 128GB RAM, 500 GB HDD )
  - Worker 2 with RHEL Core OS ( 8 Cores, 128GB RAM, 500 GB HDD )
  - HAProxy Load Balancer Virtual Machine
  - One more VM is created and destroyed during Openshift installation (BootStrap Virtual Machine)
- Linux Server 1 ( 10.10.15.102 ) - Openshift cluster 1 ( 8 participants - user01 thru user07 and user23 )
- Linux Server 2 ( 10.10.15.103 ) - Openshift cluster 2 ( 8 participants - user08 thru user14 and user24 )
- Linux Server 3 ( 10.10.15.101 ) - openshift cluster 3 ( 9 participants - user15 thru user22 and user25 )

- In case you RPS cloud login username is 24MAN0605-u01, then you should login to your respective Linux server as user01 with password 'rps@2345' to the Server 1 (10.10.15.102).

- In case you cloud login username 24MAN0605-u15, then you should login as user15 with password 'rps@2345' to the Server 2 (10.10.15.103).

- In case your RPS cloud login username is 24MAN0605-u25, then you should login to your respective Linux server as user25 with password 'rps@2345' to the Server 3 (10.10.15.101).

## Pre-test - kindly complete the pre-test from your RPS Lab machine
<pre>
https://app.mymapit.in/code4/tiny/M3j7pG
</pre>

Note
<pre>
- You can copy the above pre-test url from the RPS windows cloud lab machine desktop in a file named PRE TEST
- Copy/Paste between your laptop and rps lab machine is disabled as per your bank policy
- You don't have to enable the camera access
- Kindly use your personal email-id while registering ( avoid using BOFA id )
- The link above may not work directly from your work laptop web browser
- Once you are done with the test we will start the training 
- Kindly leave a message via WebEx chat if you have access, otherwise you may tell me
</pre>

## Verifying your Linux lab machine

Check if docker community edition is pre-installed
```
docker --version
```

Expected output
<pre>
[root@tektutor.org openshift-april-2024]# docker --version
Docker version 26.0.1, build d260a54
</pre>

Check the version of oc and kubectl openshift client tools
```
oc version
kubectl version
```

Expected output
<pre>
[root@tektutor.org openshift-april-2024]# <b>oc version</b>
W0415 10:23:48.403940 1673608 loader.go:222] Config not found: /root/ocp4_cluster_ocp/install_dir/auth/kubeconfig
Client Version: 4.14.12
Kustomize Version: v5.0.1
  
[root@tektutor.org openshift-april-2024]# <b>kubectl version</b>
W0415 10:23:52.446759 1673707 loader.go:222] Config not found: /root/ocp4_cluster_ocp/install_dir/auth/kubeconfig
WARNING: This version information is deprecated and will be replaced with the output from kubectl version --short.  Use --output=yaml|json to get the full version.
Client Version: version.Info{Major:"1", Minor:"27", GitVersion:"v1.27.4", GitCommit:"286cfa5f978c4a89c776347c82fa09a232eef144", GitTreeState:"clean", BuildDate:"2024-01-29T22:50:23Z", GoVersion:"go1.20.12 X:strictfipsruntime", Compiler:"gc", Platform:"linux/amd64"}
Kustomize Version: v5.0.1  
</pre>

Check if you are able to list out the nodes in the Openshift cluster
```
oc get nodes
```
Expected output
<pre>
[root@tektutor.org openshift-april-2024]# <b>oc get nodes</b>
NAME                              STATUS   ROLES                         AGE     VERSION
master-1.ocp4.tektutor.org.labs   Ready    control-plane,master,worker   5h35m   v1.27.11+749fe1d
master-2.ocp4.tektutor.org.labs   Ready    control-plane,master,worker   5h35m   v1.27.11+749fe1d
master-3.ocp4.tektutor.org.labs   Ready    control-plane,master,worker   5h35m   v1.27.11+749fe1d
worker-1.ocp4.tektutor.org.labs   Ready    worker                        5h18m   v1.27.11+749fe1d
worker-2.ocp4.tektutor.org.labs   Ready    worker                        5h18m   v1.27.11+749fe1d  
</pre>
