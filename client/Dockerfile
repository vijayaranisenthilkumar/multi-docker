#specify a base image

FROM node:alpine as builder

# install some dependencies
WORKDIR '/app'

COPY ./package*.json ./
RUN npm install

COPY . .

RUN  npm run build

FROM  nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html