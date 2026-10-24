# Neo: standalone voice assistant

Neo is a plain web app: no server, no sign-up, no build step. You host the files for free, open the link on your Android phone, and paste in a free AI key. Nothing here costs money or asks for payment details.

Files: `index.html` (the app), `manifest.webmanifest`, `sw.js` and two icons (these let Android install it like an app).

## Step 1: Get a free AI key (about 2 minutes)

Recommended: **Google Gemini**.

1. Open https://aistudio.google.com/apikey and sign in with a Google account.
2. Tap **Create API key** and copy it.

Good to know: the free tier needs no card and is rate-limited (the limits are shown in your AI Studio console). Google may use free-tier chats to improve its products, so don't tell Neo anything you want kept private. If chat later says the model name isn't accepted, open Neo's Settings and type a current free model name from AI Studio into **Model**.

Other free choices, picked in Neo's Settings:
- **OpenRouter** (https://openrouter.ai/keys): free models, no card, about 50 requests a day, and the model behind it changes.
- **Groq** (https://console.groq.com/keys): free tier with limits.
- **Custom**: any OpenAI-compatible server, for example Ollama on your own computer.

## Step 2: Put the app online (free)

Neo must be on an `https://` address. Opening `index.html` straight from your phone's files usually blocks the microphone and installing.

**Option A: Netlify Drop (easiest on a computer)**
1. Unzip `neo-app.zip` so you have a folder.
2. Go to https://app.netlify.com/drop and drag the folder onto the page.
3. Netlify gives you a link ending in `netlify.app`. Check Netlify's current free-plan terms.

**Option B: GitHub Pages (works from the phone alone)**
1. Make a free account at https://github.com, then create a **public** repository named `neo`.
2. Tap **Add file, then Upload files**, upload all five files, and commit.
3. Open **Settings, then Pages**. Under Branch, pick `main` and `/ (root)`, then Save.
4. After a minute or two your app is at `https://YOUR-USERNAME.github.io/neo/`.

Never put your API key in these files. You type it into the app instead, so a public repository is safe.

## Step 3: Set up on Android

1. Open your link in **Chrome**.
2. Go to the **Settings** tab, choose your provider, paste the key, and tap **Test**. You should see "Connected".
3. Go to **Talk**, tap the orb, and allow the microphone when asked.
4. Chrome menu (three dots), then **Add to Home screen** or **Install app**.

## What works and what doesn't

Works: chat, voice input (Chrome's speech recognition, which needs internet), spoken replies in a female English voice from your phone, saved memory you can edit, tasks, and reminders.

Doesn't, because it's a web app:
- **Reminders only alert while Neo is open on screen.** Alerts with the app closed need a native Android app.
- **No "Neo" wake word.** Always-listening needs a native Android app with microphone permissions.
- **No email or phone integrations, and no login.**
- **Memory lives only in this browser on this device.** It isn't synced, and clearing Chrome's site data erases it. Another phone starts empty.

## Privacy and safety

- Your key is stored in the browser on your phone in plain form. Anyone using your unlocked phone could read it. Use a free key you can delete, and delete it at the provider if you lose the phone.
- Your messages and saved memories go to the provider you chose when Neo replies.
- Neo refuses to save passwords or card numbers and asks before saving sensitive facts.

## Fixing problems

| You see | Try |
|---|---|
| Microphone is blocked | Chrome menu, Settings, Site settings, Microphone, allow your Neo address |
| API key was rejected | Re-copy the key with no spaces |
| Free limit reached | Wait a minute, try tomorrow, or switch provider |
| Model name not accepted | Type a current model name into the Model field |
| No voice or wrong voice | Pick one in Settings; voices come from your phone |

## Next steps

A wake word needs a native Android app: a foreground service with microphone permission and an on-device detector such as Porcupine, which has its own licence and a free tier you would need to check. It would open this same web app or call the same AI provider.
