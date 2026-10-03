# PULSE 4.1 — Global Seismic & Volcanic Intelligence

**رصد الزلازل والبراكين العالمي | Real-time earthquake & volcano monitoring**

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![PWA](https://img.shields.io/badge/PWA-ready-57e3a0)
![Vanilla JS](https://img.shields.io/badge/Vanilla-JS-f5bd5b)
![No API keys](https://img.shields.io/badge/API%20keys-none-blue)
![Languages](https://img.shields.io/badge/Languages-AR%20%7C%20EN-lightgrey)

[العربية](#-العربية) · [English](#-english) · [Developer / المطور](#-developer--المطور) · [License](#-license--الترخيص)

---

## 🇸🇾 العربية

### نظرة عامة
**PULSE 4.1** تطبيق ويب تقدّمي (PWA) في ملف HTML واحد، لمراقبة النشاط الزلزالي والبركاني في العالم لحظة بلحظة. يعرض الخريطة بواجهة كاملة، وأسفلها آخر الأحداث اللحظية بكامل بياناتها، مع تحليلات وتنبيهات صوتية ومراقبة للمناطق. لا يحتاج إلى مفاتيح API ولا إلى خادم.

### المزايا
- **خريطة بواجهة كاملة** (Leaflet) مع تجميع الأحداث (Marker Cluster) ونبضات متحركة تتناسب مع قوة الزلزال.
- **آخر المستجدات اللحظية** أسفل الخريطة: لكل حدث القوة، نوع المقدار، الموقع، الوقت، آخر تحديث، الإحداثيات، العمق، التسونامي، عدد من شعروا به، MMI/CDI، التنبيه، المحطات، Gap/RMS/Dmin، الأهمية، الحالة، النوع، المصدر، الطاقة المقدرة، والمعرّف، مع رابط USGS وزر «عرض على الخريطة».
- **ثلاث طبقات للخريطة:** داكنة، شوارع، قمر صناعي، مع طبقة البراكين وخريطة حرارية.
- **تبويبات التحليل:**
  - نظرة عامة: مؤشرات سريعة وأحدث الأحداث.
  - الزلازل: فلترة حسب القوة والعمق وإعادة تشغيل الأحداث (Replay).
  - التحليلات: توزيع المقادير وملاحظات علمية.
  - الخط الزمني.
  - التجمعات (Clusters): مؤشر حسابي من PULSE (3 أحداث أو أكثر ضمن 50 كم و72 ساعة).
  - البراكين: البراكين ذات النشاط المرتفع من USGS.
  - Region Watch: مراقبة منطقة بنطاق (كم) حول موقعك أو أي نقطة.
  - التنبيهات.
- **نظام تنبيهات:** إشعارات المتصفح، صوت، اهتزاز، ولافتة داخل التطبيق. عتبة المقدار الافتراضية 5.0، وتُرسل للأحداث الحديثة (آخر 15 دقيقة). تنبيهات للبراكين ذات الحالة الحمراء/البرتقالية أو الثورانية.
- **ثنائي اللغة:** العربية (RTL) والإنجليزية (LTR) مع حفظ اللغة المختارة.
- **بحث عن الأماكن** (Nominatim/OpenStreetMap) وتحديد موقعك.
- **يعمل مع ضعف الاتصال:** يحفظ آخر بيانات محلياً، ويتحول تلقائياً إلى خريطة SVG احتياطية إذا تعذر تحميل الخرائط.
- **تقدير الطاقة الزلزالية:** `log10(E[J]) = 1.5 × M + 4.8` (تقدير تجريبي تقريبي).

### طريقة الاستخدام
1. افتح التطبيق: تظهر الخريطة بملء الشاشة. اضغط أي أيقونة زلزال لعرض تفاصيلها واللوحة السفلية.
2. اضغط **«آخر الأحداث ⌄»** أو مرّر للأسفل لقراءة المستجدات اللحظية بكامل البيانات. اضغط **«عرض على الخريطة»** للانتقال إلى الحدث.
3. أدوات الخريطة (يسار): ⌖ موقعي · ⛶ إظهار كل الأحداث · ◌ خريطة حرارية · ☷ الطبقات · 🌋 البراكين.
4. زر **LIVE** يوقف التحديث التلقائي أو يستأنفه. يتحدث موجز الزلازل كل 45 ثانية، والبراكين كل 10 دقائق.
5. زر **EN / AR** يبدّل اللغة. زر 🔔 يفتح إعدادات التنبيه.
6. لتفعيل التنبيهات: اضغط «تفعيل التنبيهات الآن» (مطلوب لتشغيل الصوت في المتصفحات)، ثم اضبط عتبة المقدار وحفظ.
7. لمراقبة منطقتك: تبويب **Region Watch** ← «موقعي» ← حدّد النطاق بالكيلومتر.

### التثبيت والنشر
لا يحتاج بناءً أو تبعيات. ضع الملفات في مجلد واحد:

```
index.html              # التطبيق
manifest.webmanifest    # بيان PWA
sw.js                   # Service Worker (اختياري للعمل دون اتصال)
```

- **محلياً:** `python3 -m http.server 8080` ثم افتح `http://localhost:8080`.
- **Codeberg Pages:** ارفع الملفات إلى مستودع `pages` (أو الفرع المخصص) وفعّل الصفحات.
- يجب تقديم التطبيق عبر **HTTPS** (أو localhost) لتعمل الإشعارات وتحديد الموقع وService Worker.

### مصادر البيانات والمكتبات
| المصدر | الاستخدام |
|---|---|
| USGS Earthquake Hazards Program | موجز الزلازل (`all_day.geojson`) |
| USGS Volcano Hazards (HANS) | البراكين ذات النشاط المرتفع |
| OpenStreetMap / Nominatim | البحث الجغرافي وطبقة الشوارع |
| CARTO / Esri | طبقتا الخريطة الداكنة والقمر الصناعي |
| Leaflet 1.9.4 (BSD-2-Clause) | محرك الخرائط |
| Leaflet.markercluster 1.5.3 (MIT) | تجميع العلامات |

### إخلاء مسؤولية
PULSE **لا يتنبأ بالزلازل** ولا يستبدل التحذيرات الرسمية. يعرض بيانات المصادر الرسمية بعد نشرها، وقد تتأخر أو تتغير مع المراجعة. في حالات الطوارئ اتبع تعليمات الجهات الرسمية في بلدك. مؤشرات التجمعات والطاقة محسوبة داخل التطبيق وليست تصنيفات رسمية.

---

## 🇬🇧 English

### Overview
**PULSE 4.1** is a single-file Progressive Web App for monitoring global earthquake and volcanic activity in real time. It shows a full-screen map with the latest live events and their complete data below it, plus analytics, audible alerts, and region monitoring. No API keys and no backend required.

### Features
- **Full-screen map** (Leaflet) with marker clustering and animated pulses scaled to magnitude.
- **Live events feed** below the map with complete data per event: magnitude and type, place, time, last update, coordinates, depth, tsunami flag, felt reports, MMI/CDI, alert level, stations, Gap/RMS/Dmin, significance, status, type, source, estimated energy and ID — with a USGS link and a "Show on map" button.
- **Map layers:** Dark, Street, Satellite, plus a volcano layer and a heatmap.
- **Analysis tabs:** Overview, Earthquakes (magnitude/depth filters and event Replay), Analytics, Timeline, Clusters (computed indicator: 3+ events within 50 km and 72 h), Volcanoes (USGS elevated feed), Region Watch (radius around your location or a chosen point), Alerts.
- **Alert system:** browser notifications, sound, vibration and an in-app banner. Default threshold M5.0, applied to recent events (last 15 minutes). Volcano alerts for red/orange/eruption statuses.
- **Bilingual:** Arabic (RTL) and English (LTR); the choice is remembered.
- **Place search** (Nominatim/OpenStreetMap) and geolocation.
- **Resilient:** caches the last data locally and switches to a fallback SVG map if tiles fail to load.
- **Energy estimate:** `log10(E[J]) = 1.5 × M + 4.8` (approximate empirical relation).

### How to use
1. Open the app: the map fills the screen. Tap any quake marker to see details and the bottom panel.
2. Tap **"Latest events ⌄"** or scroll down for the live feed with full data. Tap **"Show on map"** to jump to an event.
3. Map tools (left): ⌖ My location · ⛶ Fit all events · ◌ Heatmap · ☷ Layers · 🌋 Volcanoes.
4. The **LIVE** button pauses/resumes auto-refresh. Earthquakes refresh every 45 s, volcanoes every 10 min.
5. **EN / AR** switches the language. 🔔 opens alert settings.
6. To enable alerts: tap "Enable alerts now" (browsers require this to play sound), then set the magnitude threshold and save.
7. To watch your area: **Region Watch** → "My location" → set the radius in km.

### Install & deploy
No build step or dependencies. Keep these files together:

```
index.html              # the app
manifest.webmanifest    # PWA manifest
sw.js                   # Service Worker (optional, for offline support)
```

- **Locally:** `python3 -m http.server 8080`, then open `http://localhost:8080`.
- **Codeberg Pages:** push the files to your `pages` repository (or branch) and enable Pages.
- Serve over **HTTPS** (or localhost) so notifications, geolocation and the Service Worker work.

### Data sources & libraries
| Source | Used for |
|---|---|
| USGS Earthquake Hazards Program | Earthquake feed (`all_day.geojson`) |
| USGS Volcano Hazards (HANS) | Elevated-activity volcanoes |
| OpenStreetMap / Nominatim | Geocoding and street layer |
| CARTO / Esri | Dark and satellite map tiles |
| Leaflet 1.9.4 (BSD-2-Clause) | Mapping engine |
| Leaflet.markercluster 1.5.3 (MIT) | Marker clustering |

### Disclaimer
PULSE **does not predict earthquakes** and does not replace official warnings. It shows data from official sources after publication; values may be delayed or revised. In an emergency, follow your local authorities. Cluster and energy figures are computed in-app and are not official classifications.

---

## 👨‍💻 Developer / المطور

**Nidal Watfa (نضال وتفة) — NIDAL WATFA**
مطوّر برمجيات مستقل (Self-taught) من سوريا، يبني تطبيقاته بالكامل من هاتف محمول.
*Self-taught software developer from Syria, building entirely on a mobile phone.*

> **Vanilla Evolution — القوة في البساطة والأداء**
> *Strength in simplicity and performance.*

### 🔗 Links / الروابط

| المنصة · Platform | الرابط · Link |
|---|---|
| 📧 Email | [nidalwatfa99@gmail.com](mailto:nidalwatfa99@gmail.com) |
| 🌐 Codeberg | [codeberg.org/nidalwatfa](https://codeberg.org/nidalwatfa) |
| 🐙 GitHub | [github.com/danial56hd-wq](https://github.com/danial56hd-wq) |
| 💼 LinkedIn | [linkedin.com/in/nidal-watfa-a91720301](https://www.linkedin.com/in/nidal-watfa-a91720301) |
| 𝕏 (Twitter) | [x.com/NidalWatfa12501](https://x.com/NidalWatfa12501) |
| ✈️ Telegram | [@nidal12watfa](https://t.me/nidal12watfa) |
| 🆔 ORCID | [0009-0003-2462-6630](https://orcid.org/0009-0003-2462-6630) |

### 🤝 Contact & Feedback / التواصل والملاحظات

- للإبلاغ عن مشكلة أو اقتراح ميزة: راسلني عبر البريد أو تيليجرام، أو استخدم بطاقة «المطور» داخل التطبيق.
- For bug reports and feature requests: email or Telegram, or use the in-app **Developer** card.
- Pull requests and issues are welcome on the project repository.

### 📚 Cite / الاستشهاد

If you use PULSE in research or a publication, please credit:

> Watfa, N. (2026). *PULSE 4.1 — Global Seismic & Volcanic Intelligence* [Software]. ORCID: 0009-0003-2462-6630.

---

## 📄 License / الترخيص

Released under the **MIT License** — see [LICENSE](LICENSE).
© 2026 Nidal Watfa.
