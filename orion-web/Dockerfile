FROM node:8.9.3-alpine
MAINTAINER Kevin Lin <developer@kevinlin.info>

ARG sha
ARG mapbox_api_token
ARG orion_server_url=/api

RUN apk update
RUN apk add curl unzip

RUN curl -L -o orion-web.zip https://github.com/acupajoe/orion-web/archive/$sha.zip
RUN unzip orion-web.zip
WORKDIR "orion-web-$sha"

RUN npm install
RUN npm install -g node-static

ENV NODE_ENV production
ENV MAPBOX_API_TOKEN $mapbox_api_token
ENV ORION_SERVER_URL $orion_server_url

RUN npm run build

EXPOSE 3001

CMD ["static", "dist", "-a", "0.0.0.0", "-p", "3001"]
