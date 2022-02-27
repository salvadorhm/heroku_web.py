# Heroku-Web.py-Git

Web.py webapp sample with Heroku-Docker

***

## 1. GitHub repo

1. Create a new Github repo with any name and README.md file.

## 2. Gitpod for development

1. Create and account in [GITPOD](https://gitpod.io) - Use Github credentials.
2. Copy the Github URL.
3. Paste de Github URL in Gipod.

```bash
https://gitpod.io#GITHUB_REPO_URL

* THIS CREATE A CONAINER WITH VS CODE 
```

***

## Local development

1. Copy and paste Dockerfile.
2. Copy and paste heroku.yml
3. Create webapp/ copy and paste all files [app.py, requirements.txt, wsgi.py, templates/, base.html, index.html]

### 1. Install libraries

Open webapp/ and run the next commands.

```bash
$ pip3 install -r requirements.txt

Collecting web.py
  Downloading web.py-0.62.tar.gz (1000 kB)
  ...
```

### 2. Run webapp

For debbug the webapp.

```bash
$ python3 app.py

http://0.0.0.0:8080/
```

### 3. Run webapp  with gunicorn

For deploy the webapp.

```bash
$ gunicorn --bind 0.0.0.0:8080 app:wsgiapp

[2022-02-26 22:01:24 +0000] [5573] [INFO] Starting gunicorn 20.1.0
[2022-02-26 22:01:24 +0000] [5573] [INFO] Listening at: http://0.0.0.0:8080 (5573)
[2022-02-26 22:01:24 +0000] [5573] [INFO] Using worker: sync
[2022-02-26 22:01:24 +0000] [5575] [INFO] Booting worker with pid: 5575
```

***

## Deploy to Heroku - Git

### 1. Sign up Heroku

* Sign Up in [Heroku](https://dashboard.heroku.com/)

### 2. Install heroku cli

```bash
$ curl https://cli-assets.heroku.com/install-ubuntu.sh | sh

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  1232  100  1232    0     0   5154      0 --:--:-- --:--:-- --:--:--  5133
```

### 3. Heroku login (Password -> Heroku API KEY)

```bash
$ heroku login -i

heroku: Enter your login credentials
Email: 
```

### 4. Create remote container in Heroku

```bash
$ heroku create WEBAPP_NAME

Creating ⬢ WEBAPP_NAME... done
https://WEBAPP_NAME.herokuapp.com/ | https://git.heroku.com/WEBAPP_NAME.git
```

### 5. Confirm remote heroku

```bash
$ git remote -v

origin  https://github.com/GITHUB_USER/REPO_NAME.py.git (fetch)
origin  https://github.com/GITHUB_USER/REPO_NAME.py.git (push)
```

### 6. Push to remote container

* This use the Dockerfile and heroku.yml for createa a remote contianer in Heroku.

```bash
$ heroku git:remote -a WEBAPP_NAME

set git remote heroku to https://git.heroku.com/WEBAPP_NAME.git
```


heroku buildpacks:set heroku/python

