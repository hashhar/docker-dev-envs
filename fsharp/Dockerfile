# FSharp Development Environment
#
# VERSION     0.0.1

FROM          ubuntu:xenial
MAINTAINER    Ashhar Hasan <hashhar_lists@outlook.com>
LABEL         Description="This image provides a local dev environment for fsharp."

# Update the package repository and install some packages.
RUN           apt-get update \
              && apt-get upgrade -y \
              && apt-get install -y \
                 bash-completion \
                 curl \
                 git \
                 man-db \
                 tmux \
                 vim \
                 wget

# Install FSharp
RUN           apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF \
              && echo "deb http://download.mono-project.com/repo/debian wheezy main" > /etc/apt/sources.list.d/mono-xamarin.list \
              && apt-get update \
              && apt-get install -y fsharp mono-complete

# Install VSCode
RUN           curl -L -o /tmp/visual-studio-code.deb https://go.microsoft.com/fwlink/?LinkID=760868
RUN           apt-get install -y libnotify-bin libnss3 libgconf-2-4 libasound2 \
              && dpkg -i /tmp/visual-studio-code.deb

# Create a user for development.
RUN           useradd -m fsharp

# Log in as the new user.
USER          fsharp
SHELL         ["/bin/bash"]
ENV           SHELL=/bin/bash
ENV           HOME=/home/fsharp
ENV           DISPLAY=:0
