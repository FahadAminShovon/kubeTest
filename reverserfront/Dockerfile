 
FROM node:11.10.0-alpine AS build-stage

RUN apk add --update --no-cache \
    python \
    make \
    g++

COPY . /src
WORKDIR /src
COPY ./package* ./
RUN npm install
RUN yarn build

FROM nginx:latest
RUN rm -rf /usr/share/nginx/html
RUN mkdir /usr/share/nginx/html
COPY --from=build-stage /src/build/ /usr/share/nginx/html/
COPY default.conf /etc/nginx/conf.d/
# COPY brilliant.com.bd.crt /usr/share/nginx/
# COPY brilliant.com.bd.key /usr/share/nginx/
EXPOSE 80