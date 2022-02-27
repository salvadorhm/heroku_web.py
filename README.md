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

### 7. Config Heroku buildpack -> Python

```bash
$ heroku buildpacks:set heroku/python
```

### 8. Add files to git

```bash
$ git add .

$
```

### 9. Commit changes

```bash
$ git commit -m "Basic schema"

[main d4aaf89] Basic schema
 1 file changed, 1 insertion(+), 1 deletion(-)
```

### 10. Push changes to GitHub

```bash
$ git push -u origin main

Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 290 bytes | 290.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/GITHUB_USER/REPO_NAME.py.git
   d54f035..d4aaf89  main -> main
branch 'main' set up to track 'origin/main'.
```

### 11. Pushh changes to Heroku

```bash
$ git push heroku main

Enumerating objects: 30, done.
Counting objects: 100% (30/30), done.
Delta compression using up to 16 threads
Compressing objects: 100% (21/21), done.
Writing objects: 100% (30/30), 4.35 KiB | 4.35 MiB/s, done.
Total 30 (delta 4), reused 3 (delta 0), pack-reused 0
remote: Compressing source files... done.
remote: Building source:
remote: 
remote: -----> Building on the Heroku-20 stack
...
remote: Verifying deploy... done.
To https://git.heroku.com/APP_NAME.git
 * [new branch]      main -> main
```

### 12. Open Web Browser

```bash
$ heroku open

* OPEN WEB BROWSER
```

### 13. Install heroku cli

```bash
$ heroku logs --tail

2022-02-27T19:53:50.466499+00:00 app[api]: Release v1 created by user heroku_user@gmail.com
2022-02-27T19:53:50.466499+00:00 app[api]: Initial release by user heroku_user@gmail.com
2022-02-27T19:53:50.696294+00:00 app[api]: Enable Logplex by user heroku_user@gmail.com
2022-02-27T19:53:50.696294+00:00 app[api]: Release v2 created by user heroku_user@gmail.com
2022-02-27T19:57:28.000000+00:00 app[api]: Build started by user heroku_user@gmail.com
```
