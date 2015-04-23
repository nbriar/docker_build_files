FROM debian:wheezy

# File Author / Maintainer
MAINTAINER Nathan / Hang

# Update the repository sources list
RUN apt-get update && apt-get install -y \
  git \
  wget \
  procps \
  build-essential \
  zlib1g-dev \
  libssl-dev \
  libreadline6-dev

#install ruby
WORKDIR /tmp
RUN wget http://ftp.ruby-lang.org/pub/ruby/2.1/ruby-2.1.2.tar.gz
RUN tar -xvzf ruby-2.1.2.tar.gz
WORKDIR /tmp/ruby-2.1.2/


RUN /tmp/ruby-2.1.2/configure --prefix=/usr/local
RUN make && make install


