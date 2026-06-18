# ✨ Celestial Sign-Out Web App
### Akindele Oluwaseun Deborah · Class of 2026

A digital graduation cloth-signing experience. Classmates visit the page, click the dress, type their name and a message, and their signature appears live for everyone.

---

## 🚀 Setup in 5 Steps

### Step 1 — Add Deborah's Photo
Replace the emoji placeholder in `index.html`:

Find this line:
```html
<div class="photo-placeholder">🌟</div>
<!-- <img src="photo.jpg" alt="Akindele Oluwaseun Deborah" /> -->
```

Replace with:
```html
<!-- <div class="photo-placeholder">🌟</div> -->
<img src="photo.jpg" alt="Akindele Oluwaseun Deborah" />
```

Then place `photo.jpg` in the same folder as `index.html`.

---

### Step 2 — Create a Firebase Project (free)

1. Go to [https://console.firebase.google.com](https://console.firebase.google.com)
2. Click **"Add project"** → name it `celestial-signout` → Continue
3. Disable Google Analytics (not needed) → **Create project**
4. Click **Firestore Database** in the left sidebar
5. Click **"Create database"** → choose **Production mode** → pick any region → **Enable**
6. Go to **Project Settings** (gear icon) → **Your apps** → click the `</>` Web icon
7. Register app name: `celestial-web` → **Register app**
8. Copy the `firebaseConfig` object shown

---

### Step 3 — Paste Firebase Config

Open `index.html` and find:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  ...
};
```

Replace with your real config from Step 2.

---

### Step 4 — Set Firestore Security Rules

In Firebase Console → Firestore → **Rules** tab, paste:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /signatures/{doc} {
      allow read: if true;
      allow create: if request.resource.data.name is string
                    && request.resource.data.name.size() > 0
                    && request.resource.data.name.size() <= 30;
    }
  }
}
```

Click **Publish**.

---

### Step 5 — Deploy to Vercel (free)

1. Create a [GitHub](https://github.com) account if you don't have one
2. Create a new **public** repository named `celestial-signout`
3. Upload `index.html` (and `photo.jpg`) to the repo
4. Go to [https://vercel.com](https://vercel.com) → sign in with GitHub
5. Click **"Add New Project"** → import `celestial-signout`
6. Framework Preset: **Other** → click **Deploy**
7. Vercel gives you a live URL like `celestial-signout.vercel.app`

**Share that URL with all of Deborah's classmates!** 🎉

---

## 📁 File Structure

```
celestial-signout/
├── index.html    ← the entire app (edit this file)
├── photo.jpg     ← Deborah's photo (you add this)
└── README.md     ← this file
```

---

## 💡 Customising

| What to change | Where in index.html |
|---|---|
| Bio text | Search for `hero-bio` |
| Page background colors | Search for `:root` → edit CSS variables |
| Max signature length | `maxlength="30"` on the name input |
| Max message length | `maxlength="80"` on the textarea |

---

Made with ❤️ for Celestial · Class of 2026
