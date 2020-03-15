FROM python:3.7.1

RUN mkdir /app
WORKDIR /app

RUN apt-get update -y 
RUN apt-get install -y python-pip python-dev

# We copy just the requirements.txt first to leverage Docker cache
COPY ./requirements.txt /app/requirements.txt



RUN pip install -r requirements.txt

ADD . /app

EXPOSE 5000


CMD flask run --host=0.0.0.0