# MLflow Tracking Docker Image
This repository contains a Dockerfile and associated files to build a Docker image for serving MLflow models. The Docker image is based on Python 3.10.12 and includes the necessary dependencies for running MLflow server.
# 🚀 Quick Start
## Run on Local WSL Ubuntu 22.04

### Need python 3.10
```sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt install python3.10
python3 --version
```
### Install pip
```
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python3 get-pip.py
```
### Install mlflow 
```
python3 -m pip install mlflow
```

## Run mlflow
```
git clone git@github.com:abaidgulshan/mlfow-tracking-model-example.git
cd mlfow-tracking-model-example
python3 train_model.py
```
# ⚙️  Upload artifact to S3 bucket

```
aws s3 cp mlruns/0/da5c2192da744b038920a404c26cb6fd/artifacts/model/*  s3://mlflow-serving-artifect/model/
```

# 🛠️ Building the Docker Image
```
sudo docker build -t mlflow-serving .
```
# 🐳 Docker Run into the container
```
sudo docker run  --name mlflow-api -p 5000:5000 -e MODEL_URI=s3://mlflow-serving-artifect/model/ -e SERVING_PORT=5000 -e  AWS_ACCESS_KEY_ID=XXXX -e AWS_SECRET_ACCESS_KEY=XXXX mlflow-serving
```
* Replace s3://mlflow-serving-artifect/model/ with your actual model URI and provide your AWS access and secret keys.

📝 Notes
* Adjust the Dockerfile and scripts according to your specific use case and model requirements.
* Make sure to replace placeholder values and credentials with your actual information.
* The AWS CLI is included in the image to provide compatibility with AWS services.
* Feel free to contribute and improve this project! 🌟
