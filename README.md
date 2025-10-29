<div align="center">
<img width="1200" height="475" alt="Screenshot" src="/images/page-screenshot.png" />
</div>

# just_a_blog — AI Tools Showcase

This repository contains a small Vite/React site built as an academic project for the Semester 7 course "Cloud Computing and Data Analytics". The goal was to build a lightweight site that demonstrates AI tooling and host it on Google Cloud Platform so it is globally accessible.

Live (deployed on GCP App Engine):

https://aitoolsframwork.de.r.appspot.com/

## What this repo includes

- Source for a small frontend app (Vite + React / TypeScript).
- A minimal `app.yaml` for App Engine deployment (used to host the app on GCP).

## Quick local run (development)

Prerequisites:

- Node.js (LTS recommended)
- npm (or pnpm/yarn)

Steps:

1. Install dependencies

```powershell
npm install
```

2. Provide your Gemini API key (used by the app if applicable)

- Option A — create `.env.local` in the repo root and add:

```
GEMINI_API_KEY=your_gemini_api_key_here
```

- Option B — set the environment variable in PowerShell (temporary for the session):

```powershell
$Env:GEMINI_API_KEY = 'your_gemini_api_key_here'
npm run dev
```

3. Start the dev server

```powershell
npm run dev
```

Visit the local address printed by Vite (usually http://localhost:5173).

## Build for production

```powershell
npm run build
```

You can preview the production build locally with:

```powershell
npm run preview
```

## Deploying to Google Cloud (App Engine)

This project was deployed to GCP App Engine. Below are the minimal steps used to publish the app. Adjust `YOUR_GCP_PROJECT_ID` and the region to your values.

Prerequisites:

- Install the Google Cloud SDK (gcloud) and authenticate: `gcloud auth login`
- Enable App Engine for your project.

Deploy steps (PowerShell):

```powershell
# Set the project
gcloud config set project YOUR_GCP_PROJECT_ID

# If you haven't created an App Engine app yet (choose region once):
gcloud app create --region=us-central

# Deploy using the included app.yaml
gcloud app deploy app.yaml --project=YOUR_GCP_PROJECT_ID

# Open the deployed site in the browser
gcloud app browse --project=YOUR_GCP_PROJECT_ID
```

Notes on secrets / API keys in production:

- For a simple setup you can store env vars in `app.yaml` under `env_variables:`. For better security, use Secret Manager and mount or fetch secrets at runtime.
- The live site for the semester project is hosted at the URL shown above.

## Academic context / Attribution

This repository and the deployed site were created as part of coursework for the Semester 7 subject "Cloud Computing and Data Analytics". The project demonstrates deploying a small frontend app to GCP App Engine with an AI-focused demo surface.

If you use this code or adapt it for coursework, please include appropriate attribution.

## Troubleshooting

- If deployment fails, check the App Engine logs in Cloud Console and verify your `app.yaml` is correct and any required build steps are present.
- Ensure required environment variables (like `GEMINI_API_KEY`) are available to the app in production.

## Contact

For questions about this academic project, contact the repository owner.

---
