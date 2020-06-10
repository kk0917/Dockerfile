FROM centos:7

LABEL maintainer="KKKK"

WORKDIR /usr/local/lib/

SHELL ["/bin/bash", "-c"]

RUN : " *** nginx install ***" \
  && { \
        echo '[nginx-stable]'; \
        echo 'name=nginx stable repo'; \
        echo 'baseurl=http://nginx.org/packages/centos/$releasever/$basearch/'; \
        echo 'gpgcheck=1'; \
        echo 'enabled=1'; \
        echo 'gpgkey=https://nginx.org/keys/nginx_signing.key'; \
        echo 'gpgkey=https://nginx.org/keys/nginx_signing.key'; \
     } > /etc/yum.repos.d/nginx.repo \
  && yum -y update \
  && yum -y install nginx \
  && systemctl enable nginx \
  && nginx -v \
  && yum -y install https://repo.ius.io/ius-release-el7.rpm \
  && yum --enablerepo=ius search python36 \
  && yum --enablerepo=ius -y install python36 \
  && python3.6 -v

WORKDIR /usr/share/nginx/html

EXPOSE 80

CMD ["/sbin/init"]
