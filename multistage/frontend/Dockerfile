#stage1
FROM node:21 AS frontend-builder

#set the working directory to /app
WORKDIR /app

#copy the package.json and package-lock.json for dependancy installation
COPY package*.json ./

#install dependancies
RUN npm install

#copy the rest of the application code
COPY . .

#stage2
FROM node:21-slim

#set the working directory to /app
WORKDIR /app

#copy the build assets and dependancies from front builder stage
COPY --from=frontend-builder /app .

#copy the .env.sample file to .env.local
COPY .env.sample .env.local

#expose port 5173 for the node.js application 
EXPOSE 5173

#define the default command to run the application in the development
CMD ["npm", "run", "dev","--","--host"]

