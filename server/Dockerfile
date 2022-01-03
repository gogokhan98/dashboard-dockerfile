FROM node:latest AS builder
WORKDIR /server
COPY ./package.json .
COPY ./tsconfig.json .
COPY ./src ./src
RUN npm install
RUN npm run build

FROM node:latest
WORKDIR /server
COPY package.json .
RUN npm install --only=production
COPY --from=builder /server/build ./build
EXPOSE 8080
CMD ["npm", "start"]