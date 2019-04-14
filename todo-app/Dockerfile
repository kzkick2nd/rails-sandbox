# WORKDIR = /usr/src/app
FROM ruby:2.6

# throw errors if Gemfile has been modified since Gemfile.lock
RUN bundle config --global frozen 1

RUN apt-get update -qq && apt-get install -y memcached libsasl2-dev

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY Gemfile /usr/src/app/
COPY Gemfile.lock /usr/src/app/
RUN bundle install

COPY . /usr/src/app

RUN bundle config --delete frozen \
 && apt-get update -qq && apt-get install -y build-essential nodejs \
 && rm -rf /var/lib/apt/lists/*
