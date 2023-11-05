# phpGedView-container

Goal of this repo is containerize PhpGedView.

*[PhpGedView](https://wiki.phpgedview.net/) (PGV) is a revolutionary genealogy program which allows you to view and edit your genealogy using a web interface. As a flexible, collaborative web server program, hosted online, PhpGedView has full editing capabilities, full privacy functions, can import standard GEDCOM text files from most genealogy programs, and it supports multimedia like photos and document images.*

It has a last stable version 4.2.4 (from 2011) build for php 5.3 and MySQL 5.1 and "current" 4.3 version that is more up to date but installed from source code directly. 

I aim to create docker images for PhpGedView v4.3 that would be "up to date", easily run locally or in the cloud.

## Usage

If you want to run PhpGedView locally just clone the repo and run ```docker compose up```. This will download mswietlicki/phpgedview:latest from docker hub and mount /config/config.php, /index and /media from current directory.

After that you can access PhpGedView in http://localhost

**WARNING: During install DO NOT USE dbuser: 'root' and empty. Because the way session.php is written this will show you "site_unavailable" message after setup.**

## Build image

To build docker image yourself

```sh
cd phpGetView
docker build -t phpgedview .
```

