This project contains a Dockerfile to create a [jupyter](https://jupyter.org/) notebook server with additional [NodeJS](https://nodejs.org/en/) kernel. It also contains [plotly](https://plotly.com/) libary to print sophisticated charts. If you have certain code you want to use immediately in your jupyter notebook, there is a volume which mounts to `/home/jovyan/mount`.

## Build
You can build a docker image from this given Dockerfile: `docker build -t jupyter-nodejs-kernel:latest .`  
I'll recommend to give this image a label so it is easier to work with it.

## Run
For running this jupyter server, you'll need to create a container and run this: `docker run -p 8888:8888 jupyter-nodejs-kernel:latest`  

### Mount project folder
Optionaly you can mount a project folder of yours to access this immidiately with juypter by mounting a volume with `-v <path>:/home/jovyan/mount`.  
Your path must be specified absolutely. Windows users need to specified this with drive letter, e.g. `C:/...`. 

## Maintain
It is possible to connect with the container through docker execution command:
`docker exec -ti <container-id> bash`
