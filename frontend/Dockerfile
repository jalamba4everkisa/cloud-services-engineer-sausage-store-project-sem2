FROM node:8 AS builder
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html && mkdir -p /usr/share/nginx/html
COPY --from=builder /app/dist/frontend/ /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]