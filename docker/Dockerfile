FROM node:12.16.2-alpine as build

WORKDIR /app

COPY . .

RUN yarn

ENV HOST 0.0.0.0

RUN yarn build

FROM node:12.16.2-alpine

WORKDIR /app

COPY . .

RUN yarn install --production=true

ENV HOST 0.0.0.0

COPY --from=build /app/.nuxt .nuxt

CMD ["yarn", "start"]