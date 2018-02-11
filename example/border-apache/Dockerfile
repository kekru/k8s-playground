FROM httpd:2.4
RUN apt-get update && apt-get install -y curl
RUN apt-get install -y wget
RUN mkdir /datainstall
RUN wget https://github.com/zmartzone/mod_auth_openidc/releases/download/v2.3.3/libapache2-mod-auth-openidc_2.3.3-1.jessie.1_amd64.deb -O /datainstall/mod-auth-openidc.deb
RUN ls -la /datainstall
RUN dpkg -i /datainstall/mod-auth-openidc.deb || true
RUN apt-get -fy install
RUN dpkg -i /datainstall/mod-auth-openidc.deb
# rm -rf /var/lib/apt/lists/*

#RUN mv /usr/lib/apache2/modules/* /usr/local/apache2/modules/

RUN wget https://raw.githubusercontent.com/kekru/linux-utils/master/cert-generate/create-certs.sh -O /datainstall/create-certs.sh
RUN chmod +x /datainstall/create-certs.sh \
 && /datainstall/create-certs.sh -m ca -pw yourSecretPassword -t /datainstall/certs -e 900 \
 && /datainstall/create-certs.sh -m server -h myserver.example.com -pw yourSecretPassword -t /datainstall/certs -e 365 

RUN ls -la /datainstall/certs
ADD httpd.conf /usr/local/apache2/conf/httpd.conf
