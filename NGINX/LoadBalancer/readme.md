 ## Create image
```bash
docker build -t nginx-loadbalancer -f lb/Dockerfile lb
docker build -t nginx-backend1 -f backend1/Dockerfile backend1
docker build -t nginx-backend2 -f backend2/Dockerfile backend2
```
 ## Execute 
 ```bash
docker run -d --name backend1 nginx-backend1
docker run -d --name backend2 nginx-backend2
docker run -d -p 80:80 --name loadbalancer --link backend1 --link backend2 nginx-loadbalancer
 ```
