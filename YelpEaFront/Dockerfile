FROM node:22-alpine AS builder
WORKDIR /app
COPY . .
RUN npm ci
RUN npm run build -- --output-path=dist-app --configuration production

FROM nginx:alpine
COPY --from=builder /app/dist-app /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]