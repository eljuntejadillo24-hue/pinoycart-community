# PinoyCart Community App

Installable PWA + Node.js backend.

## Features
- Register/login; bcrypt password hashing
- Text and image posts (5 MB image limit)
- Like/unlike, comments
- Member profile, bio, profile photo
- Basic notifications for likes/comments
- Admin moderation: hide/delete posts
- PWA manifest and service worker

## Run
Install Node.js 18+. In this folder:
```bash
npm install
```
Set admin account and a strong session secret, then start.

Linux/macOS:
```bash
export SESSION_SECRET="use-a-long-random-secret"
export ADMIN_USERNAME="admin"
export ADMIN_PASSWORD="choose-a-strong-password"
npm start
```
Windows PowerShell:
```powershell
$env:SESSION_SECRET="use-a-long-random-secret"
$env:ADMIN_USERNAME="admin"
$env:ADMIN_PASSWORD="choose-a-strong-password"
npm start
```
Open http://localhost:3000.

Admin is created on first startup only if ADMIN_USERNAME and ADMIN_PASSWORD are set and no admin exists.

## Android
For an installable app, deploy the server to a host with HTTPS, open the HTTPS URL in Chrome on Android, then use Chrome menu > Install app / Add to Home screen. For local testing, phone and computer can share Wi-Fi, but PWA installation/service-worker support generally requires HTTPS (or localhost on the same device).

## Data and hosting
Data is saved in `data/community.json`; uploaded images are in `uploads/`. Use hosting with persistent disk. The default session store is in-memory and is suitable only for local testing/single instance. Before public launch, add a persistent session store, rate limiting, CSRF protection, email/phone verification, password reset, report workflows, backups, and preferably migrate JSON data to PostgreSQL/object storage. Always use HTTPS and change SESSION_SECRET. Do not publish credentials or user data.
