# 1st stage
FROM node:20-alpine AS build

# asigning working directory
WORKDIR /app

#install required build tools
RUN apk add --no-cache python3 make g++

# copy package.json to install dependency
COPY package*.json .
RUN npm install

# copy all code
COPY . .

# build the code
RUN npm run build

# 2nd stage
FROM nginx:stable-alpine AS runner

COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
