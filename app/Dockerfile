FROM debian:buster-slim
RUN apt-get install node npm
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
CMD ["npm", "start"]