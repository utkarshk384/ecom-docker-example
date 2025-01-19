FROM node:19.4-bullseye-slim AS build
WORKDIR /app
COPY package*.json ./
COPY setupProxy.js ./
RUN --mount=type=cache,target=usr/src/app/.npm \
npm set cache /usr/src/app/.npm && \
npm ci --only=production
COPY . .
RUN npm run build
FROM nginxinc/nginx-unprivileged:1.23-alpine-perl
EXPOSE 3000 
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf