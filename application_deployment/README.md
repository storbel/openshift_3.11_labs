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

 