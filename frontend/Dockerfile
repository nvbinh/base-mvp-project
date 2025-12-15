# Stage 0, "build-stage", based on Node.js, to build and compile the frontend
FROM node:24 AS build
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY ./ ./
ARG NEXT_PUBLIC_API_URL
ENV NEXT_PUBLIC_API_URL=${NEXT_PUBLIC_API_URL}

RUN npm run build

FROM node:24 AS runner
WORKDIR /app
ENV NODE_ENV=production PORT=3000

COPY --from=build /app/package*.json ./
COPY --from=build /app/node_modules ./node_modules
COPY --from=build /app/.next ./.next
COPY --from=build /app/public ./public

EXPOSE 3000
CMD ["npm", "run", "start"]

# Stage 1, based on Nginx, to have only the compiled app, ready for production with Nginx
# FROM nginx:1

# COPY --from=build-stage /app/out/ /usr/share/nginx/html

# COPY ./nginx.conf /etc/nginx/conf.d/default.conf
# COPY ./nginx-backend-not-found.conf /etc/nginx/extra-conf.d/backend-not-found.conf
