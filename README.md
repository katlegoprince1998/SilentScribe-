# 📄 SilentScribe – AI-Powered Meeting Transcriber & Summarizer with Team Accountability

> **SilentScribe** is a powerful SaaS platform that helps teams by transcribing meetings, generating intelligent summaries, identifying action items, and tracking accountability.

---

## 🚀 Tech Stack (MERN)

<p align="center">
  <img src="https://img.shields.io/badge/MongoDB-%2347A248.svg?&style=for-the-badge&logo=mongodb&logoColor=white" width=150 height=60/>
  <img src="https://img.shields.io/badge/Express.js-%23000000.svg?&style=for-the-badge&logo=express&logoColor=white" width=150 height=60/>
  <img src="https://img.shields.io/badge/React-%2361DAFB.svg?&style=for-the-badge&logo=react&logoColor=black" width=150 height=60/>
  <img src="https://img.shields.io/badge/Node.js-%23339933.svg?&style=for-the-badge&logo=node.js&logoColor=white" width=150 height=60/>
</p>

## 🧠 Vision

A productivity-driven solution for remote teams, project managers, and consultants who want to:

* Save time by avoiding manual note-taking.
* Automatically track responsibilities.
* Hold teams accountable with accurate follow-ups.

### 🎯 Target Market

* Remote-first teams
* Agile development teams
* Consulting agencies
* Project managers and team leads
* HR & recruiting departments conducting frequent interviews

---

## 📘 Business Requirement Specification (BRS)

### 🧾 Modules

1. **Authentication & Authorization**

   * JWT-based login/registration
   * Google/Slack OAuth (optional)
2. **Team & User Management**

   * Team creation/invite
   * Role-based access (Admin, Member, Guest)
3. **Meeting Management**

   * Upload or record meetings
   * AI transcription (Whisper, AssemblyAI, Deepgram)
   * AI summarization (GPT-4)
4. **Task & Action Items**

   * Auto-generated tasks from summaries
   * Assignment, tracking, and status updates
5. **Accountability Dashboard**

   * Completion tracking, metrics, and reminders
6. **Integrations** (future)

   * Google Calendar
   * Slack
   * Zoom

### 📊 KPIs

* % of meetings with action items generated
* Task completion rate per user/team
* Average turnaround time per task

---

## 🧰 Tools & Services

| Tool/Service        | Purpose                         |
| ------------------- | ------------------------------- |
| MongoDB Atlas       | Database                        |
| Express.js          | RESTful APIs                    |
| React.js            | Frontend UI                     |
| Node.js             | Backend runtime                 |
| OpenAI Whisper      | Audio transcription             |
| GPT-4 API           | Summarization & NLP             |
| AWS S3 / Cloudinary | Audio file storage              |
| Socket.io           | Real-time transcription updates |
| Mongoose            | MongoDB ODM                     |
| Postmark/SendGrid   | Email notifications/reminders   |

---

## 🗂️ Core Features

### ✅ Authentication & Teams

* JWT-based auth
* Team creation and invites
* User roles: Admin, Member, Guest

### 📂 Meeting Transcription

* Upload or record meetings
* Store transcripts
* View real-time transcription (via Socket.io)

### 📝 AI Summarization

* Auto-generated summary with:

  * Key takeaways
  * Decisions
  * Next steps
  * Action items

### 📌 Action Items & Tasks

* Extracted via AI from transcript
* Assignable to team members
* Track status and deadlines

### 📊 Accountability Dashboard

* Overview of task completion
* Team performance metrics
* Weekly digest/reminders

---

## 🧪 Database Models (Mongoose)

### `User`

```js
{
  _id, name, email, teamId, role, assignedTasks: [ObjectId]
}
```

### `Meeting`

```js
{
  _id, teamId, title, date, audioUrl, transcript, summary, participants: [ObjectId], actionItems: [ObjectId]
}
```

### `ActionItem`

```js
{
  _id, meetingId, description, assignedTo, dueDate, status
}
```

### `Team`

```js
{
  _id, name, members: [ObjectId]
}
```

---

## 🧭 Roadmap (2025 - 2027)

### 🔹 2025 (MVP Year)

* [x] Setup MongoDB, Express, Node.js, React
* [ ] Implement authentication & team management
* [ ] Integrate transcription API (Whisper/Deepgram)
* [ ] Build Meeting CRUD + storage

### 🔹 2026 (AI & Accountability Focus)

* [ ] Summarization via GPT-4
* [ ] Task extraction from transcript
* [ ] Dashboard for team accountability
* [ ] Slack + Email reminder integration

### 🔹 2027 (Growth & Scale)

* [ ] Integrate with Google Meet/Zoom
* [ ] Support multilingual transcription/summarization
* [ ] Deploy with CI/CD, monitoring, and logging
* [ ] Launch paid plans & SaaS monetization

---

# 📘 SilentScribe – API Endpoints & UI Screens Documentation

This document provides a comprehensive list of API endpoints and frontend screens to be implemented for the SilentScribe SaaS project.

---

## 🧩 API Endpoints (REST)

### 🔐 Authentication

| Method | Endpoint             | Description                      |
| ------ | -------------------- | -------------------------------- |
| POST   | `/api/auth/register` | Register new user                |
| POST   | `/api/auth/login`    | Authenticate user and return JWT |
| GET    | `/api/auth/me`       | Get current authenticated user   |

---

### 👥 User & Team Management

| Method | Endpoint                | Description                   |
| ------ | ----------------------- | ----------------------------- |
| GET    | `/api/users`            | Get all users (admin only)    |
| GET    | `/api/users/:id`        | Get single user by ID         |
| PATCH  | `/api/users/:id`        | Update user profile or role   |
| GET    | `/api/teams`            | Get all teams user belongs to |
| POST   | `/api/teams`            | Create new team               |
| GET    | `/api/teams/:id`        | Get specific team info        |
| PATCH  | `/api/teams/:id`        | Update team name or members   |
| POST   | `/api/teams/:id/invite` | Invite a user to the team     |

---

### 🎤 Meetings

| Method | Endpoint                       | Description                     |
| ------ | ------------------------------ | ------------------------------- |
| GET    | `/api/meetings`                | List all meetings (per team)    |
| POST   | `/api/meetings`                | Create a new meeting entry      |
| GET    | `/api/meetings/:id`            | Get meeting details             |
| PATCH  | `/api/meetings/:id`            | Update meeting metadata         |
| DELETE | `/api/meetings/:id`            | Delete a meeting                |
| POST   | `/api/meetings/:id/transcribe` | Upload or trigger transcription |
| GET    | `/api/meetings/:id/transcript` | Fetch the transcript            |

---

### 📝 Summaries & Action Items

| Method | Endpoint                         | Description                           |
| ------ | -------------------------------- | ------------------------------------- |
| GET    | `/api/meetings/:id/summary`      | Get AI-generated summary              |
| GET    | `/api/meetings/:id/action-items` | Get list of action items              |
| POST   | `/api/meetings/:id/action-items` | Add action items manually             |
| PATCH  | `/api/action-items/:id`          | Update action item (status, due date) |
| DELETE | `/api/action-items/:id`          | Delete an action item                 |

---

### 📊 Dashboard & Notifications

| Method | Endpoint             | Description                        |
| ------ | -------------------- | ---------------------------------- |
| GET    | `/api/dashboard`     | Get user/team accountability stats |
| GET    | `/api/notifications` | List all reminders/alerts          |
| POST   | `/api/notifications` | Create custom reminder             |

---

## 💻 Frontend Screens (React.js)

### 🔐 Auth Screens

* **LoginPage.jsx** – Login form
* **RegisterPage.jsx** – Registration form

---

### 🏠 Dashboard Screens

* **DashboardOverview\.jsx** – Task/activity summary
* **WeeklyDigest.jsx** – Weekly accountability digest view

---

### 👥 Team Screens

* **TeamList.jsx** – List all teams
* **TeamCreate.jsx** – Create a new team
* **TeamDetails.jsx** – Team members and meeting links
* **InviteMemberModal.jsx** – Invite user modal

---

### 🎤 Meeting Screens

* **MeetingList.jsx** – Show all meetings
* **MeetingCreate.jsx** – Upload/record audio
* **MeetingDetails.jsx** – View transcript, summary, action items
* **TranscriptionUpload.jsx** – Upload audio file
* **LiveTranscription.jsx** – Real-time transcription viewer

---

### 📝 Action Items Screens

* **ActionItemList.jsx** – Tasks generated from a meeting
* **ActionItemEdit.jsx** – Edit task (assign, due date, status)
* **CreateManualActionItem.jsx** – Add custom task manually

---

### 📊 Analytics & Notifications

* **AccountabilityBoard.jsx** – Charts showing completion rate, delays
* **NotificationsList.jsx** – User notifications
* **CreateReminder.jsx** – Set a manual reminder

---

## 🗂️ Admin Tools & Settings

* **AdminUserList.jsx** – View/manage all users
* **AppSettings.jsx** – API keys, integrations, feature flags
* **BillingPlans.jsx** – View/upgrade plans (2027 goal)

---

## 🧩 Notes

* API secured with JWT auth middleware
* All data tied to `teamId` for multi-tenant support
* Summarization and transcription handled via OpenAI/Whisper APIs


---

## 🧑‍💻 Contributing

Want to contribute? Feel free to fork and build on it. Reach out with ideas or suggestions!

---

## ⭐ Final Thoughts

SilentScribe is more than a meeting tool—it's your team's accountability assistant. With smart transcriptions and task tracking, it ensures no good idea or responsibility is ever forgotten again.

> "Talk less, track more – let SilentScribe handle the details."

## 📬 Contact

**Author**: Katlego Prince Mashego
**Email**: katlegomashego37@gmail.com
**Company**: Quantum Digital Applications (QDA)

**License:** MIT License

