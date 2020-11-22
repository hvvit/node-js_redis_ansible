FROM node:14.15.1
EXPOSE 5000
WORKDIR /usr/app
COPY ./package.json ./

RUN npm install

COPY ./ ./
CMD ["npm","start"]
