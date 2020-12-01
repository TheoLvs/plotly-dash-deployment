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

### Deploying on Heroku
Heroku is the most simple server provider. You can create and deploy apps for free in just a few minutes. That's what we are going to do here : 

- Create your dash app, eg ``app.py``
- Create a requirements file, eg ``requirements.txt``. You can use tools such as ``pipreqs``, ``pipenv`` or other environment managers to help you create the right file. 
- Don't forget to add if not present the requirements to ``gunicorn`` in your requirements file
- Create a Procfile - it's a text file to help Heroku understand what file to be launched on the server. Write in it the following command. 
```
web: gunicorn app:server
```
-  
