# Vue + Flask template


_Flask + Vue.js Web Application Template, inspired by [this](https://github.com/gtalarico/flask-vuejs-template.git) repo._

## Features
* Minimal Flask 1.0 App
* [Flask-RestPlus](http://flask-restplus.readthedocs.io) API with class-based secure resource routing
* [vue-cli 3](https://github.com/vuejs/vue-cli/blob/dev/docs/README.md) + yarn
* [Vuex](https://vuex.vuejs.org/)
* [Vue Router](https://router.vuejs.org/)
* [Axios](https://github.com/axios/axios/) for backend communication
* Heroku Configuration with one-click deployment + Gunicorn



## Template Structure

The template uses Flask & Flask-RestPlus to create a minimal REST style API, and let's VueJs + vue-cli handle the front end and asset pipline.
Data from the python server to the Vue application is passed by making Ajax requests.

## Installation

##### Before you start

Before getting started, you should have the following installed and running:

- Yarn
- Vue Cli 3
- Python 3
- Heroku CLI

##### Template and Dependencies



```bash
# clone repo
$ git clone https://github.com/banjoanton/vue-flask-template.git

# setup virtual env and activate
$ python3 -m venv venv
$ source venv/bin/activate

# install python dependencies
$ pip3 install -r requirements.txt

# install JS dependencies
$ npm install

# You can also use yarn (and must use if you want to deploy)
$ yarn install
```


## Development Server

```bash
# run backend
$ python run.py

# serve frontend from another tab
$ yarn serve
```

The Vuejs application will be served from `localhost:8080` and the Flask API and static files will be served from `localhost:5000`.

The dual dev-server setup allows you to take advantage of
webpack's development server with hot module replacement.

Proxy config in `vue.config.js` is used to route the requests
back to Flask's Api on port 5000.

If you would rather run a single dev server, you can run Flask's
development server only on `:5000`, but you have to build build the Vue app first
and the page will not reload on changes.

```bash
# build application
$ npm run build

# run backend
$ python3 run.py
```


## Production Server

Here are the commands we need to run to get things setup on the Heroku side:

```bash
$ heroku apps:create flask-vuejs-template-demo
$ heroku git:remote --app flask-vuejs-template-demo
$ heroku buildpacks:add --index 1 heroku/nodejs
$ heroku buildpacks:add --index 2 heroku/python
$ heroku config:set FLASK_ENV=production
$ heroku config:set FLASK_SECRET=SuperSecretKey

$ git push heroku
```
