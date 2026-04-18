# TherynTravel — Affiliate Marketing Travel Website

A static HTML/CSS/JS travel website for affiliate marketing, featuring destination galleries, booking partner links, an affiliate programs directory, an about section, and a newsletter sign-up form.

## 🗂 Project Structure

```
theryn/
├── index.html          # Single-page site
├── css/
│   └── style.css       # All styles (responsive)
├── js/
│   └── main.js         # Nav, filter, form, animations
└── images/             # Place your own travel photos here
```

## 🚀 Deploy to GitHub Pages (Free Hosting)

1. Go to your repository on GitHub: **Settings → Pages**
2. Under **Source**, select `Deploy from a branch`
3. Choose the **`main`** branch and **`/ (root)`** folder
4. Click **Save** — your site will be live at `https://arthur1972.github.io/theryn/` within a minute

## 📸 Replacing Placeholder Photos

Photos currently use Unsplash URLs. To use your own:

1. Add your images to the `/images/` folder (e.g., `images/maldives.jpg`)
2. In `index.html`, replace `https://images.unsplash.com/...` URLs with `images/maldives.jpg`

## 🔗 Adding Your Affiliate Links

In `index.html`, search for `href="https://www.expedia.com..."` (and other partner links) and replace them with your personal affiliate tracking URLs from each program's dashboard.

## ✉️ Connecting the Newsletter Form

The form currently shows a success message client-side. To actually collect emails, replace the form submission handler in `js/main.js` with your email service provider's API (e.g., Mailchimp, ConvertKit, Kit).

## 📄 License

MIT
