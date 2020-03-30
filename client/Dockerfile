FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./default.conf ./etc/nginx/conf.d/default.conf
# copy stuff from previous step to html folder inside nginx container
COPY --from=builder /app/build /usr/share/nginx/html