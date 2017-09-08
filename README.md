# nginx-unit-python-django
nginx unit playground for django app

# RUN


```
docker run  \
   -itd \
   --name unit-django \ 
   -p 8080:8080  \
   mrchoke/nginx-unit-django:1.11.4
```


*test*

```
docker exec  unit-django  \
   curl  http://localhost:8000 

```


  *output*


```json
{
	"listeners": {},
	"applications": {}
}
```

# CONFIG

```
docker exec  unit-django  \
   curl -XPUT http://localhost:8000 -d@/srv/app/config.json
```
*test*

```
docker exec  unit-django  \
   curl  http://localhost:8000 

```


  *output*


```json
{
     "listeners": {
         "*:8080": {
             "application": "django"
         }
     },
     "applications": {
        "django": {
		"type": "python",
     		"workers": 3,
    		"module": "wsgi",
     		"user": "root",
     		"group": "root",
     		"path": "/srv/app"
   	}
   }
}
```
# WEB

```
http://localhost:8080
```

*Django Admin*
```
username: admin
password: unit1234
```

# Docker Hub

 * Dockerfile  https://hub.docker.com/r/mrchoke/nginx-unit-django/
