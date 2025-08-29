Bajaj Finserv Health - Java Hiring Task Submission
This repository contains my solution for the Bajaj Finserv Health Qualifier 1 hiring task for the Java role.

*Project Overview
The project is a standalone Spring Boot application built to solve the hiring challenge. It is designed to be run from the command line and performs the required two-step API process upon startup:

Initial Request: It first sends a POST request with my candidate details (name, regNo, email) to the specified endpoint to receive a unique webhook URL and access token.

Solution Submission: Using the webhookUrl and accessToken from the initial response, it then sends a second POST request containing my final SQL query solution.

The application is self-contained and executes the entire process without needing manual triggers or API endpoints. The core logic is implemented directly within the main application class using CommandLineRunner.

⚙ How It Works
The application's entry point is the BfhQualifierJavaMainApplication class, which implements CommandLineRunner. This allows the code to execute as soon as the application is run.

The process is as follows:

The application is launched from the command line.

The run method within the main class is triggered.

It first calls the generateWebhook method, which sends a POST request to https://bfhldevapigw.healthrx.co.in/hiring/generateWebhook/JAVA with the candidate's credentials.

The server responds with a JSON object containing a unique webhookUrl and a JWT accessToken.

The application then immediately calls the submitFinalQuery method.

This method sets the Authorization header with the received accessToken and sends the final SQL query in the request body to the webhookUrl.

The application logs the outcome of both steps to the console and then terminates.

Data Transfer Objects (DTOs) are implemented using modern Java record types for conciseness and immutability.

🔧 Configuration
All personal details and the final SQL query are hardcoded within the BfhQualifierJavaMainApplication.java file.

Candidate Details:

UserCredentials credentials = new UserCredentials("Pushpam Raj", "22bce8110", "pushpamraj0123@gmail.com");

SQL Query Solution:
This project contains the solution for Question 2 (Even Number), as assigned by my registration number.

String sqlQuery = "SELECT d.doctor_id, d.doctor_name, d.specialization FROM doctors d GROUP BY d.doctor_id, d.doctor_name, d.specialization HAVING COUNT(DISTINCT d.hospital_id) > 1;";

*How to Run
You can build and run the project using the included Maven wrapper.

Clone the repository:

git clone https://github.com/Pushpam0123/bfh-qualifier-java-main.git
cd bfh-qualifier-java-main

Build the project:
This command will compile the code and package it into an executable JAR file in the target/ directory.

# For Windows
./mvnw.cmd clean package

# For macOS/Linux
./mvnw clean package

Run the application:
Execute the generated JAR file from your terminal. The entire task will run, and you can monitor the progress in the console.

java -jar target/bfh-qualifier-java-main-0.0.1-SNAPSHOT.jar

You will see detailed logs in the console outlining the success or failure of each API call.
