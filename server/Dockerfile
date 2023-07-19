FROM node:20.4-alpine3.17 as development

WORKDIR /app

COPY ./package*.json ./

COPY ./ .

RUN npm install

ENV port 3005

EXPOSE 3005

CMD [ "npm", "start"]

