FROM debian:buster-slim
RUN apt-get install nodejs npm
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]