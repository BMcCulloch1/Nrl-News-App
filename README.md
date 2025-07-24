# Nrl-News-App

A full-stack NRL news app that scrapes articles using Python, stores them in AWS S3, serves them through a simple Node.js Lambda API, and displays them in a clean React + Tailwind frontend. Built as a learning project to explore AWS, automation, and cloud deployment.

---

## Project Structure

This monorepo contains three parts:

```
nrl-news-app/
├── nrl-news-scraper/      # Python scraper running on EC2
├── nrl-news-lambda/       # Node.js Lambda function + API Gateway
├── nrl-news-frontend/     # React + Tailwind UI fetching and displaying the news
```

---

## Features

- Scrapes articles from [nrl.com](https://nrl.com) and [zerotackle.com](https://zerotackle.com) using Playwright and BeautifulSoup.
- Automatically uploads the latest news to S3 every hour.
- Serverless API built with AWS Lambda + API Gateway.
- Uses the AWS SDK for JavaScript (v3) to retrieve news data from S3
- Frontend built with React and styled using Tailwind CSS.
- Designed to be fast, clean, and easy to deploy.

---

## Deployment Overview

Each part of the app is managed independently:

### 1. **Scraper (Python + EC2)**
- Hosted on a t3.micro EC2 instance.
- Uses cron jobs to run every hour and on reboot.
- Uploads `latest_nrl_news.json` and `all_nrl_news.json` to an S3 bucket.

### 2. **Lambda API (Node.js)**
- Deployed with AWS SAM CLI.
- Fetches JSON from S3 and serves it via a `/news/` endpoint.

### 3. **Frontend (React + Tailwind)**
- Fetches data from the API and displays the latest articles.
- Mobile responsive and styled with Tailwind.

---

## What I Learned

This project helped me understand:
- EC2 automation with cron
- S3 integration using `boto3`
- Serverless backend with Lambda and API Gateway
- Building and styling a frontend with React and Tailwind
- Organising a full-stack project in a clean, modular way

---

## 📁 Repos

Each part of the project is a separate GitHub repo:

- [nrl-news-scraper](https://github.com/yourusername/nrl-news-scraper) — Python scraper + EC2 setup
- [nrl-news-lambda](https://github.com/yourusername/nrl-news-lambda) — Lambda function + API Gateway
- [nrl-news-frontend](https://github.com/yourusername/nrl-news-frontend) — React + Tailwind UI

---

## Tools & Tech

- Python (Playwright, BeautifulSoup, boto3)
- AWS (EC2, S3, Lambda, API Gateway)
- JavaScript (Node.js, React)
- Tailwind CSS
- AWS SAM CLI

---

## Next Steps

- Add pagination and past news archive
- Store image URLs for each article
- Improve error handling on all levels
- CI/CD with GitHub Actions and AWS

