# Docker Image for SnowEX Hackweek 2021

This repository builds a [JupyterHub](https://jupyter.org/hub) environment with Repo2Docker [GitHub Actions CI](https://github.com/jupyterhub/repo2docker-action)

[![Action Status](https://github.com/snowex-hackweek/docker-image/workflows/CI/badge.svg)](https://github.com/snowex-hackweek/docker-image/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/uwhackweek/snowex)](https://hub.docker.com/r/uwhackweek/snowex/tags)
[![BinderHub](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/snowex-hackweek/docker-image/main?urlpath=git-pull?repo=https://github.com/snowex-hackweek/website%26amp%3Bbranch=main%26amp%3Burlpath=lab)

https://hub.docker.com/r/uwhackweek/snowex/tags

### How to update the image

build with GitHub Actions simply by pushing to GitHub

* pull requests trigger image building without pushing to DockerHub
```
git clone https://github.com/snowex-hackweek/docker-image
cd docker-image
git checkout dev
# make sure dev branch is up-to-date with master
git merge master
# modify environment.yml or other files in binder/
git commit -a -m "modified binder/environment to my liking"
git push
# go to github.com and create a pull request to merge dev changes into master
```

* PRs trigger re-building image
* Commits to master build image and push to DockerHub tagged by github commit sha and 'latest'

### Pull your image to run a local JupyterLab session
```
docker pull uwhackweek/snowex:latest
docker run -it --name HACKWEEK -p 8888:8888 uwhackweek/snowex:latest jupyter lab --ip 0.0.0.0
docker stop HACKWEEK
docker rm HACKWEEK
```

### Point to a specific tagged image in JupyterHub config
(image: uwhackweek/snowex:eb19306d469b)
https://zero-to-jupyterhub.readthedocs.io/en/latest/reference/reference.html?highlight=profile_list#singleuser-profilelist
