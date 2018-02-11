FROM nginx:alpine
ADD nginx.conf /etc/nginx/nginx.conf
ADD run.sh /data/run.sh
RUN chmod +x /data/run.sh

ENV BASE_URL=app.127.0.0.1.nip.io \
    DNS_RESOLVER=kube-dns.kube-system.svc.cluster.local

#RUN /data/run.sh || true
#RUN cat /etc/nginx/nginx.conf
#CMD ["nginx-debug", "-g", "daemon off;"]
#CMD ["nginx", "-g", "daemon off;"]
CMD /data/run.sh