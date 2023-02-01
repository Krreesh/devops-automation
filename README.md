# devops-automation

<h2>Kubernetes Status</h2>
<pre>
[ec2-user@ip-172-31-85-97 ~]$ k get svc
NAME                  TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)          AGE
kubernetes            ClusterIP   10.96.0.1       <none>        443/TCP          20d
mysql                 NodePort    10.97.199.243   <none>        3306:31819/TCP   12h
springboot-crud-svc   NodePort    10.110.62.170   <none>        8080:30463/TCP   11h
[ec2-user@ip-172-31-85-97 ~]$ k port-forward service/springboot-crud-svc --address=0.0.0.0 8080:8080
Forwarding from 0.0.0.0:8080 -> 8989
Handling connection for 8080

^C[ec2-user@ip-172-31-85-97 ~]$ k get po
NAME                                          READY   STATUS    RESTARTS      AGE
angular-app                                   1/1     Running   4 (11h ago)   42h
mysql-fb4dd8d-k9sp6                           1/1     Running   1 (11h ago)   14h
springboot-crud-deployment-7f9bb7cfdb-8946p   1/1     Running   0             70m
springboot-crud-deployment-7f9bb7cfdb-mnnrd   1/1     Running   0             70m
springboot-crud-deployment-7f9bb7cfdb-xsmjz   1/1     Running   0             11h
[ec2-user@ip-172-31-85-97 ~]$ k port-forward service/springboot-crud-svc --address=0.0.0.0 8080:8080
Forwarding from 0.0.0.0:8080 -> 8989
Handling connection for 8080
</pre>
<h2>Minikube Dashboard</h2>
<pre>
[ec2-user@ip-172-31-85-97 ~]$ minikube dashboard
* Verifying dashboard health ...
* Launching proxy ...
* Verifying proxy health ...
* Opening http://127.0.0.1:37925/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/ in your default browser...
  http://127.0.0.1:37925/api/v1/namespaces/kubernetes-dashboard/services/http:kubernetes-dashboard:/proxy/
</pre>
<h2>Started kube proxy to view dashboard in browser</h2>
<pre>
[ec2-user@ip-172-31-85-97 ~]$ k proxy --address=0.0.0.0 --accept-hosts '.*'
Starting to serve on [::]:8001
</pre>
