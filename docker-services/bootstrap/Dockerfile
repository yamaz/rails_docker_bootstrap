FROM ruby:3.2.1

RUN apt update -qq && apt install -y  \
telnet less emacs
RUN mkdir /myapp
RUN gem install bundler rails
RUN gem update bunlder
RUN touch  /myapp/Gemfile /myapp/Gemfile.lock
WORKDIR /myapp
COPY . /myapp
RUN bundle install

# To avoid container exit
COPY entrypoint_for_loop.sh /usr/bin/entrypoint.sh
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]


EXPOSE 3000

