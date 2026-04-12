# Ruby Sinatra Example Application

## Overview

A lightweight, production-ready Ruby web application built with Sinatra.

This project demonstrates:
- A simple HTTP service
- Containerization using Docker
- Deployment using NIFE

It is suitable for:
- Learning Sinatra fundamentals
- Understanding containerized deployments
- Practicing cloud deployment workflows

---

## Application Flow

```text
1. HTTP Request (GET /)
2. Handled by Sinatra route
3. Read NAME from environment
4. Generate greeting
5. Return response
```

---

## Endpoint

```text
GET / → Returns greeting message
```

---

## Requirements

Make sure you have the following installed:

- Ruby (3.0+)
- RubyGems
- Bundler
- Git

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/nifetency/ruby-example.git
cd ruby-example
```

---

### 2. Install Dependencies

```bash
gem install sinatra rackup puma
```

Or using Gemfile:

```bash
bundle install
```

---

### 3. Run the Application

```bash
ruby server.rb
```

---

### 4. Open in Browser

Visit:

```
http://localhost:8080
```

Expected output:

```
Bonjour world!
```

---

## Customization

Set a custom name using environment variables:

```bash
# macOS/Linux
NAME=David ruby server.rb

# Windows PowerShell
$env:NAME="David"; ruby server.rb
```

Output:

```
Bonjour David!
```

---

## Run with Docker (Optional)

```bash
docker build -t ruby-example-app .
docker run -p 8080:8080 -e NAME=Alice ruby-example-app
```

---

## Deployment on NIFE

Deploy your application using the NIFE platform:

https://launch.nife.io/

Deployment flow:

```text
Source → Build → Resources → Review → Deploy
```

Prerequisite: Ensure a workload (Deployment, CronJob, or StatefulSet) exists.

---

## Method 1: Deploy via Docker Image (Recommended)

### Step 1: Build and Push Image

```bash
docker build -t ruby-example-app .
docker tag ruby-example-app <username>/ruby-example-app:latest
docker push <username>/ruby-example-app:latest
```

---

### Step 2: Configure Source

- Source: Docker Image
- Registry: Docker Hub
- Image: `<username>/ruby-example-app:latest`
- Tag: `latest`

---

### Step 3: Build Configuration

- Internal Port: `8080`
- External Port: `80`

Optional environment variables:

| Key      | Value      |
|----------|------------|
| NAME     | Ruby       |
| RACK_ENV | production |

---

### Step 4: Resources Configuration

- Region: e.g., `ap-south-1`
- Resource Type: CPU

Recommended settings:

- CPU Request: `250m`
- Memory Request: `512MB`
- CPU Limit: `500m`
- Memory Limit: `1GB`

---

### Step 5: Deploy

- Strategy: Rolling
- Workload: Deployment
- Routing Policy: Latency
- Replicas: 1–2

Click **Deploy**.

---

## Method 2: Deploy via Git Repository

### Step 1: Select Source

- Source: Git Repository
- Provider: GitHub
- Branch: `main`

---

### Step 2: Build Configuration

- Internal Port: `8080`
- External Port: `80`

Enable:

```
Auto-Dockerize with Runtime
```

---

### Step 3: Build and Security

NIFE automatically performs:

- SAST
- SCA
- Container scan
- IaC scan

Resolve any critical issues before proceeding.

---

### Step 4: Resources and Deploy

Use the recommended configuration above and deploy.

---

## Deployment using nifectl (CLI)

You can deploy the application using the nifectl CLI.

---

### Step 1: Download nifectl

https://docs.nife.io/Quick-Start/Nifectl

---

### Step 2: Open Terminal

- Type `cmd` in the address bar  
  OR  
- Right-click → **Open in Terminal**

---

### Step 3: Verify Installation

```bash
nifectl --help
```

---

## Deployment Steps

### Step 1: Login

```bash
nifectl auth login
```

---

### Step 2: Initialize Project

```bash
nifectl init
```

Provide:
- Application name
- Organization
- Repository URL
- Branch (`main`)

---

### Step 3: Configure Deployment

- Deployment Type: Deployment
- Resource Type: CPU
- Replicas: 1

Ports:
- Internal: `8080`
- External: `80`

---

### Step 4: Deploy

```bash
nifectl deploy
```

---

### Step 5: Select Region

Example:

```
IND - Mumbai
```

---

### Step 6: Monitor Deployment

Monitor logs for:
- Validation
- Build
- Deployment

---

### Step 7: Access Application

```
https://<your-nife-url>
```

---

## Dependencies

| Dependency | Purpose         |
|------------|----------------|
| Ruby       | Runtime        |
| Sinatra    | Web framework  |
| Rack       | Interface layer|
| Puma       | Web server     |

---

## Environment Variables

| Variable | Description     | Default |
|----------|-----------------|---------|
| NAME     | Greeting name   | World   |

---

## Troubleshooting

| Issue               | Solution                    |
|--------------------|-----------------------------|
| Port already in use| Change port or stop process |
| Docker not running | Start Docker                |
| Image pull error   | Ensure image is public      |
| Build fails        | Verify configuration        |
| No workloads       | Create workload in NIFE     |
| Deployment blocked | Resolve security issues     |

---