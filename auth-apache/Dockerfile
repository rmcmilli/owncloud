FROM httpd:latest
RUN apt-get update
RUN apt-get install -y libapache2-mod-auth-radius libapache2-mod-wsgi-py3
COPY ./my-httpd.conf /usr/local/apache2/conf/httpd.conf
#RUN a2enmod auth_radius
RUN mkdir -p /var/www/html/auth
RUN chown www-data.www-data /var/www/html/auth -R
COPY ./000-default.conf /etc/apache2/sites-enabled/
RUN mkdir /etc/apache2/mods-enabled
RUN ln -s /etc/apache2/mods-available/auth_radius.load /etc/apache2/mods-enabled/
RUN mv /usr/local/apache2/conf/extra/httpd-vhosts.conf /usr/local/apache2/conf/extra/httpd-vhosts.conf.bak
RUN ln -s /etc/apache2/sites-enabled/radius.conf /usr/local/apache2/conf/extra/httpd-vhosts.conf
RUN mkdir /var/log/apache2