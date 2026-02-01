---
{"dg-publish":true,"permalink":"/hosting-your-static-wiki-on-the-internet-1/"}
---


## **Should You Pay for Hosting?** 

### **Free is Great at First** 
- For a **personal or small project**, free static hosting is more than enough.
- These platforms handle bandwidth and uptime for you.
- Great for learning!

### **Upgrade Later If Needed**
- If your wiki grows to thousands of pages, or you want to add **search**, logins, edit-from-browser, etc., you might want a paid or more professional solution. Until then, free static hosting is perfect!
- Even big-ish projects can live on free plans for a long time.
- If you ever want to go bigger (custom search, user accounts, databases), you could look at [paid plans] or [more complex solutions] (like paid Vercel/Netlify, DigitalOcean, or running a [[MediaWiki\|MediaWiki]] instance on a [[VPS\|VPS]]).

**Tip:** If you want features like search, consider using JavaScript-based search libraries (like [Lunr.js](https://lunrjs.com/)) which work client-side on static sites.

### The Core Idea: Start Simple, Scale as Needed

The paragraph describes a **progression of complexity and cost** for hosting a wiki.

1. **Stage 1 (Simple & Free):** A static site generator (like MkDocs, [[Jekyll\|Jekyll]], Docusaurus) creates HTML files from your notes. You host these files for free on platforms like [[GitHub Pages\|GitHub Pages]], GitLab Pages, or [[Cloudflare Pages\|Cloudflare Pages]]. It's fast, secure, and costs nothing. Perfect for a personal knowledge base.
2. **Stage 2 (More Features, Low Cost):** When you need **search, user logins, or a browser-based editor**, you outgrow static files. You might use the [paid "Pro" tiers] of Vercel/Netlify (which add [[serverless function\|serverless function]]s) or simpler [hosted wiki services].
3. **Stage 3 (Full Control, High Complexity):** When you need maximum power and customization—like a full **database, user permissions, plugins, and complex search**—you move to a [[self-hosted solution\|self-hosted solution]]. This is where **"running a MediaWiki instance on a VPS"** comes in.

### Running a MediaWiki instance on a VPS

This is the most powerful and hands-on option. Let's define the terms:

* **[[MediaWiki\|MediaWiki]]:** The [[open-source software\|open-source software]] that powers **[[Wikipedia\|Wikipedia]]**. It's a full-featured, database-driven [[wiki engine\|wiki engine]] written in [[PHP\|PHP]].
 * **Features:** User accounts with permissions, [[rich-text editor\|rich-text editor]], full revision history, powerful search, categories, templates, thousands of extensions, and a massive community.
* **[[Virtual Private Server (VPS)\|Virtual Private Server (VPS)]]:** A slice of a physical server that acts like your own dedicated computer in the cloud. You have full control ([[root access\|root access]]) to install any software you want. Providers include [[DigitalOcean\|DigitalOcean]], Linode, [[Vultr\|Vultr]], AWS Lightsail, and Hetzner.
* **Instance:** Simply another word for a "[[virtual machine\|virtual machine]]" or "server" running the software. So, a "MediaWiki instance" is one [[installation\|installation]] of the MediaWiki software running on a [[server\|server]].

#### What It Actually Means to Run This:

You are becoming your own [[system administrator\|system administrator]]. Here’s what you are responsible for: 

1. **Renting the Server:** You sign up with a VPS provider, choose an operating system (usually Linux), and rent a server (e.g., $5-10/month for a small wiki).
2. **Installing the "Stack":** You manually install and configure all the required software:
  * **[[Web server\|Web server]]:** (e.g., Apache or [[Nginx\|Nginx]]) to deliver web pages.
  * **Database:** (e.g., [[MySQL\|MySQL]] or MariaDB) to store all your pages, users, and history.
  * **PHP:** The programming language MediaWiki is built on.
  * **MediaWiki itself:** Download, configure, and run the [[installation wizard\|installation wizard]].
1. **Ongoing Maintenance:**
  * **Security:** Applying operating system updates, software patches, configuring firewalls, and setting up SSL certificates (HTTPS).
  * **Backups:** Regularly backing up your database and wiki files to another location.
  * **Updates:** Upgrading MediaWiki to new versions for features and security.
  * **Monitoring:** Ensuring the server stays online and performs well.
  * **Troubleshooting:** Fixing any errors that occur.

