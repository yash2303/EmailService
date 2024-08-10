# Email Service

## Overview
The Email Service is a Spring Boot application designed to send emails based on events received from a Kafka topic. It uses JavaMail for email sending and integrates with Kafka for event consumption.

## Project Structure
- `src/main/java/com/yashasvi/emailservice/EmailServiceApplication.java`: Main class to run the Spring Boot application.
- `src/main/resources/application.properties`: Configuration file for the application.
- `src/main/java/com/yashasvi/emailservice/utils/EmailUtil.java`: Utility class for sending emails.
- `src/main/java/com/yashasvi/emailservice/consumers/SendEmailEventConsumer.java`: Kafka consumer that listens for email events and triggers email sending.
- `src/main/java/com/yashasvi/emailservice/dtos/SendEmailEventDto.java`: Data Transfer Object (DTO) for email events.

## Prerequisites
- Java 11 or higher
- Maven
- Kafka
- SMTP server credentials (e.g., Gmail)

## Configuration
Configure the application by setting the following properties in `src/main/resources/application.properties`:
```ini
server.port=8484
```

## Running the Application
1. Build the project using Maven:
    ```sh
    mvn clean install
    ```
2. Run the Spring Boot application:
    ```sh
    mvn spring-boot:run
    ```

## Kafka Configuration
Ensure Kafka is running and the topic `sendEmail` is created. The consumer listens to this topic for email events.

## Sending Emails
The `SendEmailEventConsumer` class listens to the `sendEmail` topic. When a message is received, it deserializes the message into a `SendEmailEventDto` object and sends an email using the `EmailUtil` class.

## Example Kafka Message
```json
{
  "to": "recipient@example.com",
  "subject": "Test Email",
  "body": "This is a test email."
}
```

## License
This project is licensed under the MIT License.
