FROM ruby:2.5.6
RUN apt-get update -qq && \
    apt-get install -y build-essential \
                       libpq-dev \
                       nodejs

RUN mkdir /base
ENV APP_ROOT /base
WORKDIR $APP_ROOT

ADD Gemfile $APP_ROOT/Gemfile
ADD Gemfile.lock $APP_ROOT/Gemfile.lock
ADD . $APP_ROOT
RUN bundle config --local build.mysql2 "--with-ldflags=-L/usr/local/opt/openssl/lib --with-cppflags=-I/usr/local/opt/openssl/include"
RUN gem install bundler -v 2.0.2

RUN bundle _2.0.2_ install
#ADD . $APP_ROOT
