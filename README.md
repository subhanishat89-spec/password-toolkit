# 🔐 Password Security Toolkit

A privacy-first password toolkit built with vanilla HTML, CSS, and JavaScript. Check how strong a password is, find out whether it has appeared in a known data breach, and generate strong random passwords or passphrases. Everything runs in your browser, with no frameworks, no backend, and no sign-up.

🔗 **Live Demo:** [subhanishat89-spec.github.io/password-toolkit](https://subhanishat89-spec.github.io/password-toolkit/)

![Screenshot](screenshot.png)

## ✨ Features

- 📊 **Strength checker:** entropy estimate, strength meter, requirements checklist, and score breakdown
- 🧠 **Pattern detection:** repeats, sequences (`abc`, `1234`), keyboard runs (`qwerty`), years, dictionary words, and common passwords, including leetspeak variants like `p@ssw0rd`
- 💡 **Personalized tips** on how to improve a weak password
- ⏱️ **Crack-time estimates** for offline (10 billion guesses/s) and online (100 guesses/s) attacks
- 🕵️ **Breach check** with the [Have I Been Pwned](https://haveibeenpwned.com/API/v3#PwnedPasswords) API using **k-anonymity**: only the first 5 characters of the SHA-1 hash are sent
- 🎲 **Secure generator** using `crypto.getRandomValues` with rejection sampling (no modulo bias):
  - Random passwords with custom length, character types, and an option to avoid look-alike characters
  - Word-based passphrases with adjustable word count, separator, capitalization, and optional number
- 📋 One-click copy and a "Check this" shortcut that sends a generated password to the checker
- 🌙 Dark mode, responsive layout, and screen-reader support

## 🧠 How It Works

**Entropy:** estimated as `effective length × log₂(character pool size)`. The effective length is reduced for repeated characters, sequences, keyboard patterns, years, and dictionary words. Very common passwords are capped at a very low score.

**K-anonymity (leak check):** the browser hashes the password with SHA-1 (Web Crypto API), sends only the first 5 hex characters to the API, and matches the returned suffixes locally. The password and the full hash never leave the device.

**Generation:** passwords include at least one character of each selected type and are shuffled with a Fisher–Yates shuffle driven by secure randomness. Passphrase strength is `words × log₂(word list size)`, which assumes the attacker knows the word list.

## 🛠️ Tech Stack

HTML5 · CSS3 (custom properties, grid, dark mode) · JavaScript (ES6+) · Web Crypto API · Fetch API

## ⚠️ Limitations

Entropy and crack-time values are estimates for comparing passwords. Real attackers use more advanced strategies. Use a unique password for every account and a password manager. Never type real passwords into any online tool; use test passwords when demoing.

## 🚀 Run Locally

```bash
git clone https://github.com/subhanishat89-spec/password-toolkit.git
cd password-toolkit
```

Open `index.html` in your browser. The breach check needs an internet connection.

## 🔮 Future Improvements

- 📚 Larger word list (e.g., EFF diceware)
- 🔍 Smarter pattern detection (names, dates, full dictionary matching)
- 📈 Visual entropy breakdown chart

## 👤 Author

**Nishat Subha** · [@subhanishat89-spec](https://github.com/subhanishat89-spec)
