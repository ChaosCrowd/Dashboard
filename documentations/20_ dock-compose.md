## docker-compose.yml
```
nginx:
    image: nginx
    links:
        - tomcat
    ports:
        - "80:80"


tomcat:
  image: qiuxf/ordering
  container_name: tomcat
  ports:
    - 8080:8080

```
