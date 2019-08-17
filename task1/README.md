# Task 1

Building and Pushing Docker Images To Nexus3

## Objective

Building an pipeline that can build docker image, tag it and push to Nexus repository.

## Prerequisites

1. Nexus URL where docker repository lives.
2. Jenkins Slave where Docker is install and able to login to Nexus Docker Repository.
3. Git Repository URL of your Dockerfile.
4. Created credentials in Jenkins to access your Git Repository.

## Pipeline Steps

1. Create a Pipeline Job by selecting

   New Item --> Pipeline --> Give JobName --> then OK

2. Paste the Jenkins file in the text area of pipeline at the bottom.

3. Replace the Git URL and Credentials to clone repository. If you don't replace build will fail as those credentials are my.

```
git credentialsId: 'REPLACEME', url: 'REPLACEME'
```

4. Replace Nexus URL with your Nexus domain or ip:port and give any image name you like to have in repository.

```
docker tag moviesinfo REPLACEMEWITHNEXUSURL/REPLACEWITHIAMGENAME:${VERSION}

docker push REPLACEMEWITHNEXUSURL/EPLACEWITHIAMGENAME:${VERSION}
```

5. Once you save it. Run the Job and it will fail as we have to pass `Version` parameter and it won't show up until we run once. First fail is fine.

6. Run the Job again by clicking `Build with Parameter` and provide the version for your image and run it.

7. If it's successful, it will show up in your docker registery and if it fails check the logs to find out.
