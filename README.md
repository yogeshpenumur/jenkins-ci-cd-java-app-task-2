#   TASK 2: Create a Simple Jenkins Pipeline for CI/CD

##   Java Web App – CI/CD with Jenkins and Docker

This project is a simple Java-based web application built using Maven, containerized using Docker, and deployed automatically via a Jenkins CI/CD pipeline.

---

##   Automate Code Deployment Using CI/CD Pipeline (Jenkins)

###   What I Did – Step by Step

- **  Created a Java Project**: Built a Java web application (WAR or JAR) using Maven (`mvn clean package`).
- **  Dockerized the App**:
  - Used an OpenJDK or Tomcat base image.
  - Copied the packaged `.war` or `.jar` into the container.
  - Exposed necessary ports (e.g. `8080`).
  - Defined a default command such as `CMD ["java", "-jar", "app.war"]` or Tomcat startup.
- **  Created Jenkinsfile**:
  - Clone the GitHub repo.
  - Build the Java app using Maven within a Docker agent (`maven:3.8.1-adoptopenjdk-11`).
  - Build Docker image tagged as `yogeshpenumur/img:${BUILD_NUMBER}`.
  - Remove old container and run a new one on port `9990`.
  - Copy `webapps.dist` into Tomcat's `webapps` directory inside the container.
- ** Jenkins Configuration**:
  - Added Jenkinsfile to repository.
  - Configured a Jenkins job to trigger on pushes to `main` by using GitHub hook trigger for GITScm polling .
- ** Tested the Full Pipeline**:
  - Final push triggered full pipeline automatically, container deployed and accessible.

---

##  Dockerfile Template


##  Dockerfile Explanation

- `FROM tomcat:8`
  - Uses the official Tomcat 8 Docker image.
  - Comes with pre-installed Java and Tomcat server.

- `COPY target/*.war /usr/local/tomcat/webapps/myweb.war`
  - Copies the compiled `.war` file from the `target/` folder.
  - Renames and deploys it as `myweb.war` inside Tomcat's `webapps` directory.
  - Tomcat auto-deploys `.war` files from this location.



