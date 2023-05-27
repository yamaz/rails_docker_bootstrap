#FROM golang:1.20 AS builder
#RUN go install github.com/cloudspannerecosystem/spanner-cli@latest


FROM ruby:3.2.1
RUN apt update -qq && apt install -y  \
 mlocate  telnet less emacs software-properties-common nodejs npm python3-pip && npm install -g yarn  \
&& yarn add @client-side-validations/simple-form && mkdir /myapp && pip3 install fire bcrypt argon2-cffi pycryptodome

RUN gem install bundler rails && gem update bunlder
RUN touch  /myapp/Gemfile /myapp/Gemfile.lock

COPY ./ /myapp
COPY entrypoint_for_rails.sh /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

RUN chmod +x /usr/bin/entrypoint.sh
WORKDIR /myapp
RUN bundle install
            

#CMD ["rails", "server", "-b", "0.0.0.0"]
CMD ["tail", "-f", "/dev/null"]
