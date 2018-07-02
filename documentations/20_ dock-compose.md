## 一、docker部署tomcat与web

https://blog.csdn.net/HOMERUNIT/article/details/80850214

## 二、docker部署nginx

## 三、docker-compose.yml
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
