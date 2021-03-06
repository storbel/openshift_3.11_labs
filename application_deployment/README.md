## Application deployement 


```

```
### Create new application with Openshift

```

```

### Create new application from a GIT repository


```

```

#### Create new application with --context-dir

```

$ oc new-app https://github.com/sclorg/s2i-ruby-container.git \
    --context-dir=2.0/test/puma-test-app
    
```

#### Create new application from specific branch

```

$ oc new-app https://github.com/openshift/ruby-hello-world.git#beta4

```

#### Create new application by setting strategy 

```
$ oc new-app /home/user/code/myapp --strategy=docker

```


#### Create new application by setting Environment Variables 

```
$ oc new-app openshift/postgresql-92-centos7 \
    -e POSTGRESQL_USER=user \
    -e POSTGRESQL_DATABASE=db \
    -e POSTGRESQL_PASSWORD=password
```


#### To list all local templates and image streams, use:
```
  oc new-app -L
 ```
#### Search templates, image streams, and Docker images

To search templates, image streams, and Docker images that match the arguments provided, use:
```
  oc new-app -S php
  oc new-app -S --template=ruby
  oc new-app -S --image-stream=mysql
  oc new-app -S --docker-image=python
  ```
 
