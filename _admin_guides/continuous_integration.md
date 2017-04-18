# Continuous Integration (CI)
Spinnaker's goal is leverage existing CI solutions to build and produce an artifact that can be deployed.

## Enabling Jenkins & Igor to talk to Spinnaker

To enable Igor, Gate to integrate with your Jenkins build you'll need to edit your `spinnaker-local.yml` file.  First configure Jenkins by finding your password  or API Token.  You can find your token here: `http://${YOUR_JENKINS_URL}.armory.io/me/configure`.

Then configure your `/opt/spinnaker/config/spinnaker-local.yml` file and add the following:

```
services:
  igor:
    enabled: true
  jenkins:
    enabled: true
    defaultMaster:
      name: Name-of-Jenkins-Service
      baseUrl: http://${YOUR_JENKINS_URL}
      username: ${YOUR_USERNAME}
      password: ${API_TOKEN}
```

Make sure to restart the Igor service: `sudo docker restart igor`


## Purpose
Igor is an API that communicates with Jenkins and is responsible for executing jobs, reading state of jobs or  