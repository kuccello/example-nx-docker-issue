FROM node:lts-alpine3.14

WORKDIR /app
ENV PORT=5956
ENV PKG_CONFIG_PATH=/dlib-install/usr/local/lib64/pkgconfig/

COPY ./dist/apps/hackathon-api .

RUN apk update && \
    apk add \
    alpine-sdk \
  && apk add --no-cache python3 py3-pip \
  && apk add --update nodejs npm

RUN npm install --production

EXPOSE ${PORT}

CMD ["node", "./main.js"]