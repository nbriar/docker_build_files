FROM nbriar/rails:4.1.5



# throw errors if Gemfile has been modified since Gemfile.lock
RUN bundle config --global frozen 1
RUN apt-get install -y curl libcurl3 libcurl3-gnutls libcurl4-openssl-dev
RUN apt-get update && apt-get install -y postgresql postgresql-contrib postgresql-server-dev-9.1 mysql-server libmysqlclient-dev sqlite3 libsqlite3-dev --no-install-recommends && rm -rf /var/lib/apt/lists/*


RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app


ONBUILD COPY Gemfile /usr/src/app/
ONBUILD COPY Gemfile.lock /usr/src/app/
ONBUILD RUN bundle install

ONBUILD COPY . /usr/src/app

RUN curl -sL https://deb.nodesource.com/setup | bash -
	
RUN apt-get install -y nodejs --no-install-recommends 
RUN rm -rf /var/lib/apt/lists/*

CMD rake db:migrate
CMD rake assets:precompile


EXPOSE 3000
CMD ["unicorn", "-l", "3000"]
