# docker-jenkins-frontend

> Docker image for deployments and testing with Jenkins and other useful tools.

:warning: Current in dev :warning:

## Tools  

  - Google Chrome -> `google-chrome-stable` (customizable version)
  - Xvfb
  - Jenkins (of course :smile:)

## Run

Run as `root` user and bind the **jenkins_home** directory to your system:

    docker run -p 8080:8080 -p 50000:50000 -v yourFavouritePath:/var/jenkins_home jenkins

Run as `jenkins` user:

    docker run -u jenkins -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins

Run and bind also the **.ssh** directory to share your SSH key with the container:

    docker run -p 8080:8080 -p 50000:50000 -v yourFavouritePath:/var/jenkins_home jenkins -v yourSSHfolderPath:/var/jenkins_home/.ssh



## Important notes

Make sure your host user you will use to run the container will have the correct `guid`. Alternatively you can modify the Dockerfile and change the `guid` of the `jenkins` user inside the container.  

Modify this line:

    RUN usermod -u 1011 jenkins \
      && groupmod -g 1011 jenkins

And change the **1011** with the `guid` of your user.

## Reference

This is an extension of the [official Jenkins docker image](https://hub.docker.com/_/jenkins/).

## Todo

- docker-compose
- server SMPT
- Ruby for Capistrano

## License

[MIT](https://github.com/LasaleFamine/docker-jenkins-frontend/blob/master/LICENSE.md) &copy; LasaleFamine
