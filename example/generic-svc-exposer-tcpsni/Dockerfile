FROM nginx:1.15-alpine
ADD nginx.conf /etc/nginx/nginx.conf
ADD run.sh /data/run.sh
RUN chmod +x /data/run.sh

ENV BASE_URL=app.192.168.0.150.nip.io \
    DNS_RESOLVER=kube-dns.kube-system.svc.cluster.local

ADD certs /certs

#RUN /data/run.sh || true
#RUN cat /etc/nginx/nginx.conf
#CMD ["nginx-debug", "-g", "daemon off;"]
#CMD ["nginx", "-g", "daemon off;"]
CMD /data/run.sh