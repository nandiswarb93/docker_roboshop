#optimised image code
FROM node:20.19.5-alpine3.22 AS build 
WORKDIR /opt/server
COPY package.json .
COPY *.js .
# this may add extra cache memory
RUN npm install

FROM node:20.19.5-alpine3.22

#create a group and user
WORKDIR /opt/server
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop && \
    chown -R roboshop:roboshop /opt/server 
EXPOSE 8080
LABEL com.project="roboshop" \ 
    component="catalogue" \
    created_by="nandiswar"
ENV MONGO="true" \
    REDIS_URL="redis://redis:6379" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"

COPY --from=build /opt/server /opt/server
USER roboshop
CMD ["server.js"]
ENTRYPOINT ["node"]








# FROM node:20
# WORKDIR /opt/server
# EXPOSE 8080
# COPY package.json .
# COPY *.js .
# RUN npm install
# ENV MONGO="true" \
#     REDIS_URL="redis://redis:6379" \
#     MONGO_URL="mongodb://mongodb:27017/users"
# CMD ["node", "server.js"]
