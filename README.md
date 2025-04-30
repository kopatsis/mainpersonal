# kopatsis.com Giga Repo

This is a giga repo that contains everything powering my personal website. It includes both the **frontend** and the **backend contact service**.

---

## 🌐 Frontend

**Repo**: [kopatsis/kopatsiscom](https://github.com/kopatsis/kopatsiscom)  
**Live Site**: [https://kopatsis.com](https://kopatsis.com)

A minimalist, efficient HTML/CSS/JS frontend that serves as a professional and educational hub about myself. It includes:

- Project links
- Background and resume details
- A **"Contact Me"** form for direct communication

### Tech Stack

- Vanilla HTML, CSS, JS  
- jQuery and Bootstrap for interactivity and styling enhancements  
- Form submission via `fetch` API

The "Contact Me" form connects to the backend Go service described below.

---

## 📩 Contact Service (Backend)

**Repo**: [kopatsis/emaildrop](https://github.com/kopatsis/emaildrop)

A lightweight but robust Go server built with Gin, designed to receive and process form submissions from the frontend.

### Features

- Accepts form data and Cloudflare Turnstile token from the frontend
- Validates origin domain and ensures email formatting correctness
- Verifies Turnstile to prevent bot submissions
- Rate-limits submissions based on a 24-hour window to comply with SendGrid's free tier
- Geo-locates submissions using a built-in GeoIP2 MMDB to estimate city/country
- Sends a Slack webhook to my personal Slack with:
  - Form submission content
  - Request metadata including geo info and a generated request ID
- Sends confirmation email to the submitter via SendGrid
- Sends a backup email to my address: `j@kopatsis.com`
- Saves all submission data (including failed ones) into a local SQLite database

### Admin Features

- CLI access with a special password to:
  - Retrieve a single request by ID
  - Query all requests in a given time window

---

## 🛠 Deployment

- Hosted on the smallest DigitalOcean droplet  
- Deployed as a Docker container  
- Served under a subdomain of [kopatsis.com](https://kopatsis.com)

---

Feel free to explore each individual repo for more specific implementation details.
