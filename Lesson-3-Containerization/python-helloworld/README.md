# Move to the correct directory to build the Dockerfile 
cd DevOps_Microservices/Lesson-3-Containerization/python-helloworld
# Ensure Docker Desktop is running locally
docker --version
# Build an image using the Dockerfile in the current directory
docker build -t python-helloworld .
docker images
# Run a container
docker run -d -p 5000:5000 python-helloworld
# Check the output at http://localhost:5000/ or http://0.0.0.0:5000/ or http://127.0.0.1:5000/
docker ps
# Now, stop the container.
# Tag locally before pushing to the Dockerhub
# Replace igithiu/ with your Dockerhub profile
docker tag python-helloworld igithiu/python-helloworld:v1.0.0
docker images
# Log into the Dockerhub from your local terminal
docker login
# Replace igithiu with your Dockerhub profile
docker push igithiu/python-helloworld:v1.0.0
# Check the image in your Dockerhub online at https://hub.docker.com/repository/docker/igithiu/python-helloworld
# Assuming the Kubernetes cluster is ready
kubectl get nodes
# Deploy the App from Dockerhub to the Kubernetes Cluster
kubectl create deploy python-helloworld --image=igithiu/python-helloworld:v1.0.0
# See the status
kubectl get deploy,rs,svc,pods
# Port forward 
kubectl port-forward pod/python-helloworld-5df47ccdd-jw84x --address 0.0.0.0 5000:5000















