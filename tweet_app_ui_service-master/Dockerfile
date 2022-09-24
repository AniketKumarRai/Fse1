# stage 1
FROM node:14.17.0 as node
# ENV REACT_APP_GATEWAY_HOST=REACT_APP_GATEWAY_HOST_VALUE
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build

# stage 2
FROM nginx:1.23.1
COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=node /app/dist/tweetapp-angular /usr/share/nginx/html


# COPY --from=build  /app/build /usr/share/nginx/html