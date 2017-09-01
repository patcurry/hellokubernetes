#FROM python:3.6
#RUN mkdir /app
#WORKDIR /app
#ADD requirements.txt /app/requirements.txt
#RUN pip install -r /app/requirements.txt
#COPY . /app
#EXPOSE 8080
#ENV NAME world
#RUN pwd
#RUN ls
#CMD python ./manage.py runserver 0.0.0.0:8080

FROM python:3.6

RUN apt-get -q update && apt-get install -y -q \
  sqlite3 --no-install-recommends \
  && apt-get clean && rm -rf /var/lib/apt/lists/*

ENV LANG C.UTF-8

RUN mkdir /app
WORKDIR /app

ADD requirements.txt /app/requirements.txt
RUN pip install -r /app/requirements.txt

ADD . /app

CMD gunicorn -b :8080 main.wsgi
