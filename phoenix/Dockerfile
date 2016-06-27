FROM erlang:18

MAINTAINER Claudia Farias <krawdyah@gmail.com>

# Elixir requires UTF-8
ENV LANG=C.UTF-8

# Install NodeJS and Elixir
ENV ELIXIR_VERSION 1.3.0
RUN apt-get update \
    && apt-get install -y build-essential unzip nodejs
RUN mkdir /opt/elixir \
    && cd /opt/elixir
RUN wget https://github.com/elixir-lang/elixir/releases/download/v$ELIXIR_VERSION/Precompiled.zip \
    && unzip Precompiled.zip && rm Precompiled.zip
RUN export PATH="$PATH:/opt/elixir/bin"

# Install Phoenix
ENV PHOENIX_VERSION 1.1.6
RUN mix local.hex --force
RUN mix archive.install --force https://github.com/phoenixframework/archives/raw/master/phoenix_new-$PHOENIX_VERSION.ez

WORKDIR /code
