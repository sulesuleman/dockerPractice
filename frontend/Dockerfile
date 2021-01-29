### Stage 1: build ###

FROM node:12.20.1 as node

# Set working directory.
RUN mkdir /web

WORKDIR /web

# Copy app dependencies.
COPY package.json ./

# Install app dependencies.
RUN npm install

# Copy app files.
COPY . .

RUN npm run build --prod


FROM nginx:1.16.0-alpine as prod_stage

COPY --from=node /web/dist/frontend /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
