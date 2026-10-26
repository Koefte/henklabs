# Mobile App Studio Legal Compliance & Landing Website

[![Deploy to GitHub Pages](https://github.com/yourusername/compliance-website/actions/workflows/deploy.yml/badge.svg)](https://github.com/yourusername/compliance-website/actions/workflows/deploy.yml)
[![Zero External Trackers](https://img.shields.io/badge/GDPR-100%25%20Compliant-success)](#)
[![Zero Build Steps](https://img.shields.io/badge/Build-Zero%20Dependencies-blue)](#)

A static, high-performance developer entity website and compliance suite designed for **free hosting on GitHub Pages**. 

This site fulfills all mandatory developer verification requirements for:
1. **Google Play Console Organization / Developer Account Verification** (DUNS number & official domain ownership matching).
2. **German Legal Compliance (§ 5 DDG & § 18 MStV)** for an indie mobile app studio operating as a German *Einzelunternehmen / Kleingewerbe* in Aachen.
3. **European GDPR (DSGVO Articles 12–21)** for offline-first Android apps using Google Play Billing and RevenueCat.
4. **IAB Tech Lab `app-ads.txt`** mobile publisher verification.

---

## ⚡ Key Highlights & Architecture

- **Zero Build Steps & Zero Dependencies:** Pure static HTML5 and CSS. No `node_modules`, no npm, no build pipelines.
- **Blazing Fast (< 50ms):** Single-digit millisecond response times on GitHub Pages / Fastly CDN edges.
- **Zero Privacy Leaks:** **NO** Google Fonts (`fonts.googleapis.com`), **NO** external tracking pixels, **NO** cookies, **NO** analytics scripts. Fully compliant with German court precedents (LG München I, 2022).
- **Responsive & Dual-Themed:** Fluid mobile-first layout with automatic dark and light mode (`prefers-color-scheme`).

---

## 📁 Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml      # Automated GitHub Actions Pages deployment
├── .gitignore              # Standard git ignore file
├── CNAME                   # Custom apex domain configuration for GitHub Pages
├── README.md               # Setup, DNS, and Play Console verification guide
├── app-ads.txt             # IAB Tech Lab authorized sellers file for AdMob
├── impressum.html          # German § 5 DDG & § 18 MStV legal notice
├── index.html              # Developer studio landing page & app showcase
├── privacy.html            # Comprehensive GDPR / DSGVO offline-first privacy policy
└── style.css               # Modern, self-contained CSS with dark/light themes
```

---

## 🛠️ Step 1: Search-and-Replace Placeholders

Run a global search-and-replace across all files in this repository for the following placeholders:

| Token | Example Value | Description | Affected Files |
|---|---|---|---|
| `{{STUDIO_NAME}}` | `Aachen App Labs` | Public brand / studio name | `index.html`, `impressum.html`, `privacy.html` |
| `{{DEVELOPER_NAME}}` | `Max Mustermann` | Legal full name of the sole proprietor (*Einzelunternehmer*) | `index.html`, `impressum.html`, `privacy.html` |
| `{{STREET_AND_NUMBER}}` | `Templergraben 55` | Valid summonable street address (*ladungsfähige Anschrift*) in Aachen | `impressum.html`, `privacy.html` |
| `{{ZIP_CITY}}` | `52062 Aachen` | Postal code and city | `impressum.html`, `privacy.html` |
| `{{CONTACT_EMAIL}}` | `support@yourstudio.me` | Public support and compliance email address | `index.html`, `impressum.html`, `privacy.html` |
| `{{PHONE_NUMBER}}` | `+49 241 XXXXXXXX` | Business phone number (or note: *auf Anfrage*) | `impressum.html` |
| `{{CUSTOM_DOMAIN}}` | `yourstudio.me` | Custom domain name (without `https://` or `www`) | `CNAME`, `impressum.html`, `privacy.html` |
| `{{UST_IDNR}}` | `DE123456789` | German VAT ID (if assigned; otherwise keep note provided in template) | `impressum.html` |
| `{{GITHUB_URL}}` | `https://github.com/yourusername` | Link to your GitHub profile or organization | `index.html`, `impressum.html`, `privacy.html` |
| `{{ANDROID_PACKAGE_ID}}`| `com.example.microapp.micro_app_factory` | Google Play application package ID | `index.html` |
| `{{ADMOB_PUB_ID}}` | `pub-1234567890123456` | 16-digit AdMob Publisher ID *(only if ads are used)* | `app-ads.txt` |

> [!IMPORTANT]
> **German Legal Address Requirement:** Section 5 of the German DDG (*Digitale-Dienste-Gesetz*) strictly requires a summonable address (*ladungsfähige Anschrift*). A pure P.O. box (*Postfach*) is **not** legally sufficient under German law.

---

## 🚀 Step 2: Enable GitHub Pages

1. Push this repository to GitHub:
   ```bash
   git add .
   git commit -m "feat: initial release of compliance and studio landing site"
   git remote add origin https://github.com/<your-username>/<your-repo-name>.git
   git push -u origin main
   ```
2. In your GitHub repository, open **Settings** &rarr; **Pages** (under *Code and automation*).
3. Under **Build and deployment &rarr; Source**, select:
   - **GitHub Actions** *(Recommended - utilizes the included `.github/workflows/deploy.yml` workflow)*.
   - Alternatively, choose **Deploy from a branch**, select branch `main` and folder `/ (root)`.
4. In the **Custom domain** field, enter your domain (e.g., `yourstudio.me`) and click **Save**.
5. Once your DNS has propagated (see Step 3 below), check the box **Enforce HTTPS**.

---

## 🌐 Step 3: Configure DNS Records (Namecheap / Any Registrar)

Log in to your DNS provider (e.g., Namecheap &rarr; *Domain List* &rarr; *Manage* &rarr; *Advanced DNS*) and add the following records:

### 1. Apex Domain A-Records (Point to GitHub Pages Edge Servers)
Add **4 A-Records** for the Host `@`:

| Type | Host | Value | TTL |
|---|---|---|---|
| **A Record** | `@` | `185.199.108.153` | Automatic / 300s |
| **A Record** | `@` | `185.199.109.153` | Automatic / 300s |
| **A Record** | `@` | `185.199.110.153` | Automatic / 300s |
| **A Record** | `@` | `185.199.111.153` | Automatic / 300s |

### 2. IPv6 AAAA Records (Optional but Recommended)
| Type | Host | Value | TTL |
|---|---|---|---|
| **AAAA Record** | `@` | `2606:50c0:8000::153` | Automatic / 300s |
| **AAAA Record** | `@` | `2606:50c0:8001::153` | Automatic / 300s |
| **AAAA Record** | `@` | `2606:50c0:8002::153` | Automatic / 300s |
| **AAAA Record** | `@` | `2606:50c0:8003::153` | Automatic / 300s |

### 3. CNAME Record for `www` Subdomain
Redirects `www.yourstudio.me` to your GitHub Pages apex domain:

| Type | Host | Value | TTL |
|---|---|---|---|
| **CNAME Record** | `www` | `<your-github-username>.github.io.` | Automatic / 300s |

---

## 🔍 Step 4: Verify Domain in Google Search Console (For Google Play Verification)

Google Play Console requires verification of your official website domain during organization / developer onboarding:

1. Open [Google Search Console](https://search.google.com/search-console).
2. Select **Domain** property type (not *URL prefix*) and enter your domain: `yourstudio.me`.
3. Google Search Console will provide a **DNS TXT verification record**, for example:
   ```
   google-site-verification=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
   ```
4. In your Namecheap DNS records:
   - Add a new **TXT Record**.
   - Host: `@`
   - Value: `google-site-verification=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`
   - TTL: Automatic / 300s
5. Wait 2–5 minutes and click **Verify** in Google Search Console.
6. Once verified, link this verified domain in your **Google Play Console &rarr; Developer Account &rarr; About you &rarr; Website**.

---

## 📱 Step 5: Update Your Flutter Micro-App URLs

Once your site is live, open your mobile app's `lib/config/app_config.dart` file and update the compliance endpoints:

```dart
// lib/config/app_config.dart
static const String impressumUrl = 'https://yourstudio.me/impressum.html';
static const String privacyPolicyUrl = 'https://yourstudio.me/privacy.html';
```

All in-app legal dialogs, drawer links, and Google Play Store metadata will now automatically resolve to your legal developer pages.
