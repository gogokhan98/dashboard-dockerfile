FROM node:latest AS builder
WORKDIR /client
COPY ./package.json .
COPY ./tsconfig.json .
COPY ./src ./src
COPY ./public ./public
RUN npm install
RUN npm run build

FROM node:latest AS production
WORKDIR /production
COPY ./package.json .
RUN npm install --only=production
COPY --from=builder /client/build ./build
EXPOSE 8080
CMD ["npm", "start"]