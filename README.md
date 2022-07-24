# Helm Task

- # Create a helm chart for the app below and deploy it (please try to keep everything thing changeable using values.yaml)
[https://github.com/tradebyte/DevOps-Challenge](https://github.com/tradebyte/DevOps-Challenge)
- Deploy Jenkins Chart on the cluster and login to jenkins
Bonus: package, sign and push your chart to [https://artifacthub.io/](https://artifacthub.io/)

 

```bash

$ mkdir helm_lab 
$ helm create helm-test 
```

# Then, Create template files

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled.png)

# Then, Install chart

```bash
$ helm install test helm-test/ --values helm-test/values.yaml
```

# Then, check

```bash
$ kubectl get pods
```

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%201.png)

# Then, get the service url

```bash
$ minikube service my-app-np --url
```

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%202.png)

# Then, test the URL

# [http://192.168.49.2:30080/](http://192.168.49.2:30080/)

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%203.png)

# Deploy Jenkins Chart on the cluster and login to jenkins

- First add jenkins repo

```bash
$ helm repo add jenkins https://charts.jenkins.io
```

- Then, update it

```bash
$ helm repo update 
```

- Then, install jenkins on the cluster

```bash
$ helm install jenkins jenkins/jenkins
```

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%204.png)

- Then run this command to get the password

```bash
$ kubectl exec --namespace default -it svc/jenkins -c jenkins -- /bin/cat /run/secrets/additional/chart-admin-password && echo
```

- Then, get the URL

```bash
$ kubectl --namespace default port-forward svc/jenkins 8080:8080
```

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%205.png)

- Then, test

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%206.png)

# Bonus: package, sign and push your chart to [https://artifacthub.io/](https://artifacthub.io/)

- First we pack our charts

```bash
$ helm package . -d charts
```

- Then, indexing it

```bash
$ helm repo index charts
```

- Then push it to git hub and go to create page

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%207.png)

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%208.png)

```bash

```

- Copy the link and go to Artifact Hub
- Sign in Artifact Hub and go to control panal

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%209.png)

- Then  put the link

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%2010.png)

- and the Repo will be created successfully

 

![Untitled](Helm%20Task%20c65b7ce6669b45079a5bab4bd3ee01ba/Untitled%2011.png)