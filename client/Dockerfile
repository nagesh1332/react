FROM node:alpine3.18 as build
WORKDIR /app
COPY package*.json .
COPY yarn*.lock .
RUN yarn install
COPY . .
RUN yarn build

#Stage 2
FROM nginx:1.19.0
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY /app/build .
EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]
