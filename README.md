# 🤟 Silent Voice Manual Testing Project

Manual API testing for the **Silent Voice** platform using Postman — a system that helps people with hearing and speech disabilities by transcribing voice to text and converting text to sign language.

> **API Under Test:** [http://silentvoice.runasp.net](http://silentvoice.runasp.net)

---

## 👥 Team Members

- **Islam Waled**
- **Shrouk Elkassas**

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| Postman | API manual testing |
| Newman | Collection runner |

---

## 📁 Project Structure

```
Silent_Voice_Manual_Testing/
├── Silent_Voice_postman_collection.json   # Postman collection
├── Environment_Silent_Voice.json          # Postman environment
└── README.md
```

---

## 🧪 Test Coverage

### 🔐 Authentication (`/api/Auth`) — 13 Requests

| # | Request | Method | Type | Expected |
|---|---------|--------|------|----------|
| 1 | Register with valid data | POST | ✅ Positive | 200 + OTP message |
| 2 | Register with exceeded FName | POST | ❌ Negative | 400 + validation error |
| 3 | Confirm email with valid OTP | POST | ✅ Positive | 200 + confirmed |
| 4 | Confirm email with wrong OTP | POST | ❌ Negative | 400 |
| 5 | Confirm email with fixed OTP | POST | ✅ Positive | 200 + confirmed |
| 6 | Login with valid credentials | POST | ✅ Positive | 200 + JWT token |
| 7 | Login with wrong password | POST | ❌ Negative | 400 or 401 |
| 8 | Forgot password | POST | ✅ Positive | 200 |
| 9 | Verify reset OTP | POST | ✅ Positive | 200 |
| 10 | Verify wrong reset OTP | POST | ❌ Negative | 400 |
| 11 | Set new password | POST | ✅ Positive | 200 |
| 12 | Resend password reset OTP | POST | ✅ Positive | 200 |
| 13 | Resend email OTP | POST | ✅ Positive | 200 |

### 🤟 Sign Language (`/api/Sign`) — 4 Requests

| # | Request | Method | Type | Expected |
|---|---------|--------|------|----------|
| 1 | Save a sign sentence | POST | ✅ Positive | 200 + signID |
| 2 | Get sign history | GET | ✅ Positive | 200 + array |
| 3 | Get sign by ID | GET | ✅ Positive | 200 + sign data |
| 4 | Delete sign by ID | DELETE | ✅ Positive | 200 |

### 🎙️ Voice Transcription (`/api/Voice`) — 8 Requests

| # | Request | Method | Type | Expected |
|---|---------|--------|------|----------|
| 1 | Transcribe valid WAV file | POST | ✅ Positive | 200 + voiceID |
| 2 | Transcribe wrong extension | POST | ❌ Negative | 400 |
| 3 | Transcribe wrong language type | POST | ❌ Negative | 400 |
| 4 | Get voice history | GET | ✅ Positive | 200 + array |
| 5 | Get voice by ID | GET | ✅ Positive | 200 + voice data |
| 6 | Get audio file by filename | GET | ✅ Positive | 200 |
| 7 | Get audio with wrong filename | GET | ❌ Negative | 404 |
| 8 | Delete voice by ID | DELETE | ✅ Positive | 200 |

---

## 🚀 How to Run

### Option 1 — Postman UI
1. Import `Silent_Voice_postman_collection.json` into Postman
2. Import `Environment_Silent_Voice.json` as environment
3. Select the environment and run the collection

### Option 2 — Newman (CLI)
```bash
newman run Silent_Voice_postman_collection.json -e Environment_Silent_Voice.json
```

---

## 📋 Newman Report

- 🌐 [View Newman Report in Browser](https://htmlpreview.github.io/?https://github.com/ShroukElkassas/Silent_Voice-Manual-Testing-Project/blob/main/newman-report.html)

---

## 📊 Test Results Summary

| Module | Total Requests | Positive | Negative |
|--------|---------------|----------|----------|
| Auth | 13 | 9 | 4 |
| Sign | 4 | 4 | 0 |
| Voice | 8 | 5 | 3 |
| **Total** | **25** | **18** | **7** |
