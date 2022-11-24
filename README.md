# Django-k8s tuto 

- Apply config by typing : 
```bash
kubectl apply -f pg-deployment.yaml
```
```bash
kubectl apply -f django-app.yaml
```
<h5> You can now test the application using the services. However, the services are internal to minikube, and you won’t be able to access them through the browser. You can counter this by using the port-forward command to direct the internal port to an external port that can be accessed locally. To do that, run the command below :</h5>

```bash
kubectl port-forward svc/leads 8000:80
```
<hr>
<h2>Run commands in pods :</h2>
<h5>Your application is running, but you haven’t done the migrations for the database or created a superuser. To do this, you need to open an interactive Bash shell so that you can run commands on your pods. The command to create an interactive shell requires the name of the pod, and you can get that by running kubectl get pods. </h5>
<h4> Open the interactive bash by running the command below:</h4>

```bash
kubectl exec -it pod-name -- bash
```
<h4>Now, you can run the migration commands by running the following command:</h4>

```bash
python manage.py makemigrations && python manage.py migrate
#------Create a superuser by running the command below and filling in the prompt:
python manage.py createsuperuser
```
<h4>[+]- Now, you can use the credentials you inputted above to access the admin of your application (http://127.0.0.1:8000/admin/). Once all that’s done, you’ll be able to access the application and use it however you like.</h4>

