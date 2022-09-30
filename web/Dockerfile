# Install dependencies only when needed
FROM node:14.16.1-buster as builder
# Installing dependencies
RUN mkdir -p /app
WORKDIR /app
COPY package*.json /app/
RUN npm install

# Copying source files
COPY . /app

# Building app
RUN npm run build

FROM node:14.16.1-buster as runner
ENV PORT 3000

# Create app directory
RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

COPY --from=builder /app/ /usr/src/app

EXPOSE 3000

# Running the app
CMD "npm" "run" "dev"