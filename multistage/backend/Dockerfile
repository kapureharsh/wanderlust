#stage1
FROM node:21 AS backend-builder

#set up working directory
WORKDIR /app

#coping our code
COPY . .

#when we install "npm install" then it's dependancy are also installed
RUN npm i

#stage2
FROM node:21-slim

#set up working directory
WORKDIR /app

#copy the above stage as compressed
COPY --from=backend-builder /app .


COPY .env.sample .env

EXPOSE 5000

CMD ["npm", "start"]
