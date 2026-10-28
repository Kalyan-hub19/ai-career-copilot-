# CareerPilot — AI Career Copilot

A responsive resume-vs-job-description analyzer powered by Gemini. The browser UI calls a Vercel serverless function; the Gemini API key stays on the server.

## Files
- `index.html` — responsive frontend, sample inputs, report view, downloadable text report
- `api/analyze.js` — server-side Gemini request and input validation
- `vercel.json` — Vercel configuration
- `.gitignore` — prevents local secrets from being committed

## Deploy to Vercel (recommended)
1. Download and unzip this project.
2. Create a GitHub repository named `ai-career-copilot-yourname`.
3. Upload the **contents** of this folder (not the enclosing zip) to the repository and commit.
4. In Vercel, choose **Add New → Project**, import that repository, and deploy. Framework preset can be **Other**.
5. In Vercel → Project → **Settings → Environment Variables**, add:
   - Name: `GEMINI_API_KEY`
   - Value: your Gemini API key from https://aistudio.google.com/
   - Environments: Production, Preview, Development (as needed)
6. Save, then go to **Deployments** and redeploy the latest deployment.
7. Open the deployed URL, paste a resume and a job description, and click **Analyze my match**.

## Test locally
The frontend can be opened directly, but the AI endpoint requires a server. To test the full project locally, install Node.js and Vercel CLI, set `GEMINI_API_KEY` in your shell environment, then run:
```bash
npm install -g vercel
vercel dev
```
Do not add the API key to `index.html`, commit it to GitHub, or share it in screenshots. If a key has already been exposed, rotate it in Google AI Studio.

## Notes
- This is an AI-generated estimate, not an official ATS score or guarantee of hiring.
- The API function validates request method and input length. For a public production app, consider adding rate limiting and abuse protection.
- The Gemini model name is set to `gemini-2.5-flash` in `api/analyze.js`; change it to a currently available model if your AI Studio project does not have access to it.
