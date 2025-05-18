# OAuth2-Demo

This is a simple Spring Boot application demonstrating **OAuth2 login** using **Google** and **GitHub** as authentication providers.

After successful login, users are redirected to a simple API endpoint that returns a greeting message. The application uses **Spring Security** with session-based authentication (suitable for browser-based flows).

---

## 🔧 Technologies Used

- Java 21
- Spring Boot 3.x
- Spring Security 6
- OAuth2 Client
- Auth Provider - Google & Github
- Maven

---

## ✅ Features

- OAuth2 login with Google and GitHub
- Secured API endpoint (`GET /`)
- Logout endpoint (`POST /logout`)
- Configurable via `application.yml` or `application.properties`

---

## 🗂️ Project Structure

```

src/
├── main/
│   ├── java/com/oauth2demo/
│   │   ├── config/SecurityConfig.java       # Security configuration
│   │   └── controller/HomeController.java   # REST controller
│   └── resources/
│       └── application.properties           # App configuration

```

---

## 🔐 OAuth2 Configuration

In order to use Google or GitHub as an OAuth2 provider, you must:

### 1. Create OAuth apps:

- **Google**: [Google Developer Console](https://console.developers.google.com/)
- **GitHub**: [GitHub Developer Settings](https://github.com/settings/developers)

### 2. Add your credentials in `application.properties`:

```properties
spring.application.name=OAuth2-Demo

server.port=8080

spring.security.oauth2.client.registration.google.client-id=YOUR_GOOGLE_CLIENT_ID
spring.security.oauth2.client.registration.google.client-secret=YOUR_GOOGLE_CLIENT_SECRET

spring.security.oauth2.client.registration.github.client-id=YOUR_GITHUB_CLIENT_ID
spring.security.oauth2.client.registration.github.client-secret=YOUR_GITHUB_CLIENT_SECRET
```

> Make sure to set the **redirect URI** in your provider’s app settings as:
>
> ```
> http://localhost:8080/login/oauth2/code/google
> http://localhost:8080/login/oauth2/code/github
> ```

---

## 🚀 Running the Application

```bash
# Clone the repository
git clone https://github.com/Hariharan1893/Spring-Security-OAuth2-Demo.git
cd Spring-Security-OAuth2-Demo

# Run the application
./mvnw spring-boot:run
```

Then open your browser and visit:

```
http://localhost:8080/
```

You’ll be redirected to the OAuth2 login screen (Google or GitHub).

---

## 🔓 Logout

Send a `POST` request to the `/logout` endpoint to invalidate the session:

```bash
curl -X POST http://localhost:8080/logout
```

> Note: Logout only clears your session from this app, not from the provider (Google/GitHub).

---

## 📫 Contact

For questions or improvements, feel free to open an issue or submit a PR.

---

## 📝 License

This project is open source and available under the [MIT License](LICENSE).
