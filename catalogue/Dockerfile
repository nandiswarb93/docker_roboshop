# #optimised image code
# FROM node:20.19.5-alpine3.22 AS build 
# WORKDIR /opt/server
# COPY package.json .
# COPY *.js .
# # this may add extra cache memory
# RUN npm install

# FROM node:20.19.5-alpine3.22

# #create a group and user

# RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
# WORKDIR /opt/server
# COPY --from=build /opt/server /opt/server
# ENV MONGO="true" \
#     MONGO_URL="mongodb://mongodb:27017/catalogue"
# RUN chown -R roboshop:roboshop /opt/server
# USER roboshop
# CMD ["node", "server.js"]



# # normal image high image size
# # FROM node:20
# # WORKDIR /opt/server
# # COPY package.json .
# # COPY *.js .
# # RUN npm install
# # ENV MONGO="true" \
# #     MONGO_URL="mongodb://mongodb:27017/catalogue"
# # CMD ["node", "server.js"]

# ---------- Stage 1: Build ----------
FROM node:20.19.5-alpine3.22 AS build

WORKDIR /app

# Copy package files only (cache optimization)
COPY package.json package-lock.json* ./

# Install only production deps (smaller!)
RUN npm ci --only=production

# Copy application code
COPY *.js . 


# ---------- Stage 2: Runtime ----------
FROM node:20.19.5-alpine3.22

# Create user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop

WORKDIR /app

# Copy ONLY needed files (node_modules + js files)
COPY --from=build /app /app

# Set permissions (as root)
RUN chown -R roboshop:roboshop /app

# Switch to non-root
USER roboshop

ENV MONGO="true" \
    MONGO_URL="mongodb://mongodb:27017/catalogue"

CMD ["node", "server.js"]

