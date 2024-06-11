Flow of the Project
Web-app/
├──backend/
├  ├──app.py
├  ├── Dockerfile
├  ├──backend-deployment.yaml
├  ├──backend-service.yaml
├  ├──requirements.txt
├   ├──static/
├     │── public/ 
├     ├── index.html 
├     ├── script.js 
├     ├── style.css
├──Frontend/
├   ├──frontend-deployment.yaml
├   ├──frontend- service.yaml
├   ├──-Dockerfile


  ### Overview:- 
  Developing a web application involving a frontend, backend, and a database connection. We are containerizating the application component by Docker and then deploying it to kubernetes cluster and using the GitHub for version control.

  ### Create a Git Repository
  1. Initialize a new repository on Github
  2. Add .gitignore file

 ### Develop a frontend
 1. Create a basic HTML file for frontend like Index.html
 2. Add a javascript file (script.js) to handle form submission and validation
 3. Add CSS files for styling(styles.css)
 4. Commit changes and push it to repository

    commands
    1. git init
    2. git add .
    3. git commit -m "Add basic HtML files and javascript file"
    4. git push
   
Create  a Dockerfile (frontend/Dockerfile) for frontend
5. Build and push the Docker image to Google Container Registry (GCR):
   docker build -t my-frontend .
   docker push gcr.io/kunal-ica1/my-frontend:latest
   
### Develop a backend application
1. Set up a simple Flask application that processes data received from the frontend.
2. Establish the Database connectivity with postgreSQL
3. Create a virtual environment (venv file)
4. Install Flask and SQLAlchemy: 
(pip install Flask FlaskSQLAlchemy psycopg2binary)
5. Create a `requirements.txt` file: 

Flask 
Flask-SQLAlchemy 
psycopg2-binary 
flask_cors 

6. Create  a Dockerfile (backend/Dockerfile) for backend
7. Build and push the Docker image to Google Container Registry (GCR):
   docker build -t my-backend .
   docker push gcr.io/kunal-ica1/my-backend:latest

8. create Kubernetes deployment file for both
9. frontend-deployment.yaml
10. backend-deployment.yaml
11. frontend-service.yaml
12. backend-service.yaml

Apply for kubernetes deployment file
kubectl apply f backend-deployment.yaml 
kubectl apply f backend-service.yaml 
kubectl apply f frontend-deployment.yaml 
kubectl apply f frontend-service.yaml 

### Check the deployment status
kubectl get deployment
kubectl get pods
kubectl get services

Login to Frontend pod and test the backend API endpoint using curl : 
curl X POST http:// backendservice.default.svc.cluster.local:5000/submit H "ContentType: application/json" d '{"value1": "test1", "value2": "test2"}'

###Connect to the database and check the data in the postgre schema
 
