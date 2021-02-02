FROM    amazonlinux:2

RUN     yum update -y \
        && amazon-linux-extras install -y \
            nginx1 \
        && yum clean all \
        && rm -rf /var/chache/yum/*

COPY    ./etc/nginx.conf /etc/nginx/nginx.conf

EXPOSE  80

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
