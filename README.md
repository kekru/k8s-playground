# k8s-playground
personal experiments with kubernetes

## links
whoami over generic-exposer over borderproxy (not in k8s yet)  
https://whoami-pr987-default.app.192.168.0.19.nip.io/protected/protectedpage  

whoami over generic-exposer over traefik  
http://whoami-pr987-default.app.192.168.0.19.nip.io:30001/  
Port 30002 is traefik dashboard  

## borderproxy
```bash
docker build -t apache2 ./border-apache/
docker run --rm -i --net=host apache2 #with -t apache will not start
```

## keycloak
```bash
docker run -d --name keycloak -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin -p 9876:8080 jboss/keycloak
```
Enable Github Connection under Identity Providers.  
http://abc.127.0.0.1.nip.io:9876/auth/admin/master/console/#/realms/master/clients/  
Github Applications: https://github.com/settings/applications/   

Create Client:  
Validated Redirect URI: https://whoami-pr987-default.app.192.168.0.19.nip.io/protected/  
Base URL = Validated Redirect URI?  
Client Protocol: openid connect  
Access Type: Confidential  

Copy `Credentials -> Secret` in Border Apache's `OIDCClientSecret` field (httpd.conf)  

## More links
+ codecentric keycloak and mod auth openidc  
  https://blog.codecentric.de/2016/08/single-sign-mit-keycloak-als-openid-connect-provider/  
+ mod auth openidc keycloak  
  https://github.com/zmartzone/mod_auth_openidc/wiki/OAuth-2.0-Resource-Server  
+ Keycloak shell config  
  http://blog.keycloak.org/2016/10/registering-new-clients-from-shell.html 
+ jwt viewer  
  https://jwt.io/  
