FROM node:lts-slim AS builder

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm ci --frozen-lockfile --ignore-scripts

COPY . .

RUN npm run build

FROM nginx:stable-alpine AS runner

COPY --from=builder /app/dist /usr/share/nginx/html
COPY --from=builder /app/.docker/nginx/nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]