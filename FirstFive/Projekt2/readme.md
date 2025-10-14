<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Flask Health Check API – Dockerized</title>
  <style>
    body {
      background-color: #0d1117;
      color: #e6edf3;
      font-family: "Segoe UI", Roboto, sans-serif;
      line-height: 1.6;
      margin: 40px;
    }
    h1, h2, h3 {
      color: #58a6ff;
    }
    code {
      background: #161b22;
      color: #ffcb6b;
      padding: 2px 5px;
      border-radius: 4px;
    }
    pre {
      background: #161b22;
      padding: 12px;
      border-radius: 8px;
      overflow-x: auto;
    }
    .section {
      margin-top: 40px;
      border-top: 1px solid #30363d;
      padding-top: 20px;
    }
  </style>
</head>
<body>

  <h1>🐍 Flask Health Check API – Dockerized</h1>
  <p>
    This project demonstrates how to create a <strong>simple Flask API</strong> and run it inside a <strong>Docker container</strong>.
    It was built as part of my DevOps learning journey to understand how containers, ports, and environment variables work together.
  </p>

  <div class="section">
    <h2>🚀 Project Overview</h2>
    <p>
      A minimal Flask application (<code>app.py</code>) provides one endpoint:
    </p>

    <pre><code>GET /health</code></pre>

    <p>It returns a JSON response indicating that the service is healthy:</p>

    <pre><code>{
  "status": "healthy"
}</code></pre>
  </div>

  <div class="section">
    <h2>🧠 What I Learned</h2>

    <h3>1️⃣ Flask Basics</h3>
    <ul>
      <li>Flask is a lightweight Python web framework.</li>
      <li><code>app = Flask(__name__)</code> initializes the Flask application.</li>
      <li><code>@app.route('/health', methods=['GET'])</code> defines a GET endpoint.</li>
      <li><code>jsonify()</code> converts Python data structures into valid JSON.</li>
      <li><code>if __name__ == '__main__':</code> ensures the app only runs when executed directly.</li>
    </ul>

    <h3>2️⃣ Docker Concepts</h3>
    <p>We created a <code>Dockerfile</code> to containerize the Flask app:</p>

    <pre><code>FROM python:3.10-slim
WORKDIR /app
COPY . .
RUN pip install --no-cache-dir Flask
EXPOSE 80
ENV PORT=80
ENV VERSION=latest
CMD ["python3", "app.py"]
</code></pre>

    <p><strong>Step-by-step explanation:</strong></p>
    <ul>
      <li><strong>FROM:</strong> Uses a lightweight Python base image.</li>
      <li><strong>WORKDIR:</strong> Sets <code>/app</code> as the working directory inside the container.</li>
      <li><strong>COPY:</strong> Copies all files (like <code>app.py</code>) into the container.</li>
      <li><strong>RUN:</strong> Installs Flask.</li>
      <li><strong>EXPOSE 80:</strong> Documents that the container listens on port 80.</li>
      <li><strong>ENV PORT=80:</strong> Sets an environment variable the app can read.</li>
      <li><strong>CMD:</strong> Defines the command to start the app when the container runs.</li>
    </ul>
  </div>

  <div class="section">
    <h3>3️⃣ Ports and Networking</h3>
    <p>When you run:</p>

    <pre><code>docker run -d -p 1000:80 project2</code></pre>

    <p>
      The container listens <strong>internally on port 80</strong>, and Docker maps
      <strong>port 1000 on your host → port 80 inside the container</strong>.
    </p>

    <p>Access the app at:</p>
    <pre><code>http://localhost:1000/health</code></pre>

    <p>✅ Example output:</p>
    <pre><code>{
  "status": "healthy"
}</code></pre>
  </div>

  <div class="section">
    <h3>4️⃣ EXPOSE vs ENV Explained</h3>
    <table border="1" cellspacing="0" cellpadding="8">
      <tr>
        <th>Keyword</th>
        <th>What It Does</th>
        <th>Real-World Analogy</th>
      </tr>
      <tr>
        <td><code>EXPOSE 80</code></td>
        <td>Documents which port the app listens on inside the container.</td>
        <td>Writing the office room number ("Room 80") on the door.</td>
      </tr>
      <tr>
        <td><code>ENV PORT=80</code></td>
        <td>Sets a variable the app can read (via <code>os.environ.get("PORT")</code>).</td>
        <td>Leaving a note inside the office saying “We’re using Room 80”.</td>
      </tr>
    </table>

    <p>
      💡 In short:<br>
      <strong>EXPOSE</strong> = for Docker documentation<br>
      <strong>ENV</strong> = for your application
    </p>
  </div>

  <div class="section">
    <h2>🧩 Run & Test</h2>

    <h3>Build the Image</h3>
    <pre><code>docker build -t project2 .</code></pre>

    <h3>Run the Container</h3>
    <pre><code>docker run --name project2 -d -p 1000:80 project2</code></pre>

    <h3>Test the Endpoint</h3>
    <pre><code>curl http://localhost:1000/health</code></pre>

    <p>✅ Expected Output:</p>
    <pre><code>{
  "status": "healthy"
}</code></pre>
  </div>

  <div class="section">
    <h2>📘 Summary</h2>
    <ul>
      <li>How to build and run a Flask app inside a Docker container.</li>
      <li>How API endpoints, ports, and environment variables interact.</li>
      <li>How Docker maps host ports to container ports (<code>-p 1000:80</code>).</li>
      <li>The purpose of <code>EXPOSE</code> and <code>ENV</code> in real-world Docker setups.</li>
    </ul>

    <p><strong>Author:</strong> Ilyas<br>
    <strong>Date:</strong> October 2025<br>
    <strong>Tech Stack:</strong> Python, Flask, Docker</p>
  </div>

</body>
</html>

