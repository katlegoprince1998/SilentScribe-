# 📄 SilentScribe – AI-Powered Meeting Transcriber & Summarizer with Team Accountability

> **SilentScribe** is a powerful SaaS platform that helps teams by transcribing meetings, generating intelligent summaries, identifying action items, and tracking accountability.

---

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

## 🚀 Tech Stack (MERN)

<p align="center">
  <img src="https://img.shields.io/badge/MongoDB-%2347A248.svg?&style=for-the-badge&logo=mongodb&logoColor=white"/>
  <img src="https://img.shields.io/badge/Express.js-%23000000.svg?&style=for-the-badge&logo=express&logoColor=white"/>
  <img src="https://img.shields.io/badge/React-%2361DAFB.svg?&style=for-the-badge&logo=react&logoColor=black"/>
  <img src="https://img.shields.io/badge/Node.js-%23339933.svg?&style=for-the-badge&logo=node.js&logoColor=white"/>
</p>

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

## 🧑‍💻 Contributing

Want to contribute? Feel free to fork and build on it. Reach out with ideas or suggestions!

---

## 📬 Contact

**Author**: Katlego Mashego
**Email**: \[Insert your contact email]
**Company**: Quantum Data Analytics (QDA)

---

## ⭐ Final Thoughts

SilentScribe is more than a meeting tool—it's your team's accountability assistant. With smart transcriptions and task tracking, it ensures no good idea or responsibility is ever forgotten again.

> "Talk less, track more – let SilentScribe handle the details."

---

**License:** MIT License

