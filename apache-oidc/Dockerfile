FROM httpd:2.4-bullseye

## install openidc module
RUN apt-get update && apt-get install -y \
libapache2-mod-auth-openidc && rm -rf /var/lib/apt/lists/*
RUN ln -s /usr/lib/apache2/modules/mod_auth_openidc.so /usr/local/apache2/modules

RUN sed -i \
		-e 's/^#\(Include .*httpd-ssl.conf\)/\1/' \
		-e 's/^#\(LoadModule .*mod_ssl.so\)/\1/' \
		-e 's/^#\(LoadModule .*mod_socache_shmcb.so\)/\1/' \
		-e 's/^#\(LoadModule .*mod_rewrite.so\)/\1/' \
		conf/httpd.conf

## Append sso.conf at the end of httpd.conf
RUN echo "\n\n" >> /usr/local/apache2/conf/httpd.conf
COPY ./sso.conf /tmp/tmp.conf

COPY ./server.crt /usr/local/apache2/conf/server.crt
COPY ./server.key /usr/local/apache2/conf/server.key


RUN cat /tmp/tmp.conf >> /usr/local/apache2/conf/httpd.conf && rm -rf /tmp.conf
