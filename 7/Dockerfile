FROM ruby:2.6

WORKDIR /var/www/app
EXPOSE 3000
COPY Gemfile Gemfile
ADD Gemfile.lock Gemfile.lock
RUN bundle install
