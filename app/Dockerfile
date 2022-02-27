FROM        alpine as builder
RUN         apk add --update nodejs npm
WORKDIR     /app
COPY        . .
RUN         npm ci
RUN         npm run build

FROM        nginx
COPY        --from=app-builder /app/build /usr/share/nginx/html
COPY        ./nginx/default.conf /etc/nginx/conf.d/default.conf
EXPOSE      3000