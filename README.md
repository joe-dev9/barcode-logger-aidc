# 📦 Barcode Logger AIDC System

A smart, real-time barcode scanning system for Zebra TC72 that logs, visualizes, and alerts on every scan using open technologies.

## ✅ Features

## ✅ Features

- 🔍 Scan barcodes with Zebra TC72 browser
- 🌐 Send scans to a Flask server via HTTP POST
- 💽 Save locally: `barcodes.txt` and `barcodes.db` (SQLite)

  ![TXT Log](/barcode-logger-aidc/blob/main/barcodes-txt.png)
  ![SQLite DB](screenshots/barcodes-db.png)

- ☁️ Sync to Firebase Firestore for cloud storage
- 📊 Real-time dashboard in any browser (HTML + Firebase)

  ![Dashboard](screenshots/dashboard-live.png)

- 📧 Email alerts on every scan via SMTP

  ![Email Alert](screenshots/email-alert.png)

- 🔁 Auto-start on boot with `systemd`
- 💡 Designed for AIDC, edge computing, and innovation labs

---

## 🏗️ System Architecture

```
[TC72 Scanner]
    |
    | HTTP POST
    v
[Flask Server (Raspberry Pi/Ubuntu)]
    |
    |---> Save to barcodes.txt
    |---> Save to SQLite (barcodes.db)
    |---> Push to Firebase Firestore
    |
    +---> Send email alert (SMTP)
    |
    +---> Real-time Dashboard (Firebase JS SDK)
```

---

## 💡 Use Cases

- 🏥 Healthcare: Scan patient labels and track in real-time
- 🏭 Manufacturing: Monitor part flow through assembly
- 📦 Logistics: Alert on high-value item scans

---

## 📸 Demo Screenshots

- TC72 scan input form  
- Dashboard table + chart  
- Live Firestore backend  
- Email alert (Gmail)  
- Systemd auto-start  

*(See `/screenshots` folder)*

---

## 🚀 Getting Started

```bash
git clone https://github.com/joe-dev9/barcode-logger-aidc.git
cd barcode-logger-aidc
```

### 1. Install dependencies

```bash
sudo apt update
sudo apt install python3-flask python3-pip sqlite3
pip3 install firebase-admin
```

### 2. Configure

- Replace `gd-testproject-firebase-adminsdk-xxxx.json` with your Firebase Admin SDK key  
- Edit the `barcode_server.py` SMTP section with your email credentials

### 3. Run the server

```bash
python3 barcode_server.py
```

### 4. Start the dashboard

```bash
python3 -m http.server 8080
# Then visit: http://<server-ip>:8080/dashboard.html
```

---

## 📂 File Structure

```
barcode-logger-aidc/
├── barcode_server.py       # Main Flask server
├── dashboard.html          # Realtime dashboard (JS + Firebase)
├── barcodes.db             # SQLite data
├── barcodes.txt            # Local log file
├── README.md
├── screenshots/            # Demo images
└── service/                # barcode_server.service (systemd unit file)
```

---

## 📅 Roadmap

- 🔗 Sync to BigQuery for advanced analytics  
- 🤖 AI anomaly detection (rare scans, outliers)  
- 🛡️ Firebase security rules  
- 📤 Firebase Hosting for public dashboard  
- 📱 Optional Android wrapper (PWA)

---

## 👨‍💻 Author

**Giuseppe Deliso**  
[LinkedIn](https://www.linkedin.com/in/giuseppedeliso) · [GitHub](https://github.com/joe-dev9)

---

## 📄 License

MIT — open-source and community-first.

