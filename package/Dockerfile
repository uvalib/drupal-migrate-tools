#
#
#
FROM public.ecr.aws/docker/library/alpine:3.20

# Add necessary packages
RUN apk --update add bash tzdata mariadb-client postgresql-client ca-certificates aws-cli rsync && rm -fr /var/cache/apk/*

# allow docker passwordless sudo
#RUN echo "docker ALL=NOPASSWD: ALL" > /etc/sudoers.d/docker

# set the timezone appropriatly
ENV TZ=UTC
RUN cp /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Specify home 
ENV APP_HOME /drupal-migrate-tools
WORKDIR $APP_HOME

# Create necessary directories
RUN mkdir -p $APP_HOME/scripts

# Move in necessary assets
COPY package/scripts/*.ksh $APP_HOME/scripts/
COPY data/container_bash_profile /root/.profile

# Specify the user
#USER docker

#
# end of file
#
