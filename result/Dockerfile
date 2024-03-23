FROM node:20.11.0 AS builder

WORKDIR /app

COPY package*.json .

RUN npm i

COPY  . .

RUN npm run build

FROM node:lts-slim

WORKDIR /result

COPY --from=builder /app/dist/ /app/package*.json ./

COPY --from=builder /app/views /result/views

RUN npm i --only=production

EXPOSE 4000

CMD [ "node","./server.js" ]

