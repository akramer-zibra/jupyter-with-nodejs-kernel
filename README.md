This project contains a Dockerfile to create a [jupyter](https://jupyter.org/) notebook server with additional [NodeJS](https://nodejs.org/en/) kernel. It also contains [plotly](https://plotly.com/) libary to print sophisticated charts. If you have certain code you want to use immediately in your jupyter notebook, there is a volume which mounts to `/home/jovyan/mount`.

## Build
You can build a docker image from this given Dockerfile: `docker build -t jupyter-nodejs-kernel:latest .`  
I'll recommend to give this image a label so it is easier to work with it.

## Run
For running this jupyter server, you'll need to create a container and run this: `docker run -p 8888:8888 jupyter-nodejs-kernel:latest`  

### Mount project folder
Optionaly you can mount a project folder of yours to access this immidiately with juypter by mounting a volume with `-v <path>:/home/jovyan/mount`.  
Your path must be specified absolutely. Windows users need to specified this with drive letter, e.g. `C:/...`. 

## Use
Simply create a "Javascript" Notebook if you want to use nodejs kernel withn a jupyter notebook. E.g.
```javascript
console.log('Hello scientist!');
```

### Create plotly charts
The integration of plotly with jupyter does `dstools` npm packge. Install this first, if you want to print plotly diagrams like this
```javascript
var ds = require('dstools');

var trace1 = {
  x: [1, 2, 3, 4],
  y: [10, 15, 13, 17],
  type: 'scatter'
};

var trace2 = {
  x: [1, 2, 3, 4],
  y: [16, 5, 11, 9],
  type: 'scatter'
};

var data = [trace1, trace2];
var layout = {};

ds.Collection().plotly(data, layout).show();
```

## Maintain
It is possible to connect with the container through docker execution command:
`docker exec -ti <container-id> bash`

### Install npm packages 
Connect via docker exec command and install npm packages within the working directory `/home/jovyan`, or use jupyter terminal connection to install npm packages with `npm install <package>` 