FROM node:alpine as builder
WORKDIR '/app'
# Gather dependencies
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx 
# Copy build from node to /usr/share/nginx/html as per Docker doc of nginx
COPY --from=builder /app/build /usr/share/nginx/html 