FROM maven:3.8.6-jdk-8 AS builder
WORKDIR /sa-webapp
<<<<<<< HEAD
COPY pom.xml .
RUN mvn  install
=======
RUN mvn install 
>>>>>>> 7e5b937990ab1dbfb185fdd1ed3896f9b9ef6dff

ENV SA_LOGIC_API_URL http://54.213.236.147:5000

FROM openjdk:8-jre-alpine
COPY --from=builder /sa-webapp/target/sentiment-analysis-web-0.0.1-SNAPSHOT.jar ./
EXPOSE 8080
CMD ["java", "-jar", "sentiment-analysis-web-0.0.1-SNAPSHOT.jar", "--sa.logic.api.url=${SA_LOGIC_API_URL}"]

