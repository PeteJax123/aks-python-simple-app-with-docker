# Step 1: Build the docker image
docker build -t chatgpt_python_app .

chatgpt_python_app = This is the name of the image. You can choose anything any name.

# Step 2: Create Azure Container Registry (Skip this step if an ACR already exists) 
az acr create --resource-group <resource-group-name> --name <acr-name> --sku Basic

# Step 3: Tag the Docker image
docker tag chatgpt_python_app <acr-login-server>/chatgpt_python_app

# Step 4: Login to ACR
az acr login --name <acr-name>

# Step 5: Push Docker image to ACR
docker push <acr-login-server>/chatgpt_python_app

kubectl apply -f chatgpt-python-app-deployment.yaml
