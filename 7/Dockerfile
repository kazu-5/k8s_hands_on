FROM ruby:2.6

WORKDIR /var/www/app
EXPOSE 3000
COPY ./app/Gemfile Gemfile
COPY ./app/Gemfile.lock Gemfile.lock
RUN gem install bundler
RUN bundle install

COPY ./app .
