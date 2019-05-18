---
layout: default
title: Docker Base Image
parent: Docker
grand_parent: Projects
nav_order: 1
---
# docker-base

[![Build Status](https://travis-ci.com/madharjan/docker-base.svg?branch=master)](https://travis-ci.com/madharjan/docker-base)
[![Layers](https://images.microbadger.com/badges/image/madharjan/docker-base.svg)](http://microbadger.com/images/madharjan/docker-base)

Docker baseimage based on [phusion/baseimage-docker](https://github.com/phusion/baseimage-docker)

## Changes

* Removed `ssh` service
* Updated to Ubuntu 16.04

## Features

* Environment variables to disable services
* Using scripts in `my_init.d` to initialize services (e.g base-startup.sh, nginx-startup.sh .. etc)
* Using scripts in `my_shutdown.d` to cleanup services before container stop (e.g postfix-stop.sh ..etc)
* Bats ([bats-core/bats-core](https://github.com/bats-core/bats-core)) based test cases

Example:

```bash
docker run -d \
  -e DISABLE_SYSLOG=1 \
  -e DISABLE_CRON=0 \
  --name <container-name> <image-name>:<image-version>
```

## Ubuntu 16.04 (docker-base)

### Environment

| Variable       | Default | Set to disable |
|----------------|---------|----------------|
| DISABLE_SYSLOG | 0       | 1              |
| DISABLE_CRON   | 0       | 1              |

## Build

### Clone this project

```bash
git clone https://github.com/madharjan/docker-base
cd docker-base
```

### Build Container `baseimage`

```bash
# login to DockerHub
docker login

# build
make

# tests
make run
make tests
make clean

# tag
make tag_latest

# release
make release
```

### Tag and Commit to Git

```bash
git tag 16.04
git push origin 16.04
```
