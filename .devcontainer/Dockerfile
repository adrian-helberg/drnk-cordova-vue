FROM node:lts-alpine
USER root
WORKDIR /app
COPY package*.json ./
COPY . .
# Update repositories
RUN apk update
# Install Nano
RUN apk add nano
# Install OpenJDK
RUN apk add openjdk8
# Set JAVA_HOME
ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk
ENV PATH="$JAVA_HOME/bin:${PATH}"
# Update npm, Install Apache Corova, Vue with CLI
RUN npm install --global --unsafe-perm npm cordova @vue/cli @vue/cli-service-global
EXPOSE 8080