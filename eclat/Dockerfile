FROM node:12-alpine
WORKDIR /app
COPY package*.json .
RUN npm install
COPY index.js index.js
CMD ["npm", "start"]