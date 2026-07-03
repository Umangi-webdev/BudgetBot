
# 💸 AI-Powered Daily Expense Tracker

An intelligent, cross-platform expense tracking system where users can log daily expenses using **WhatsApp** or a **web dashboard**, powered by **AI (Groq)** and **fallback ML models**, with automated parsing, real-time dashboards, and budget alerts.

## 📽 Demo Video

[![Watch the demo](./frontend/src/assets/demo-thumbnail.jpg)](https://www.youtube.com/watch?v=iKhEwiE2R3o)

---

## 🚀 Features

✅ **Natural Language Entry**  
Log expenses by sending messages like:
```
"Spent 200 on groceries yesterday"  
"Uber 150"  
"100 food"
```

✅ **Dual Entry Points**
- **WhatsApp** using Twilio Webhook  
- **Web Chat** with AI parsing

✅ **AI-Powered Parsing**
- Uses **Groq (LLaMA 3)** to extract amount, category, date, and note  
- Fallback to custom ML model if AI fails

✅ **Auto-Categorization & Notes Extraction**

✅ **Monthly Budget Tracking**
- Users can set budgets per month
- Budget auto-carries forward if not updated

✅ **Interactive Dashboard**
- View expenses by date, category
- Filters, history log, charts & analytics
- Add expenses manually

✅ **Authentication & Authorization**
- JWT-based login/signup
- Role-based access for users

✅ **Email Alerts** (Future Scope)
- Sends automatic email alerts when spending exceeds the monthly budget

---

## 🧠 Tech Stack

| Layer      | Technology                                   |
|------------|----------------------------------------------|
| Frontend   | React, TailwindCSS, Axios, ShadCN, Recharts  |
| Backend    | Node.js, Express, JWT, MongoDB, Mongoose     |
| AI Parsing | Groq (LLaMA 3), fallback ML model (Python)   |
| ML Model   | Trained on expense messages for category prediction |
| Auth       | JWT + Protected Routes                       |
| Email      | Nodemailer (Gmail SMTP)                      |
| WhatsApp   | Twilio + Webhook (with Ngrok for testing)    |
| Deployment | Render / Railway (Backend) + Vercel (Frontend) |

---

## 🧩 System Architecture

```
graph TD
  User[User (Web/WhatsApp)] -->|Sends message| Backend
  Backend -->|Parse with Groq| GroqAI
  Backend -->|Fallback ML| MLModel
  Backend -->|Stores| MongoDB
  Backend -->|Trigger Email| Nodemailer
  WebApp -->|Visualize Data| React Dashboard
  WebApp -->|API Calls| Backend
  WhatsApp -->|Webhook| Twilio
```

---

## ✨ Unique Highlights

- 💬 **Expense tracking via WhatsApp**—no app install required  
- 🧠 **AI-enhanced natural language parsing** using Groq  
- 🔁 **Fallback ML categorization** ensures zero message loss  
- 📧 **Email alerts** when monthly budget exceeds  
- 📊 **Real-time, elegant dashboard** for expense visualization  
- 🛠 **Modular and scalable** codebase for real-world production use

---

## 📦 Folder Structure

```
root/
├── backend/
│   ├── config/
│   ├── controllers/
│   ├── middlewares/
│   ├── models/
│   ├── routes/
│   ├── utils/
│   └── index.js
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── contexts/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── main.jsx
│   │   ├── index.css
│   │   └── App.jsx
│   └── public/
├── model/
│   ├── app.py
│   ├── category_predictor.py
│   └── expense_dataset.csv
└── README.md
```

---

## 🛠️ Setup Instructions

### 1. Clone the Repo

```bash
git clone https://github.com/your-username/BudgetBot.git
cd BudgetBot
```

### 2. Setup Backend

```bash
cd backend
npm install
```

✅ Create `.env` file:

```
# 🌍 MongoDB Connection
MONGODB_URI=mongodb+srv://yourUsername:yourPassword@yourCluster.mongodb.net/ExpenseTracker

# 🤖 GROQ AI API
GROQ_API_KEY=gsk_your_groq_api_key_here

# 💬 Twilio WhatsApp Credentials
TWILIO_ACCOUNT_SID=ACXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
TWILIO_AUTH_TOKEN=your_twilio_auth_token
TWILIO_WHATSAPP_NUMBER=whatsapp:+14155238886

# 🔐 JWT Authentication
JWT_SECRET=super_secure_jwt_secret_key

# 🌐 Server Port
PORT=5000

# 🌍 Allowed Client URL for CORS (e.g., your React/Vercel frontend)
CLIENT_URL=https://your-frontend.vercel.app
```

### 3. Setup Frontend

```bash
cd ../frontend
npm install
npm run dev
```
✅ Create `.env` file:

```
# 🔗 Backend API URL
VITE_API_URL=http://localhost:5000/api
```

### 4. ML Model Setup (Optional)

If using fallback ML:

```bash
cd ../model
pip install -r requirements.txt
python app.py
```

### 5. WhatsApp Webhook (For Development)

- Use [Ngrok](https://ngrok.com/) to expose your local server:

```bash
ngrok http 5000
```

- Configure Twilio webhook URL with:  
  `https://<ngrok-id>.ngrok-free.app/api/whatsapp/webhook`

---

## 🔐 Authentication Flow

- Signup/Login with email/password  
- Protected routes using JWT  
- Frontend stores token in localStorage  
- Attach token in headers for secure API calls

---

## 📧 Budget Reminder Logic

- Users can set/update monthly budget via dashboard  
- If not set, last month’s budget is used  
- After every expense addition:
  - Total spending is checked  
  - If exceeds budget → Email alert is sent automatically

---

## ✅ Upcoming Enhancements

- 🧾 OCR-based receipt parsing  
- 💹 Expense trend predictions  
- 📆 Custom recurring reminders  
- 🧑‍🤝‍🧑 Shared budgeting for families

---

## 👩‍💻 Author

Made with ❤️ by [Umangi Patel](https://github.com/Umangi-webdev)  
Feel free to ⭐ this repo or contribute!

