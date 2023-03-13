# build stage
FROM node:16.18-alpine as build
WORKDIR /app
COPY package.json /app/package.json
RUN npm install
COPY ./ /app/
RUN npm run build --prod

# production stage
FROM nginx:1.23-alpine
COPY --from=build /app/dist/app/ /usr/share/nginx/html
# COPY --from=build /app/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80