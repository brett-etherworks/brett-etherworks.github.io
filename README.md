# Dissertation Website - Local Development Guide

## About This Project

This is a website for Brett Gaylor's PhD dissertation: "Speculation, Culture Jamming & Play: Research-Creation approaches to cultivating Internet counter-publics"

The site features:
- Main landing page with project overview
- Three case study pages (Welcome to the Metaverse, The Education of Ursula, BrainRot Revolution)
- Shared CSS file for easy styling updates
- Brutalist web design aesthetic with courier font and bold borders

## Files Included

### For Deployment (use these for your actual website):
- `index.html` - Main landing page
- `metaverse.html` - Welcome to the Metaverse case study
- `ursula.html` - The Education of Ursula case study
- `brainrot.html` - BrainRot Revolution case study
- `styles.css` - Shared stylesheet for all pages

### For Preview (inline styles for viewing in tools that don't load external CSS):
- `index-inline.html`
- `metaverse-inline.html`
- `ursula-inline.html`
- `brainrot-inline.html`

## Setup Instructions

### Option 1: Visual Studio Code (Recommended)

1. **Download and Install VS Code**
   - Go to https://code.visualstudio.com
   - Download for macOS
   - Drag to Applications folder

2. **Install Live Server Extension**
   - Open VS Code
   - Click Extensions icon in left sidebar (or press Cmd+Shift+X)
   - Search for "Live Server" by Ritwick Dey
   - Click Install

3. **Open Your Project**
   - File → Open Folder
   - Select the folder containing your HTML files
   - You'll see all files in the left sidebar

4. **Launch Live Preview**
   - Right-click on `index.html` in the sidebar
   - Select "Open with Live Server"
   - Your default browser will open showing the site
   - **Any changes you make will auto-refresh in the browser when you save!**

5. **Edit Files**
   - Click any file in the sidebar to edit
   - Save with Cmd+S
   - Watch the browser automatically update

### Option 2: Sublime Text

1. **Download and Install**
   - Go to https://www.sublimetext.com
   - Download for macOS
   - Drag to Applications folder

2. **Open Your Project**
   - File → Open Folder
   - Select the folder with your HTML files

3. **Preview in Browser**
   - Right-click any HTML file in Finder
   - Open With → Your preferred browser (Safari, Chrome, Firefox)
   - Refresh browser (Cmd+R) after making changes

### Option 3: TextEdit (Simplest, Already on Your Mac)

1. **Configure TextEdit**
   - Open TextEdit
   - TextEdit → Preferences
   - Under "New Document" tab: Select "Plain text"
   - Under "Open and Save" tab: Uncheck "Add .txt extension"

2. **Open Files**
   - File → Open
   - Select any HTML file

3. **Preview in Browser**
   - Right-click the HTML file in Finder
   - Open With → Your browser
   - Refresh browser after making changes

## File Structure

When you deploy, make sure all files are in the same directory:

```
your-website-folder/
├── index.html
├── metaverse.html
├── ursula.html
├── brainrot.html
└── styles.css
```

## Making Changes

### To Update Styles
- Edit `styles.css`
- Changes will apply to ALL pages automatically
- This is why using external CSS is better than inline styles!

### To Update Content
- Edit the individual HTML files
- The navigation links between pages should work as long as files are in the same folder

### Common Edits You Might Want to Make

1. **Change Colors**
   - Open `styles.css`
   - Look for color codes like `#111` (black) or `#fafafa` (off-white)
   - Replace with your preferred colors

2. **Update Contact Info**
   - Open `index.html`
   - Look for the footer section
   - Change email and other details

3. **Add Video IDs**
   - Each case study has placeholder text: `YOUR_VIDEO_ID`
   - Replace with actual Vimeo video IDs when ready

4. **Change Navigation Links**
   - The dropdown menu is in the `<nav>` section of `index.html`
   - Update file names if you rename any pages

## Link Styling Demo

The metaverse.html page includes a working example of the link styling:
- Underlined links with 2px thickness
- Hover effect: inverts to white text on black background
- Smooth transition animation

To add more links with this styling, just use regular `<a>` tags:
```html
<a href="https://example.com">Link text</a>
```

## Tips for VS Code

- **Find and Replace Across All Files**: Cmd+Shift+F
- **Multi-cursor Editing**: Hold Option and click multiple places
- **Format Document**: Right-click → Format Document (makes HTML prettier)
- **Preview Side-by-Side**: Drag browser window next to VS Code window

## Need Help?

- VS Code docs: https://code.visualstudio.com/docs
- HTML reference: https://developer.mozilla.org/en-US/docs/Web/HTML
- CSS reference: https://developer.mozilla.org/en-US/docs/Web/CSS

## Next Steps

1. Set up your editor of choice
2. Preview the site locally
3. Make any content updates you need
4. Add your actual video IDs and images
5. Test all navigation links
6. Deploy to your web host when ready

---

Built with ☞ and brutalist web energy
