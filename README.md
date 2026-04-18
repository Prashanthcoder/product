# Product — Java Servlet Demo 🚀

> A hands-on project that demonstrates how a browser communicates with a **Tomcat server** using Java Servlets, including servlet lifecycle management and a multiplication utility built with servlets.

---

## 📖 About

This project provides valuable insights into the **HTTP request-response cycle** — how a browser sends a request to a server and how the server processes and responds to it.

Key concepts explored:

- How a browser sends HTTP requests to a web server
- How **Apache Tomcat** handles and routes incoming requests
- The **Servlet lifecycle** — how the container creates servlet objects and loads specific classes based on incoming requests
- A practical example: **multiplying two numbers** using a custom servlet

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Java | Core programming language |
| Java Servlets | Server-side request handling |
| Apache Tomcat | Web/application server |
| HTML | Frontend form for user input |
| HTTP | Client-server communication protocol |

---

## ⚙️ How It Works

1. The **browser (client)** sends an HTTP request to the Tomcat server.
2. Tomcat receives the request and identifies the appropriate **Servlet class** to handle it.
3. The servlet container **creates a servlet object** (if not already instantiated) following the servlet lifecycle:
   - `init()` — Servlet is initialized
   - `service()` — Request is processed
   - `destroy()` — Servlet is destroyed when no longer needed
4. The servlet performs the **multiplication of two numbers** provided via the request.
5. The server sends back an **HTTP response** with the result, which the browser displays.

---

## 🚀 Getting Started

### Prerequisites

- Java JDK 8 or above
- Apache Tomcat 9.x or above
- Any Java IDE (Eclipse / IntelliJ IDEA) or a text editor

### Setup & Run

1. **Clone the repository**
   ```bash
   git clone https://github.com/Prashanthcoder/product.git
   cd product
   ```

2. **Import the project** into your IDE as a Dynamic Web Project (Eclipse) or a Maven/Web project (IntelliJ).

3. **Deploy to Tomcat**
   - Add the project to your Tomcat server instance in the IDE, or
   - Build a `.war` file and drop it into Tomcat's `webapps/` directory.

4. **Start Tomcat** and navigate to:
   ```
   http://localhost:8080/product/
   ```

5. Enter two numbers and submit the form to see the multiplication result returned by the servlet.

---

## 📂 Project Structure

```
product/
├── src/
│   └── main/
│       └── java/
│           └── MultiplicationServlet.java   # Core servlet logic
├── WebContent/
│   ├── index.html                           # Frontend form
│   └── WEB-INF/
│       └── web.xml                          # Servlet mapping configuration
└── README.md
```

---

## 📚 Learning Outcomes

- Understand the **browser ↔ server** communication model
- Learn how Tomcat manages the **servlet lifecycle**
- See how servlet classes are **loaded and instantiated** on demand
- Build and test a simple **server-side computation** using servlets

---

## 🤝 Contributing

Contributions and suggestions are welcome! Feel free to open an issue or submit a pull request.

---

## 👤 Author

**Prashanth** — [GitHub @Prashanthcoder](https://github.com/Prashanthcoder)
