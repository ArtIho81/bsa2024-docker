FROM node:20-alpine as build

# Add configuration here

WORKDIR /frontend

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

FROM nginx:1.22.1

# Add configuration here

COPY --from=build /frontend/build /usr/share/nginx/html

RUN echo 'server { \
    listen 80; \
    server_name _; \
    root /usr/share/nginx/html; \
    location / { \
        try_files $uri /index.html; \
    } \
}' > /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]