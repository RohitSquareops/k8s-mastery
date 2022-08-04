FROM node:alpine as builder
WORKDIR /sa-frontend
RUN npm install
RUN yarn build

FROM nginx:1.15-alpine
COPY --from=builder /sa-frontend/build /usr/share/nginx/html

