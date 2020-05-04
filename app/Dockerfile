FROM phusion/passenger-nodejs:1.0.8

LABEL maintainer="Joseph Min <phoenixter96@gmail.com>"

ENV HOME /root
WORKDIR /home/app/app

# Install yarn
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update && apt-get install yarn

# Copy files and install dependencies
COPY --chown=app:app . .
RUN yarn install

# Code quality.
RUN yarn global add prettier@2.0.2 eslint@6.8.0

COPY webapp.conf /etc/nginx/sites-enabled/webapp.conf

CMD ["make", "deploy"]
