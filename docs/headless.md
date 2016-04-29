# Headless electron testing

Electron requires `xvfb` in headless environments.

For example, on Travis CI:

**`.travis.yml`**
```yml
language: node_js
node_js:
  - "0.10"
  - "0.12"
  - 4
  - 6
addons:
  apt:
    packages:
      - xvfb
install:
  - npm i electron-prebuilt -g
  - export DISPLAY=':99.0'
  - Xvfb :99 -screen 0 1024x768x24 > /dev/null 2>&1 &
  - npm install
script: npm run test
```
