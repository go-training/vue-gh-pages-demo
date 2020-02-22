# Vue.js Demo

Deploy Vue.js app to GitHub Pages using drone in five minutes.

## Project setup

```sh
yarn install
```

### Compiles and hot-reloads for development

```sh
yarn serve
```

### Compiles and minifies for production

```sh
yarn build
```

### Lints and fixes files

```sh
yarn lint
```

### Customize configuration

See [Configuration Reference](https://cli.vuejs.org/config/).

## Create your access token

![screen](./screenshots/New_personal_access_token.png)

## Deploy using Drone

```yml
---
kind: pipeline
name: testing

platform:
  os: linux
  arch: amd64

steps:
- name: release
  image: node:13
  commands:
  - yarn install
  - yarn build

- name: publish
  image: plugins/gh-pages
  settings:
    username:
      from_secret: username
    password:
      from_secret: password
    pages_directory: dist
```
