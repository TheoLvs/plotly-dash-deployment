# plotly-dash-deployment
![](https://dash-gallery.plotly.host/Manager/apps_data/dash-oil-and-gas/thumbnail_0a718df0-9ce7-11e9-8982-0242ac11004a.png)
> A primer for plotly Dash deployments

## Creating a Dash application
Before deployment, the first step if of course to create your own application. <br>
You can follow the guidelines in Dash official documentation https://dash.plotly.com/installation

## Deploying your Dash application
https://dash.plotly.com/deployment
Dash/Plotly offers a paid service to super easily deploy and manager your applications. Yet as most of it is open source, and you may want a simple thing for a prototype, you can simply deploy it in your own server.

Then you have several options: 
- Beginners - Deploy it on a simple Heroku server
- Advanced - Deploy it on a cloud server (AWS, GCP, Azure) with docker containers

### Deploying on Heroku from GitHub
Heroku is the most simple server provider. It's even more simpleYou can create and deploy apps for free in just a few minutes. That's what we are going to do here : 

- Create your dash app, eg ``app.py``
- Create a requirements file, eg ``requirements.txt``. You can use tools such as ``pipreqs``, ``pipenv`` or other environment managers to help you create the right file. 
- Don't forget to add if not present the requirements to ``gunicorn`` in your requirements file
- Create a Procfile - it's a text file to help Heroku understand what file to be launched on the server. Write in it the following command. 
```
web: gunicorn app:server
```
- As of ``2020-12-01``, Dash documentation is not totally correct when it comes to deployment on Heroku, you should correctly link the server variable in Python and the declaration in the ``Procfile`` :
```python
# Add following line in your app.py script
server = app.server

# Write the Procfile
# - app refer to the file name app.py
# - server refer to the variable name for the Flask Server 
web: gunicorn app:server
```
- Deploy directly on Heroku from GitHub, you can follow the instructions below

  - Create a new application
![](img/deploy1.jpg)
  - Find the right name and server region
![](img/deploy2.jpg)
  - Link via github, search for your repo and click on connect
![](img/deploy3.jpg)
  - Deploy manually by clicking on deploy and choosing the right github branch
![](img/deploy4.jpg)

  - You can even set up a CI/CD process with auto-deploys by playing with the auto-deploy section
![](img/deploy5.jpg)

  - You are all set ! Your app should be live ! 
![](img/deploy7.jpg)
  


#### Problems you can encounter
- Having your app not at the root of the repo, you can use subdir buildpack
- Not linking correctly 

If your app does not work, you can check in the logs why it failed : 
![](img/deploy6.jpg)