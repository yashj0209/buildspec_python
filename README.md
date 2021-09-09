# Getting Started with OCI DevOps
This is a sample project, using Python with Flask framework to create a simple weight convertor web application. With [OCI DevOps Service](https://www.oracle.com/devops/devops-service/) and this project, you'll be able to build, test and deploy this application to Oracle Container Engine for Kubernetes (OKE).

In this example, you'll build a container image of the Python Flask app, push your built container to the OCI Container Registry (OCIR), then deploy the app to Oracle Container Engine for Kubernetes (OKE) all using the OCI DevOps service.

## Running the example locally 

### Clone the Repository 
The first step is to download the repository to your local workspace.

```
git clone git@github.com:yashj0209/buildspec_python.git
cd buildspec_python
```

### Install the Requirements and Run the App
Open a terminal and test out the python Flask web app example which acts as a simple weight metric convertor.

1. Downlaod and install python(3.x or higher): https://www.python.org/downloads/
2. Setup python3 virtual environment : ``` python3 -m venv venv ```
3. Activate the virtual environment : ```source venv/bin/activate ``` 
4. Install requirements (Flask) : ``` python3 -m pip install -r requirements.txt ```
5. Start the flask app : ``` python3 app.py ```
6. Verify the app locally : open your browser to http://127.0.0.1:8080 or whatever port you set, if you've changed the local port 




