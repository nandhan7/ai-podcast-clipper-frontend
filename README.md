# 🎙️ AI Podcast Clipper – SaaS App



[📺 Watch Demo](https://drive.google.com/file/d/1lkXG43_PV93VtTn8uO2AT1JmSjgfjtnn/view?usp=sharing)  


AI Podcast Clipper is a full-stack SaaS application that takes long-form podcasts and transforms them into viral, short-form content suitable for YouTube Shorts and TikTok. It uses AI for transcription, speaker detection, clip generation, and smart cropping — all packed inside a clean UI and a credit-based system.

---

## 🌟 Features

- 🧠 Viral moment detection using Gemini Pro
- 📝 Transcription with WhisperX
- 🎯 Speaker activity detection with LR-ASD
- 🎞️ Vertical video generation using FFMPEG
- ⚙️ Background job queues using Inngest
- 🚀 GPU-accelerated processing via Modal
- 🔐 User authentication (Auth.js)
- 💳 Stripe-powered credit system
- 🌐 Uploads to AWS S3
- 📱 Responsive UI with Tailwind + Shadcn

---

## 🛠 Tech Stack

| Layer      | Tech Stack |
|------------|------------|
| Frontend   | Next.js 15, React, TypeScript, Tailwind CSS, Shadcn, Inngest, Auth.js |
| Backend    | Python 3.12, FastAPI, WhisperX, LR-ASD, Modal, FFMPEG |
| Infra/Cloud| AWS S3, Stripe, Modal, Gemini API |

---

## 🚀 Project Structure

```
AI-Podcast-Clipper/
├── Frontend/                # Next.js + Tailwind frontend
│   └── pages/, components/, inngest/
├── Backend/                 # FastAPI + AI pipeline
│   └── main.py, whisper_utils.py, etc.
├── README.md
```

---

## 🧪 Test Videos

- [MI6 Secret Agent Talks About the World's Darkest Secrets](https://www.youtube.com/watch?v=-vMgbJ6WqN4)
- [Janney Sanchez – Therapy Saved My Life](https://www.youtube.com/watch?v=SOG0GmKts_I)

---

## ⚙️ Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/nandhan7/AI-Podcast-Clipper.git
cd AI-Podcast-Clipper
```

---

## 🖥️ Frontend Setup (Next.js)

```bash
cd Frontend
npm install
npm run dev
```

Start Inngest queue:

```bash
npm run inngest-dev
```

### 🔐 Frontend `.env.local` Example

```env
DATABASE_URL="postgres://neondb_owner:"

PROCESS_VIDEO_ENDPOINT="https://bvnandhan--ai-podcast-clipper-aipodcastclipper-process-video.modal.run"
PROCESS_VIDEO_ENDPOINT_AUTH="sdfsdf"

S3_BUCKET_NAME="asdfdsfn"
AWS_REGION="ap-southeast-2"

AWS_ACCESS_KEY_ID="sdgfdf"
AWS_SECRET_ACCESS_KEY="sdfdsf"

NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY="sdfdsfdsfdsfdsfds"
STRIPE_SECRET_KEY="szdfgdsfsfds"
STRIPE_SMALL_CREDIT_PACK="price_1RhTtJPIAduvIetubV3JwEjA"
STRIPE_MEDIUM_CREDIT_PACK="price_1RhTuTPIAduvIetumnOrRzoD"
STRIPE_LARGE_CREDIT_PACK="price_1RhTutPIAduvIetuYogZ503A"

BASE_URL="http://localhost:3000"
STRIPE_WEBHOOK_SECRET="sdfdsfdsfdsfdsfdsfdsfds"
```

---

## 🧠 Backend Setup (FastAPI + AI)

```bash
cd Backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
```

### Add LR-ASD (Speaker Detection)

```bash
git clone https://github.com/Junhua-Liao/LR-ASD.git
mv LR-ASD asd
```

### Run Locally (Optional)

```bash
uvicorn main:app --reload
```

---

## 🚀 Modal Deployment

Make sure you're signed in to [Modal](https://modal.com):

```bash
modal setup
modal run main.py
modal deploy main.py
```

---

## ☁️ AWS S3 Setup

### ✅ CORS Policy

```json
[
  {
    "AllowedHeaders": ["Content-Type", "Content-Length", "Authorization"],
    "AllowedMethods": ["PUT"],
    "AllowedOrigins": ["*"],
    "ExposeHeaders": ["ETag"],
    "MaxAgeSeconds": 3600
  }
]
```

### ✅ IAM Policy Example

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": "arn:aws:s3:::your-bucket-name"
    },
    {
      "Effect": "Allow",
      "Action": ["s3:GetObject", "s3:PutObject"],
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

---

## 🔑 Gemini API Setup

Sign up and get an API Key here:  
👉 https://ai.google.dev/gemini-api/docs/quickstart?lang=python

Use Gemini 1.5 Pro or Gemini 2.5 Pro to identify viral moments from transcript text.

---

## 💳 Stripe Setup

- Create a Stripe account
- Add your `STRIPE_SECRET_KEY` and `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY` to the `.env` files
- Setup Stripe webhooks if needed

---

## ✅ To Do

- [x] Transcription pipeline
- [x] Active speaker detection
- [x] Modal GPU processing
- [x] AWS S3 upload
- [x] Credit system
- [x] Stripe integration
- [x] Gemini API
- [ ] Add YouTube upload support
- [ ] Improve clip highlight quality

---

## 📄 License

MIT © 2025 — B V Nandhan  
Inspired by Andreas Trolle's tutorial on building viral AI podcast clippers.
