# VS code with Julia
This is docker container for developing with julia in browser (using code server cersion of VS code editor). This image is now supporting only `arm63` but I will make it more generic in the future. 


## Build 

Download the code from Github. Go to the project directory 

```{bash}
cd julia
```

and build the image:

```{bash}
docker build -t code-julia . 
```

### Custom Project / Manifest

You can build the image with your own Project.toml by changing the one inside `julia_config`. 

### Custom Julia Version 
You can build the docker with a specific julia version by running:
```{bash}
docker build --build-arg JULIA_VERSION=1.5.3 -t code-julia . 
```

## Usage

By default, `docker-julia` runs on port `3838`. 

```{bash}
docker run -d -p 3838:3838 --restart=unless-stopped code-julia
```

You can access the container by going to: [http://0.0.0.0:3838](http://0.0.0.0:3838)

Additional options such as setting the number of threads:

```{bash}
docker run -d -p 3838:3838 --env JULIA_NUM_THREADS=12 --restart=unless-stopped code-julia
```

You can also link to a specific folder:
```{bash}
 docker run -d -p 3838:3838 -v /path/to/folder:/root --env JULIA_NUM_THREADS=12 --restart=unless-stopped code-julia
 ```
