# My Personal Website — Setup Guide

## Folder Structure

```
mywebsite/
├── index.html          ← Home page
├── about.html          ← About me
├── reading.html        ← Reading list
├── weekly.html         ← Weekly log
├── articles.html       ← Articles I've read
├── newspaper.html      ← News clippings + images
├── personalities.html  ← People who inspire me
├── thoughts.html       ← Random thoughts & questions
├── daylife.html        ← Day in my life
├── work.html           ← Work & learning log
├── writings.html       ← Shayari, poems, stories
├── resume.html         ← Resume
├── css/
│   └── style.css       ← All styling (one file, easy to edit)
├── images/
│   ├── background.jpg  ← Your background image (add this!)
│   ├── me.jpg          ← Your photo for About page
│   └── newspaper-*.jpg ← Newspaper clipping photos
└── files/
    └── resume.pdf      ← Optional: PDF version of resume
```

---

## Step 1 — Set Up on Your Linux (WSL)

```bash
# Go to your home folder
cd ~

# Create a folder for your website
mkdir mywebsite
cd mywebsite

# Initialize git
git init
```

Then copy all the files from the downloaded zip into this folder.

---

## Step 2 — Run Locally (Preview Before Publishing)

You don't need Node, Python, or anything special.
Just open the files in a browser:

```bash
# Option 1: Python simple server (easiest)
cd ~/mywebsite
python3 -m http.server 8000

# Then open in browser: http://localhost:8000
```

Or just double-click index.html in your file explorer.

---

## Step 3 — Add Your Background Image

1. Pick any image you like (a landscape, texture, something meaningful)
2. Copy it to the images/ folder:

```bash
cp ~/Downloads/your-photo.jpg ~/mywebsite/images/background.jpg
```

The image is already set to very low opacity (0.07) so it's subtle.
To make it more visible, open css/style.css and change:
`opacity: 0.07;` → `opacity: 0.15;`

---

## Step 4 — Customize Your Details

Open each HTML file and replace:
- `Your Name` → your actual name
- `you@email.com` → your email
- `yourusername` → your GitHub username
- The intro paragraph on index.html → your own words

---

## Step 5 — Push to GitHub

### First time setup:

```bash
# 1. Create account at github.com if you don't have one

# 2. Create a new repository on github.com
#    Name it EXACTLY: yourusername.github.io
#    (Replace 'yourusername' with your GitHub username)
#    Make it Public
#    Do NOT initialize with README

# 3. In WSL terminal:
cd ~/mywebsite
git init
git add .
git commit -m "first commit - my personal website"
git branch -M main
git remote add origin https://github.com/yourusername/yourusername.github.io.git
git push -u origin main
```

### Every time you make changes:

```bash
cd ~/mywebsite
git add .
git commit -m "added weekly log for week 21"
git push
```

That's it. 3 commands every time you update.

---

## Step 6 — Enable GitHub Pages (Free Hosting)

1. Go to your repository on github.com
2. Click **Settings** tab
3. Click **Pages** in the left sidebar
4. Under "Branch", select `main` and click Save
5. Wait 1-2 minutes

Your website will be live at: `https://yourusername.github.io`

---

## Step 7 — Custom Domain (like jayesh.in)

To get yourdomain.in:

1. **Buy the domain** from GoDaddy, Namecheap, or BigRock (~₹800-1500/year for .in)

2. **Add a CNAME file** to your website folder:

```bash
echo "yourdomain.in" > ~/mywebsite/CNAME
git add CNAME
git commit -m "add custom domain"
git push
```

3. **In GitHub Pages settings**: enter your domain under "Custom domain"

4. **In your domain registrar** (GoDaddy/Namecheap), add these DNS records:
   ```
   Type: A,  Host: @,  Value: 185.199.108.153
   Type: A,  Host: @,  Value: 185.199.109.153
   Type: A,  Host: @,  Value: 185.199.110.153
   Type: A,  Host: @,  Value: 185.199.111.153
   Type: CNAME,  Host: www,  Value: yourusername.github.io
   ```

5. Wait 10-30 minutes for DNS to update. Then it's live!

---

## How to Update the Website (Quick Reference)

### Add a new weekly log entry:
Open `weekly.html` → copy an existing week block → paste it above → update the content → save → push to GitHub

### Add a new shayari:
Open `writings.html` → copy the shayari block → paste it at top → write your shayari → save → push

### Add a newspaper image:
```bash
cp ~/Downloads/photo.jpg ~/mywebsite/images/newspaper-may21.jpg
# Then open newspaper.html and add:
# <img src="images/newspaper-may21.jpg" alt="description" class="newspaper-img" />
```

### Add a new personality:
Open `personalities.html` → copy a card block → paste it → update name, description → save → push

---

## Changing Colors

Open `css/style.css` and find this at the top:

```css
--accent: #8b4513;   /* warm brown — change this to any color */
```

Some nice options:
- Deep blue: `#1a3a5c`
- Forest green: `#2d6a4f`
- Warm red: `#c0392b`
- Ink black: `#1a1a1a`

---

## That's it!

The whole website is just HTML files + one CSS file.
No framework. No build step. No complications.
You edit a file, push to GitHub, and it's live in seconds.
