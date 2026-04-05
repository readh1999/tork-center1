# 🔧 Tork Center — نظام إدارة مركز السيارات

<div align="center">
  <img src="https://img.shields.io/badge/Version-2.0-red?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Platform-Desktop%20%7C%20Web-blue?style=for-the-badge" />
  <img src="https://img.shields.io/badge/Language-Arabic%20%2F%20EN-green?style=for-the-badge" />
</div>

---

## 📋 وصف النظام

نظام إدارة متكامل لمراكز صيانة سيارات **Infiniti / Nissan**، مبني بتقنية HTML/JS خالصة — يعمل مباشرة من المتصفح بدون خوادم.

---

## ✨ المميزات

| الميزة | الوصف |
|--------|-------|
| 🧾 **الفواتير** | فواتير نقدي / دين / تقسيط / صيانة مع طباعة وصل مبيعات |
| 🚗 **Q50 Invoice Art** | صورة إنفينيتي Q50 معدلة على وصل البيع |
| 🔩 **المخزون** | إدارة قطع الغيار مع تنبيهات المخزون المنخفض |
| 👥 **الزبائن** | بيانات الزبائن وسياراتهم كاملة |
| 💰 **الصندوق** | تتبع الإيرادات والمصروفات |
| 📊 **التقارير** | تقارير مبيعات / أرباح / ديون / مخزون |
| 🌙☀️ **المظهر** | وضع ليلي وصباحي مع حفظ تلقائي |
| 💾 **نسخ احتياطي** | تصدير تلقائي كل يومين |
| 🔥 **Firebase** | دعم Firebase للعمل متعدد الفروع |
| 🛠️ **لوحة المطور** | إعدادات خاصة بالمطور فقط |

---

## 🚀 تشغيل على سطح المكتب (Electron)

### المتطلبات
- [Node.js](https://nodejs.org/) (v16+)
- npm

### خطوات التثبيت

```bash
# 1. انسخ المستودع
git clone https://github.com/YOUR_USERNAME/tork-center.git
cd tork-center

# 2. ثبّت Electron
npm init -y
npm install electron --save-dev

# 3. أنشئ main.js
# (راجع الملف في المستودع)

# 4. شغّل التطبيق
npm start
```

### ملف `main.js` لـ Electron

```javascript
const { app, BrowserWindow } = require('electron');
const path = require('path');

function createWindow() {
  const win = new BrowserWindow({
    width: 1400,
    height: 900,
    minWidth: 1100,
    minHeight: 700,
    icon: path.join(__dirname, 'icon.png'),
    webPreferences: {
      nodeIntegration: false,
      contextIsolation: true,
    },
    titleBarStyle: 'hidden',
    frame: true,
    title: 'Tork Center — نظام الإدارة'
  });
  win.loadFile('tork-center.html');
  win.setMenuBarVisibility(false);
}

app.whenReady().then(createWindow);
app.on('window-all-closed', () => { if (process.platform !== 'darwin') app.quit(); });
app.on('activate', () => { if (BrowserWindow.getAllWindows().length === 0) createWindow(); });
```

### ملف `package.json`

```json
{
  "name": "tork-center",
  "version": "2.0.0",
  "description": "Tork Center — Car Service Management System",
  "main": "main.js",
  "scripts": {
    "start": "electron .",
    "build": "electron-builder"
  },
  "devDependencies": {
    "electron": "^28.0.0",
    "electron-builder": "^24.0.0"
  },
  "build": {
    "appId": "com.torkcenter.app",
    "productName": "Tork Center",
    "directories": { "output": "dist" },
    "win": {
      "target": "nsis",
      "icon": "icon.ico"
    },
    "linux": {
      "target": "AppImage"
    }
  }
}
```

---

## 🌐 تشغيل على GitHub Pages (ويب)

1. ارفع الملف `tork-center.html` إلى مستودعك
2. اذهب إلى **Settings → Pages**
3. اختر **Branch: main** ثم Save
4. الرابط سيكون: `https://YOUR_USERNAME.github.io/tork-center/tork-center.html`

---

## 🔐 بيانات الدخول

| النوع | اسم المستخدم | كلمة المرور | الصلاحية |
|-------|-------------|-------------|---------|
| المطور | `readh` | `readh1999` | كاملة + لوحة المطور |
| المدير | `admin` | `admin123` | كاملة |

> ⚠️ **مهم:** غيّر كلمة مرور المدير فور التثبيت.

---

## 🛠️ لوحة المطور (Developer Panel)

متاحة فقط عند الدخول بحساب **readh**:

- **تدوير كلمة المرور التلقائي**: تغيير رموز جميع المستخدمين كل 4 أشهر إلى `1234567`
- **معلومات النظام**: إحصائيات البيانات وحجم التخزين
- **إدارة النسخ الاحتياطي التلقائي**: كل يومين تلقائياً

---

## 📁 هيكل الملفات

```
tork-center/
├── tork-center.html     ← النظام الكامل
├── main.js              ← Electron entry point
├── package.json         ← Node.js config
├── README.md            ← هذا الملف
└── icon.png             ← أيقونة التطبيق (اختياري)
```

---

## 📄 الرخصة

للاستخدام الخاص — Tork Center © 2025
