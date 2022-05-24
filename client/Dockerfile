FROM node:alpine as builder
WORKDIR "/app"
COPY ./package.json ./
RUN nmp install
COPY . .
# Build the app which will create a 'build' directory with files in '/app' directory
RUN npm builder


FROM nginx
# Copy/overwrite the default.conf file to nginx server directory
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# Copy '/app/build' directory created on above instance of container to Nginx server file directory.
COPY --from=builder /app/build /usr/share/nginx/html

