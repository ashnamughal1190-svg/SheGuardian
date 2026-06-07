# SheGuardian — AI-Powered Women's Safety App

An Android app that protects women in emergencies by detecting danger **automatically** and alerting trusted contacts — without the user needing to unlock or even touch the phone.

> Final Year Project — BS Information Technology, International Islamic University, Islamabad.

---

## The Problem

Most safety apps rely on manually pressing an SOS button. In a real emergency, a person often can't reach their phone in time. **SheGuardian removes that dependency** by triggering automatically through multiple channels.

## Key Features

- **Multi-trigger SOS** — three independent ways to raise an alarm:
  - A deliberate **3-second button hold** (with animated countdown to prevent accidental triggers)
  - A **phone shake** (accelerometer-based)
  - A spoken **safe-phrase** (voice recognition)
- **Automatic silent SMS** to trusted contacts with a live location link — works over the cellular network even with no internet.
- **Real-time GPS tracking** on an OpenStreetMap view, shared with guardians.
- **AI threat analysis** using the **Google Gemini API** plus on-device motion sensing to confirm real danger and reduce false alarms.
- **Automatic audio/video evidence** capture, indexed per user.
- **Phone-OTP registration** (Firebase Phone Authentication).
- **Emergency-contact management**, fake-call escape feature, and safety-tips library.
- **Admin dashboard** for live SOS monitoring, built on real-time Firestore streams with role-based access control.

## Tech Stack

| Layer | Technologies |
|-------|-------------|
| Frontend | Flutter, Dart |
| Backend | Firebase (Authentication, Cloud Firestore, Storage, Messaging) |
| AI | Google Gemini API |
| Sensors & Maps | sensors_plus, geolocator, speech_to_text, flutter_map / OpenStreetMap |
| Media & Messaging | flutter_sound, camera, another_telephony, url_launcher |

## Screenshots

| Home / SOS | Live Tracking | Admin Dashboard |
|-----------|---------------|-----------------|
| ![Home](screenshots/home.png) | ![Tracking](screenshots/tracking.png) | ![Admin](screenshots/admin.png) |

## How It Works

1. User registers and verifies their phone number via OTP, then adds trusted contacts.
2. An emergency is triggered — by button hold, shake, or voice.
3. The app captures GPS location and starts recording evidence.
4. The AI module evaluates the context to confirm the threat.
5. Automatic SMS is sent to all contacts; the admin dashboard updates in real time.
6. Live location is shared until the user marks themselves safe.

## Technical Highlights

- Background sensor pipeline computing accelerometer magnitude `√(x² + y² + z²)` with debounce logic for reliable shake detection.
- Reactive architecture: `authStateChanges` StreamBuilder for session persistence; live admin dashboard via Firestore StreamBuilders.
- Firebase Phone-OTP with email/password credential linking.
- Security enforced at the database layer with Firestore security rules (RBAC), not just client-side checks.
- Integrated and debugged the **Google Gemini API** for contextual threat evaluation.
- Performance targets met: sub-2-second trigger-to-dashboard latency, <3%/hour background battery draw, validated on a physical device.

## My Role

I built this project as part of a two-person final-year team and owned the majority of the product. My contributions included most of the design and development — the multi-trigger SOS engine (button-hold, shake, and voice), the Google Gemini AI integration for threat evaluation, the Firebase backend (Phone-OTP authentication, the Firestore data model, and security rules), and the real-time admin dashboard. I made most of the product decisions and was responsible for getting the features working end-to-end on a physical device.

I developed SheGuardian primarily through **AI-assisted development** — using AI coding assistants to design and write the implementation, then reviewing, testing, and correcting their output to make the app reliable. My teammate contributed to part of the user interface and some backend work.

## Status

Functional prototype. Some features (safe zones, disguise mode) are planned as future work.

---

*Built with Flutter & Firebase · 2026*
