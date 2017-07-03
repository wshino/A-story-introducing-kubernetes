A story introducing kubernetes

---

About me

- TK
- Software Engineer
- Bigdata div.

---

Why Kubernetes ?

---

Before

- Multiple Docker environments
- Resources are not used effectively
- Management also tough

---

Mission

- Make Development, Staging and Production environment into one cluster
- Batch processing also runs in container
- Easy management and Resource monitoring

---

Necessary function

- Blue-Green Deployment
- Resource efficiency
- Error handling and Rollback

---

Blue-Green Deployment

- Set "color: blue", "color: green" to metadata of deployment
- Set "color: blue" to metadata of service

---

Blue-Green Deployment

```bash
COLOR=`kubectl get svc -l app=v1-frontend -o json | jq '.items[0].spec.selector.color' -r`
```

- Replace service selector to blue or green
- kubectl apply -f service.yml


---

Dependencies among Pods

- AppController
- https://github.com/Mirantis/k8s-AppController

```yaml
apiVersion: appcontroller.k8s/v1alpha1
kind: Dependency
metadata:
  name: dependency-1
parent: pod/mysql
child: job/db-migration
```
