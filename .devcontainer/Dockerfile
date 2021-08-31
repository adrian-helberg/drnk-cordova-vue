FROM node:lts-alpine
USER root
WORKDIR /app
COPY package*.json ./
COPY . .
# Install Nano
RUN apk add nano
# Install OpenJDK
RUN apk add openjdk8
# Set JAVA_HOME
ENV JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk
# Download and set up Android SDK
RUN mkdir /android-sdk
RUN wget https://dl.google.com/android/repository/sdk-tools-linux-4333796.zip && unzip *.zip -d /android-sdk && rm *.zip
ENV ANDROID_HOME="/android-sdk"
ENV PATH="$PATH:$ANDROID_HOME/tools/bin"
# Install Gradle
ENV GRADLE_VERSION 4.10
ENV GRADLE_HOME /usr/local/gradle-$GRADLE_VERSION
RUN apk upgrade --update && apk add curl
RUN cd /usr/local && \
    curl -L https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o gradle-${GRADLE_VERSION}-bin.zip && \
    unzip gradle-${GRADLE_VERSION}-bin.zip && \
    rm gradle-${GRADLE_VERSION}-bin.zip
# PATH
ENV PATH=$GRADLE_HOME/bin:$JAVA_HOME/bin:$PATH
# Update npm, Install Apache Corova, Vue with CLI
RUN npm install --global --unsafe-perm npm cordova @vue/cli @vue/cli-service-global
EXPOSE 8080