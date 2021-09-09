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
6. Verify the app locally : open your browser to http://127.0.0.1:8080/ or whatever port you set, if you've changed the local port.

### Build a container image for the App
You can locally build a container image using docker, to verify that you can run the app within a container.

```
docker build -t python-flask-example .
```

Verify the image was was built, by listing the images using ``` docker image ls```

Now, run your local container and confirm you can access the web app running in the container
```
docker run -d -p 5000:5000 python-flask-example:latest
```

And open your browser to http://127.0.0.1:5000/ 


## Build and test the app in OCI DevOps

Now that you've seen how you can locally build and test this app, let's build our CI/CD pipeline in OCI DevOps Service.

### Create External Connection to your Git repository 

1. Create a [DevOps Project](https://docs.oracle.com/en-us/iaas/Content/devops/using/devops_projects.htm) or use and an existing project. 
2. Create an External Connection to your Github repoistory in your DevOps project.
   - Create a Personal Access Token (PAT): https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token
   - In the OCI Console, Go to Identity & Security -> Vault and create a [Vault]( https://docs.oracle.com/en-us/iaas/Content/KeyManagement/Concepts/keyoverview.htm) in compartment of your own choice.
   - Create a Master Key that will be used to encrypt the PATs. 
   - Select Secrets from under Resources and create a secret using PAT obtained from Github account.
   - Make a note of the OCID of the secret.
   - Now, go to the desired project and select External Connection from the resources.
   - Select type as Github and provide OCID of the secret under Personal Access Token.
   - Finally, allow Build Service (dynamic group with DevOps Resources) to use a PAT secret by writing a policy in the root compartment as: ``` Allow dynamic-group dg-with-devops-resources to manage secret-family in tenancy```





