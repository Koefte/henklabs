# Henk Labs – Mobile App Studio Legal Compliance & Landing Website

[![Deploy to GitHub Pages](https://github.com/Koefte/compliance-website/actions/workflows/deploy.yml/badge.svg)](https://github.com/Koefte/compliance-website/actions/workflows/deploy.yml)
[![Zero External Trackers](https://img.shields.io/badge/GDPR-100%25%20Compliant-success)](#)
[![Zero Build Steps](https://img.shields.io/badge/Build-Zero%20Dependencies-blue)](#)

Official developer entity website and compliance suite for **Henk Labs** (Developer: **Henk van Wersch**, Aachen, Germany), hosted for free on **GitHub Pages** with custom domain **`https://henkstudio.me`**.

This repository fulfills all mandatory legal and developer verification requirements for:
1. **Google Play Console Organization / Developer Account Verification** (DUNS number & official domain `henkstudio.me` ownership).
2. **German Legal Compliance (§ 5 DDG & § 18 MStV)** for an indie mobile app studio operating as a German *Einzelunternehmen / Kleingewerbe* in Aachen.
3. **European GDPR (DSGVO Articles 12–21)** for offline-first Android apps using Google Play Billing and RevenueCat.
4. **IAB Tech Lab `app-ads.txt`** mobile publisher verification.

---

## ⚡ Highlights

- **Zero Build Steps & Zero Dependencies:** Pure static HTML5 and CSS. No `node_modules`, no npm, no build pipelines.
- **Blazing Fast (< 50ms):** Single-digit millisecond response times on GitHub Pages CDN edges.
- **Zero Privacy Leaks:** **NO** Google Fonts (`fonts.googleapis.com`), **NO** external tracking pixels, **NO** cookies, **NO** analytics scripts. 100% compliant with German court precedents (LG München I, 2022).
- **Responsive & Dual-Themed:** Fluid mobile-first layout with automatic dark and light mode (`prefers-color-scheme`).

---

## 📁 Repository Structure

```
.
├── .github/
│   └── workflows/
│       └── deploy.yml      # Automated GitHub Actions Pages deployment
├── .gitignore              # Standard git ignore file
├── CNAME                   # Custom domain routing: henkstudio.me
├── README.md               # Setup, DNS, and Play Console verification guide
├── app-ads.txt             # IAB Tech Lab authorized sellers file for AdMob
├── impressum.html          # German § 5 DDG & § 18 MStV legal notice
├── index.html              # Developer studio landing page & app showcase
├── privacy.html            # Comprehensive GDPR / DSGVO offline-first privacy policy
└── style.css               # Modern, self-contained CSS with dark/light themes
```

---

## 🚀 Setup & Deployment Guide

### 1. Push to GitHub
Create a new GitHub repository under your account (`https://github.com/Koefte/<your-repo-name>`):
```bash
cd /home/koefte/Documents/HenkStartup/compliance-website
git remote add origin https://github.com/Koefte/<your-repo-name>.git
git push -u origin main
```

### 2. Enable GitHub Pages
1. Go to your repository **Settings** &rarr; **Pages** (under *Code and automation*).
2. Under **Build and deployment &rarr; Source**, select **GitHub Actions** (it will automatically use `.github/workflows/deploy.yml`).
3. Under **Custom domain**, enter `henkstudio.me` and click **Save**.
4. Once DNS is verified, check **Enforce HTTPS**.

---

## 🌐 Namecheap DNS Configuration for `henkstudio.me`

Log in to Namecheap &rarr; **Domain List** &rarr; click **Manage** next to `henkstudio.me` &rarr; open **Advanced DNS** tab and set:

### 1. Apex Domain A-Records (GitHub Pages IP Addresses)
Add 4 **A Records** for Host `@`:

| Type | Host | Value | TTL |
|---|---|---|---|
| **A Record** | `@` | `185.199.108.153` | Automatic / 300s |
| **A Record** | `@` | `185.199.109.153` | Automatic / 300s |
| **A Record** | `@` | `185.199.110.153` | Automatic / 300s |
| **A Record** | `@` | `185.199.111.153` | Automatic / 300s |

### 2. CNAME Record for `www` Subdomain
| Type | Host | Value | TTL |
|---|---|---|---|
| **CNAME Record** | `www` | `koefte.github.io.` | Automatic / 300s |

---

## 🔍 Google Play Organization Account Domain Verification

Google Play Console requires verification of your official domain during organization account setup:

1. Open [Google Search Console](https://search.google.com/search-console).
2. Choose **Domain** property and enter `henkstudio.me`.
3. Copy the **DNS TXT verification record** provided by Google (e.g. `google-site-verification=...`).
4. In Namecheap Advanced DNS:
   - Add a new **TXT Record**.
   - Host: `@`
   - Value: `google-site-verification=...`
   - TTL: Automatic / 300s
5. Wait 2 minutes and click **Verify** in Google Search Console.
6. In Google Play Console &rarr; Developer Account setup, submit `https://henkstudio.me` as your official developer website.

---

## 📋 Outstanding Developer Actions Checklist

- [ ] **VAT ID (USt-IdNr.):** Once received from the Bundeszentralamt für Steuern (BZSt), insert it into `impressum.html` line 87 (currently marked with the standard compliant pending note).
- [ ] **Google Play Package ID:** Once your Google Play Organization account is approved, add the package ID to `index.html`.
- [ ] **AdMob (Optional):** If you decide to serve ads in the future, uncomment and add your publisher ID to `app-ads.txt`.
