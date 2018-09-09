FROM node:alpine AS build
WORKDIR /usr/src/app

ENV \
	FLOOD_GIT_URI=https://github.com/jfurrow/flood.git \
	GLIBC_VERSION=2.28-r0

RUN \
	apk add -U --no-cache git python make gcc wget libc-dev g++ mediainfo && \
	mkdir -p /usr/src/app && \
	git clone $FLOOD_GIT_URI /usr/src/app

COPY include/config.js /usr/src/app/config.js

RUN \
	npm install && \
	npm cache clean --force && \
	npm run build

FROM node:alpine
WORKDIR /usr/src/app

RUN apk add -U --no-cache mediainfo
COPY --from=build /usr/src/app /usr/src/app

CMD [ "npm", "run", "start:production" ]