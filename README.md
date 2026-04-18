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

## 🐛 Known Issues & Planned Fixes

### Issue — Response Not Rendered on the Same Page

**Status:** `🔧 Planned`

**Problem**

Currently, when a user sends a request from the client, the server response is either redirected to a different page or not displayed within the originating request page. This causes a disconnect in the user experience and breaks the natural flow of interaction.

**Root Cause**

The servlet uses a traditional `sendRedirect()` or `RequestDispatcher.forward()` approach, which navigates the browser away from the original page before rendering the server's response.

**Planned Solution**

- Replace the full-page form submission with an **AJAX / Fetch API** call so the response is received and rendered on the same page without a reload.
- The servlet will return the result as a **JSON response** instead of forwarding to a new JSP/HTML page.
- Display the result (and any server-side validation messages or errors) dynamically within the existing page using JavaScript DOM manipulation.

**Proposed Client-Side Change**

```javascript
document.getElementById("multiplyForm").addEventListener("submit", async (e) => {
  e.preventDefault(); // Prevent full-page reload

  const num1 = document.getElementById("num1").value;
  const num2 = document.getElementById("num2").value;

  const response = await fetch("/product/MultiplicationServlet", {
    method: "POST",
    headers: { "Content-Type": "application/x-www-form-urlencoded" },
    body: `num1=${num1}&num2=${num2}`
  });

  const data = await response.json();

  // Render result on the same page
  document.getElementById("result").innerText = `Result: ${data.result}`;
});
```

**Proposed Servlet-Side Change**

```java
@Override
protected void doPost(HttpServletRequest request, HttpServletResponse response)
    throws ServletException, IOException {

  int num1 = Integer.parseInt(request.getParameter("num1"));
  int num2 = Integer.parseInt(request.getParameter("num2"));
  int result = num1 * num2;

  // Return JSON instead of redirect/forward
  response.setContentType("application/json");
  response.setCharacterEncoding("UTF-8");
  response.getWriter().write("{\"result\": " + result + "}");
}
```

**Expected Outcome After Fix**

- The user submits two numbers on the form page.
- The result appears **on the same page** without any navigation or reload.
- Validation errors (e.g., non-numeric input) are also shown inline on the same page.

---

## 🤝 Contributing

Contributions and suggestions are welcome! Feel free to open an issue or submit a pull request.

---

## 👤 Author

**Prashanth** — [GitHub @Prashanthcoder](https://github.com/Prashanthcoder)1. 
Contributions and suggestions are welcome! Feel free to open an issue or submit a pull request.

---
