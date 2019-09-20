# GithubAction for PHPInsights

## Usage

You can use it as a Github Action like this:

_.github/workflows/main.yml_
```
on: [push, pull_request]
name: Main
jobs:
  phpinsights:
    name: PHP-Insights
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: PHP-Insights
      uses: docker://tienvx/phpinsights-action
```

_to use a custom config for example, -v or --min-quality option:_
```diff
on: [push, pull_request]
name: Main
jobs:
  phpinsights:
    name: PHP-Insights
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master
    - name: PHP-Insights
      uses: docker://tienvx/phpinsights-action
+      with:
+        args: "-v --min-quality=70 --min-complexity=70 --min-architecture=50 --min-style=80"
```

**You can copy/paste the .github folder (under examples/) to your project and thats all!**

## Docker

A Docker-Image is built automatically and located here:
https://hub.docker.com/r/tienvx/phpinsights-action

You can run it in any given directory like this:

`docker run --rm -it -w=/app -v ${PWD}:/app tienvx/phpinsights-action:latest`
