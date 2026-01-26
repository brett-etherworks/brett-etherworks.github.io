# GitHub Pages Deployment Guide

## Complete Step-by-Step Guide to Publishing Your Dissertation Website

This guide will walk you through hosting your dissertation website on GitHub Pages for free. No prior Git/GitHub experience needed!

---

## Why GitHub Pages?

- ✅ **Completely free** - No hidden costs, forever
- ✅ **Custom domains supported** - Use your own domain name
- ✅ **HTTPS included** - Secure by default
- ✅ **Fast global CDN** - Quick loading worldwide
- ✅ **Version control** - Track all your changes
- ✅ **Open web ethos** - Aligns with your dissertation themes!

---

## Part 1: Initial Setup (One-Time)

### Step 1: Create a GitHub Account

1. Go to https://github.com
2. Click "Sign up" in the top right
3. Choose a username (this will be in your URL: `username.github.io`)
   - **Tip:** Use your name or professional handle
   - Example: `brettgaylor.github.io` or `bgaylor.github.io`
4. Complete the signup process

### Step 2: Create Your Repository

A repository (or "repo") is like a folder for your website files.

1. Once logged in, click the **+** icon (top right) → "New repository"
2. **Repository name:** Type `yourusername.github.io`
   - **IMPORTANT:** Replace `yourusername` with YOUR GitHub username exactly
   - Example: If your username is `brettgaylor`, name it `brettgaylor.github.io`
3. **Description:** "PhD Dissertation Website - Speculation, Culture Jamming & Play"
4. **Public** - Keep this selected (required for free GitHub Pages)
5. **✓ Check** "Add a README file"
6. Click **"Create repository"**

**🎉 Your repository is created!** It's empty except for a README, but we'll fix that.

---

## Part 2: Upload Your Website Files

You have two options: **Web Interface** (easier) or **GitHub Desktop** (more powerful).

### Option A: Web Interface Upload (Easiest)

1. In your repository, click **"Add file"** → **"Upload files"**

2. **Drag and drop these files** from your computer:
   ```
   index.html
   styles.css
   metaverse.html
   ursula.html
   brainrot.html
   patterns.html
   references.html
   ```

3. **Don't upload these** (you only need them for local testing):
   - Files ending in `-inline.html`
   - README.md (your repo already has one)
   - graph-backgrounds.css (not needed unless you want backup)
   - background-preview.html (just for testing)

4. Scroll down and click **"Commit changes"**
   - In the box, you can write: "Initial website upload"
   - Click the green "Commit changes" button

5. **Wait 2-3 minutes** for GitHub to build your site

6. **Visit your site!** Go to: `https://yourusername.github.io`

**🎉 Your site is live!**

### Option B: GitHub Desktop (Recommended for Updates)

If you'll be updating your site regularly, GitHub Desktop is easier:

1. **Download GitHub Desktop**
   - Go to: https://desktop.github.com
   - Install and sign in with your GitHub account

2. **Clone your repository**
   - File → Clone Repository
   - Find `yourusername.github.io` in the list
   - Choose where to save it on your computer
   - Click "Clone"

3. **Add your files**
   - Open the folder GitHub Desktop created
   - Copy all your HTML/CSS files into this folder
   - GitHub Desktop will automatically detect the new files

4. **Commit and push**
   - In GitHub Desktop, you'll see all your new files listed
   - Bottom left: Write a summary like "Initial website upload"
   - Click "Commit to main"
   - Click "Push origin" (top right)

5. **Wait 2-3 minutes**, then visit `https://yourusername.github.io`

---

## Part 3: Adding Videos (When Ready)

When you have your video files ready:

### If using Web Interface:
1. In your repository, click "Add file" → "Create new file"
2. In the name field, type: `videos/placeholder.txt`
   - This creates a `videos` folder
3. Commit the file
4. Now you can upload videos into the `videos` folder
5. Update your HTML to point to: `videos/yourvideoname.mp4`

### If using GitHub Desktop:
1. Create a `videos` folder in your local repository folder
2. Add your video files to it
3. Commit and push in GitHub Desktop

**⚠️ Size Limits:**
- Individual files: 100MB max
- Total repository: 1GB recommended max
- For larger videos, consider hosting on Vimeo/YouTube and embedding

---

## Part 4: Custom Domain (Optional)

Want to use your own domain like `brettgaylor.com` instead of `username.github.io`?

### Buy a Domain:
- **Canadian registrars:** Rebel.ca, CanSpace
- **Popular options:** Namecheap, Google Domains, Cloudflare

### Configure Your Domain:

1. **In your domain registrar's DNS settings**, add these records:
   ```
   Type: A
   Name: @
   Value: 185.199.108.153
   
   Type: A
   Name: @
   Value: 185.199.109.153
   
   Type: A
   Name: @
   Value: 185.199.110.153
   
   Type: A
   Name: @
   Value: 185.199.111.153
   
   Type: CNAME
   Name: www
   Value: yourusername.github.io
   ```

2. **In your GitHub repository:**
   - Go to Settings → Pages
   - Under "Custom domain", enter your domain
   - Click Save
   - Wait 24-48 hours for DNS to propagate

3. **Enable HTTPS** (after DNS works):
   - In Settings → Pages
   - Check "Enforce HTTPS"

---

## Part 5: Making Updates

### Using Web Interface:
1. Go to your repository on GitHub
2. Click on the file you want to edit
3. Click the pencil icon (✏️) to edit
4. Make your changes
5. Scroll down, write what you changed
6. Click "Commit changes"
7. Wait 2-3 minutes, refresh your site

### Uploading New Files via Web Interface:
1. Go to your repository on GitHub
2. Click "Add file" → "Upload files"
3. Drag the new files you want to add
4. Scroll down, write a message like "Added About and Dissertation pages"
5. Click "Commit changes"
6. Wait 2-3 minutes for the site to rebuild

### Replacing Existing Files via Web Interface:
1. Upload the new version of the file (same filename)
2. GitHub will automatically replace the old version
3. In the commit message, note what changed (e.g., "Updated navigation, removed sticky menu")

### Using GitHub Desktop:
1. Make changes to files on your computer
2. Open GitHub Desktop
3. You'll see your changes listed
4. Write a summary of what you changed
5. Click "Commit to main"
6. Click "Push origin"
7. Wait 2-3 minutes, refresh your site

---

## Part 6: Best Practices

### File Organization

Keep your repository organized:
```
yourusername.github.io/
├── index.html
├── styles.css
├── metaverse.html
├── ursula.html
├── brainrot.html
├── patterns.html
├── references.html
├── videos/
│   ├── metaverse-demo.mp4
│   ├── ursula-demo.mp4
│   └── brainrot-demo.mp4
├── images/
│   └── (any other images you need)
└── README.md
```

### Commit Messages

Write clear commit messages so you know what you changed:
- ✅ "Fixed typo in abstract section"
- ✅ "Added Design Patterns page"
- ✅ "Updated navigation styling"
- ❌ "changes"
- ❌ "update"

### Testing Before Pushing

Always test your changes locally first:
1. Open the HTML files in your browser from your computer
2. Check that everything works
3. Then push to GitHub

---

## Troubleshooting

### Site not showing up?
- Wait 3-5 minutes after first push
- Check Settings → Pages - is it enabled?
- Make sure repository name is exactly `username.github.io`

### 404 Error?
- Make sure your main file is named exactly `index.html` (lowercase)
- Check that you committed and pushed your files

### CSS not loading?
- Check that `styles.css` is in the same folder as your HTML files
- Make sure your HTML has: `<link rel="stylesheet" href="styles.css">`
- Try clearing your browser cache (Cmd+Shift+R on Mac)

### Videos not playing?
- Check file size (under 100MB)
- Make sure path is correct: `videos/filename.mp4`
- Try converting to H.264 MP4 format

### Changes not appearing?
- Wait 2-3 minutes for GitHub to rebuild
- Clear browser cache
- Try incognito/private browsing mode

---

## Advanced: Custom 404 Page

Create a file called `404.html` in your repository:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Page Not Found</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body class="case-study">
    <div class="container">
        <header>
            <h1>404: Page Not Found</h1>
        </header>
        
        <section>
            <p>The page you're looking for doesn't exist.</p>
            <p><a href="index.html">← Return to home</a></p>
        </section>
    </div>
</body>
</html>
```

---

## Quick Reference Commands

### If you use Git command line later:

```bash
# Clone your repository
git clone https://github.com/yourusername/yourusername.github.io.git

# See what changed
git status

# Add all changes
git add .

# Commit changes
git commit -m "Description of what you changed"

# Push to GitHub
git push origin main

# Pull latest changes (if editing from multiple places)
git pull origin main
```

---

## Security & Privacy

### Making Content Private Later

GitHub Pages requires public repositories for free hosting. If you need to make your research private:

1. **Option 1:** Delete the repository when you're done
2. **Option 2:** Upgrade to GitHub Pro ($4/month) for private repos
3. **Option 3:** Move to different hosting when needed

### Removing Your Site

To take down your site:
1. Go to Settings → Pages
2. Click "Unpublish site"

Or delete the entire repository:
1. Settings → Scroll to bottom
2. "Delete this repository"

---

## Resources

- **GitHub Pages Docs:** https://docs.github.com/en/pages
- **GitHub Desktop Guide:** https://docs.github.com/en/desktop
- **Markdown Guide** (for README): https://guides.github.com/features/mastering-markdown/
- **Custom Domain Help:** https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

---

## Next Steps After Deployment

1. **Test everything** - Click through all pages, check all links
2. **Share the URL** - Add it to your email signature, CV, etc.
3. **Set up Google Analytics** (optional) - Track visitors
4. **Add videos** when ready
5. **Keep iterating** - GitHub makes updates easy!

---

## Staying True to "View Source" Culture

GitHub Pages perfectly embodies the open web ethos from your dissertation:

- ✅ Anyone can "view source" on your site
- ✅ Your code is public (educational!)
- ✅ Version history is transparent
- ✅ Others can learn from your approach
- ✅ You control your own infrastructure

This is very much in the spirit of "jamming yourself" - your critical work about digital systems is itself openly accessible and inspectable!

---

**Questions?** 

GitHub has excellent documentation and a helpful community. Search for "GitHub Pages" + your question and you'll usually find answers quickly.

**Good luck! 🚀**
