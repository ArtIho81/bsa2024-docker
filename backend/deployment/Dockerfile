FROM node:20-alpine

# Add configuration here

WORKDIR /backend

COPY package*.json ./
RUN npm install

COPY src ./src
COPY tsconfig.json ./

RUN npm run build

EXPOSE 4001

CMD [ "npm", "run", "serve" ]