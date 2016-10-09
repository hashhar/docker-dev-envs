
# Mozilla Development Environment
#
# VERSION     0.0.1

FROM          ubuntu:xenial
MAINTAINER    Ashhar Hasan <hashhar_lists@outlook.com>
LABEL         Description="This image provides a build environment that can build most of the Mozilla products, mainly Firefox and the SeaMonkey suite. You need to mount the directory containing the source code onto the container using '-v host_dir:container_dir'"

# Update the package repository and install some packages.
RUN           apt-get update \
              && apt-get upgrade -y \
              && apt-get install -y \
                 bash-completion \
                 curl \
                 git \
                 man-db \
                 python \
                 python-dev \
                 python-pip \
                 tmux \
                 vim \
                 wget

RUN           wget -O bootstrap.py https://hg.mozilla.org/mozilla-central/raw-file/default/python/mozboot/bin/bootstrap.py \
              && python bootstrap.py --application-choice browser --no-interactive \
              && rm bootstrap.py

# Create a user for development.
RUN           useradd -m firefox

# Log in as the new user and let them build a better web.
USER          firefox
SHELL         ["/bin/bash"]
ENV           SHELL=/bin/bash
