FROM python:3.6-slim
MAINTAINER Femi Oladele<profemzy@gmail.com>

RUN apt-get install update && apt-get install --qq -y build-essential libpq-dev postgresql-client-9.6 --fix-missing --no-install-recommends

ENV INSTALL_PATH /mobydock
RUN mkdir -p $INSTALL_PATH

WORKDIR $INSTALL_PATH

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

COPY . .

VOLUME ["static"]

CMD gunicorn -b 0.0.0.0:8000 "mobydock.app:create_app()"
