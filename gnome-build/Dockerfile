# GNOME Development Environment
#
# VERSION     0.0.1

FROM          ubuntu:xenial
MAINTAINER    Ashhar Hasan <hashhar_lists@outlook.com>
LABEL         Description="This image provides a build environment that can build most of the GNOME products. You need to mount the directory containing the source code onto the container using '-v host_dir:container_dir'"

# Update the package repository and install some packages.
RUN           apt-get update \
              && apt-get upgrade -y \
              && apt-get install -y \
                 apt-file \
                 autoconf \
                 autopoint \
                 autotools-dev \
                 bash-completion \
                 build-essential \
                 curl \
                 docbook-xsl \
                 gettext \
                 git \
                 git-core \
                 libtext-csv-perl \
                 man-db \
                 pkgconf \
                 python \
                 python-dev \
                 python-pip \
                 vim \
                 wget


# Create a user for development.
RUN           useradd -m gnome

# Log in as the new user and set up for jhbuild.
USER          gnome
COPY          jhbuildrc setup_jhbuild.sh /home/gnome/
RUN           /bin/bash /home/gnome/setup_jhbuild.sh

SHELL         ["/bin/bash"]
ENV           SHELL=/bin/bash
