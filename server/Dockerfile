#1st stage
FROM node:20-alpine AS dependency

# set working directory
WORKDIR /app

# copy package file to install dependency
COPY package*.json .

RUN npm install --production

# 2nd stage
FROM node:20-alpine AS runner

# set working dir for 2nd stage
WORKDIR /app

# copy required files from 1st stage
COPY --from=dependency /app/node_modules ./node_modules

# copy code
COPY . .

# expose 3000 port
EXPOSE 3000

CMD ["node", "server.js"]