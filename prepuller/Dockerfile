FROM centos:7
USER root
RUN  yum install -y cronie epel-release
RUN  yum install -y python34
RUN  yum -y update
COPY get_builds.py /usr/bin/get_builds
COPY node_update /usr/bin/node_update
COPY imagepuller /etc/cron.hourly/local01-imagepuller
COPY imagepurger /etc/cron.daily/local01-imagepurger
RUN  chmod 0755 /usr/bin/get_builds /usr/bin/node_update \
      /etc/cron.hourly/local01-imagepuller /etc/cron.daily/local01-imagepurger
CMD [ "/usr/sbin/crond", "-n", "-x",  "sch,proc" ]
LABEL      description="jupyterlab demo: imageprepuller" \
             name="lsstsqre/prepuller" \
             version="0.0.4"
