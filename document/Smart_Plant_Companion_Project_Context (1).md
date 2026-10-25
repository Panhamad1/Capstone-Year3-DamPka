# Smart Plant Companion & AI Health Scanner: Project Context

> **How to use this file:** Give this whole document to an AI assistant at the start of a conversation, then ask your question. It explains the project, the decisions already made, what is still open, and how to help. Update the "Status" sections as decisions change.

---

## 0. Instructions for the AI assistant reading this

- The team is a group of university students (software engineering). The main person talking to you is **new to mobile/app development**. They have learned **Flutter** and little else for mobile. Explain things simply, define terms, and give step-by-step guidance.
- **Prefer existing, free tools and services over building things from scratch** (for example, use a ready-made service instead of writing your own authentication).
- **Keep scope small.** This is a student capstone with fixed deadlines. Suggest stretch goals separately and do not expand the core scope without being asked.
- **Do not invent facts**: no made-up plant data, dataset licences, model accuracy, library names or API details. If unsure, say so and tell the user to verify.
- Respect the **decisions in Section 4**. If you think one is a bad idea, say why briefly, but do not silently change it.
- Anything marked **OPEN** or **TO CONFIRM** has not been decided. Ask before assuming.
- The AI scanner (Capstone II) is **not being worked on yet**. Focus on Capstone I unless told otherwise.

---

## 1. Project summary

| Item | Detail |
|---|---|
| **Project title** | Smart Plant Companion & AI Health Scanner |
| **University / faculty** | CADT (Institute of Digital Technology), Faculty of Digital Engineering, Department of Computer Science, specialized in Software Engineering |
| **Group** | 28 (6 members) |
| **Team members** | Chen Sovanpanha, Phally Sovanratana, Chao Vanchhoeurng, Yann Sokmeng, Thy Sereythi, Kim Seyha |
| **Project period** | 14 Oct 2026 to 31 Mar 2027 (two stages: Capstone I and Capstone II) |
| **Location context** | Cambodia (local plants and local users are the focus) |

**One-sentence idea:** A beginner-friendly plant-care app with a researched library of about 20-30 common local plants and a personal garden tracker. In a later stage it gains an AI scanner that predicts plant health from a leaf photo.

**Target users:** Beginners and hobbyists growing plants at home, on balconies, or in small gardens. The focus is on **indoor ornamental plants** and hobby gardening, with a few common edible plants.

**Problems being solved**
1. People are unsure how much light and water a plant needs.
2. Reliable care advice is hard to find, especially for local plants.
3. People forget routine care tasks and lose track of their growing plans.
4. Beginners cannot easily tell when a plant is unhealthy.

**Differentiation from existing apps** (from the team's early research)
- *Planta*: automated care schedules using plant type, location and weather. The team keeps its version simpler.
- *PictureThis*: AI plant identification and disease diagnosis. The team combines a localized plant library with long-term garden management.
- *Vera (Bloomscape)*: manual plant journal. The team adds an AI scanner (later).
- The team's positioning: simplicity, free manual tracking, localized plant information, and a focused AI demonstration.

---

## 2. Two-stage plan

### Capstone I (14 Oct to 16 Dec 2026): the app

Deliver a working app with **two main features** (Plant Library and Personal Garden), as a **Telegram Mini App first**, then an **Android build of the same Flutter code as a stretch goal** (decided; the teacher recommended starting with the Mini App because it is easier).

### Capstone II (17 Dec 2026 to 31 Mar 2027): the AI Health Scanner

Research, train, evaluate and integrate an image classifier that predicts plant health from a leaf photo. **Not being decided yet**; details in Section 8 are preliminary research only.

---

## 3. Official academic dates (fixed, do not change)

**Capstone I**
| Date | Event |
|---|---|
| 9 Oct 2026 | Advisor request deadline |
| 19 Oct 2026 | Project proposal deadline |
| 2-13 Nov 2026 | Mid-term presentation window |
| 11 Dec 2026 | All document submission |
| 16 Dec 2026 | Final Capstone I presentation |

**Capstone II**
| Date | Event |
|---|---|
| 8-19 Feb 2027 | Mid-term presentation window |
| 24 Mar 2027 | Document submission |
| 31 Mar 2027 | Final Capstone II presentation |

Internal work-period dates in the proposal are the team's own plan (proposed targets, not official).

---

## 4. Decisions made so far (Capstone I)

### 4.1 Platform and technology

| Topic | Decision |
|---|---|
| **App framework** | **Flutter** (the only mobile-related skill the team has learned) |
| **First delivery** | **Telegram Mini App** (a web app that opens inside Telegram). Built with Flutter's web build. |
| **Second delivery (stretch)** | **Android app** from the same Flutter code, only if time allows. iOS is *not* planned (needs a Mac and a paid developer account). |
| **Login / accounts** | **None.** Telegram already identifies the user. No custom authentication to build. |
| **Backend server** | **None planned** for Capstone I (no Node.js/Express/Postgres/MySQL for the core app). |
| **Hosting** | Only a **free static host** for the Mini App files, which must be served over HTTPS (examples: GitHub Pages, Netlify, Cloudflare Pages). **OPEN: which one.** Check current free-tier terms. |
| **Registering the Mini App** | Through Telegram's official **BotFather**. |
| **Plant data storage** | **Bundled with the app** (for example as JSON plus image files). Not stored in a live database. |
| **User's garden storage** | **On the user's own device** (local storage). **OPEN: exact method** (browser storage inside the Mini App, or a local database in the Android build). |
| **Offline use** | Wanted. Planned so that plant data and the user's garden work without internet. **Needs testing**: a Mini App relies on browser caching, which may be less reliable than an installed Android app. Do not promise it as guaranteed. |
| **Language** | **English** for now. Khmer is a possible future feature (design the app so languages can be added later, for example a "Khmer name" field per plant). Machine translation is considered unreliable for plant terms. |
| **Community** | **Telegram group link** inside the app. No community system will be built in the app. |

Notes for the AI:
- Earlier plans mentioned React, Node.js, Express, MySQL (a responsive web app). **Those were dropped** for the core app. Do not suggest them unless the user asks.
- The user once suggested Postgres. Explanation given: Postgres is a server database and cannot run on a phone; local storage or SQLite is the on-device equivalent. It is not needed for Capstone I.
- Mini App local storage can be cleared and does not follow the user to another device. Telegram also offers a small cloud-storage feature, which is a possible later option.

### 4.2 Features in scope for Capstone I

**Feature 1: Plant Library**
- Browse, search, and view plants (about **20-30** common, locally relevant plants; this is a *proposed target*, not yet completed).
- Plant detail page with care guidance (watering, light, and so on), a **photo**, and **source links**, so users can explore more instead of reading long text.
- Offline-friendly: data and images stored with the app.
- Suggested extra fields (ideas, not all confirmed): common, scientific and Khmer names; soil; humidity; temperature; fertilizing; propagation; common problems and fixes; pet/human toxicity; difficulty level; growing/harvest time for edibles; favorites; category filter; an "Add to my garden" button.

**Feature 2: Personal Garden (hybrid design)**
- Each library plant has a **template** with default start steps, milestones and care intervals (because beginners do not know how to start).
- When a user adds a plant, the template is **copied** into their garden.
- The user can then **freely edit** steps, dates and intervals (because real life does not follow the system's recommendation exactly).
- Record milestones, progress and care activities (for example "watered today").
- **Reminders: in-app alerts only** in the Mini App. Phone notifications are possible only in the Android build, and only if time allows.

**Feature 3 (light): Community**
- A link to a Telegram group where users ask questions and share ideas.

### 4.3 Explicitly out of scope for Capstone I

- The AI Health Scanner and any model training
- Complex disease diagnosis
- Weather-based care automation
- Push/SMS/email notifications from a server
- An in-app community or social system
- User accounts and login
- A custom backend server
- Advanced filters and plant photo timelines (later ideas)

### 4.4 Plant data approach

- The team **researches plant facts manually** and writes summaries **in their own words**, recording a **source link** for every entry.
- Third-party plant APIs were rejected earlier (request limits, paid details, caching restrictions).
- Images: the team's own photos where possible, or freely licensed images (for example Wikimedia Commons, Unsplash, Pexels). **Record the licence and credit** each image. Check licences rather than assuming anything is free to use.
- Trusted sources named in the research:
  - NC State Extension Gardener Plant Toolbox: https://plants.ces.ncsu.edu/
  - University of Minnesota Extension (houseplants): https://extension.umn.edu/houseplants
  - Clemson Cooperative Extension: https://hgic.clemson.edu/
  - Royal Horticultural Society: https://www.rhs.org.uk/plants
- Suggested record fields: `plant_id`, `common_name`, `scientific_name`, `category` (Indoor Ornamental or Balcony Edible), `light_requirement`, `watering_guidance`, `soil_and_pot`, `common_problems`, `source_url`, `image_url` (plus the extra fields listed in 4.2).
- Suggested workflow: split the plants among teammates (about five each), use identical fields for all entries, and review for consistency before importing.

### 4.5 Plant list (NOT chosen yet)

The specific 20-30 plants have **not been chosen**. The team will decide, picking plants that are common locally in Cambodia. Do not assume or suggest a fixed list. If asked to help choose plants, ask about local availability first, and note that for Capstone II the supported plants should also match the chosen AI dataset.

---

## 5. Capstone I plan (proposed internal work periods)

| Period | Work |
|---|---|
| 17-19 Oct | Finish and submit the proposal (official deadline 19 Oct) |
| 20-24 Oct | Agree requirements, review similar apps, assign task owners |
| 20-31 Oct | Research care sources, collect first plant records, preliminary review of AI datasets |
| 23 Oct-1 Nov | Sketch screens, plan data structure, set up Flutter + Telegram Mini App environment, build a skeleton |
| 2-13 Nov | Mid-term presentation window: demo the prototype |
| 14-20 Nov | Finish plant browse/search/detail, and adding plants from templates with edit/stop/delete |
| 21-27 Nov | Milestones, progress, care records, in-app reminders, Telegram group link |
| 28 Nov-4 Dec | Combine into one Mini App, host it, test in Telegram (including offline); start Android build if time allows |
| 5-8 Dec | Test on a phone, fix issues, finish Android build if time allows |
| 9-10 Dec | Finish report and documents |
| 11 Dec | All documents submitted (official) |
| 12-15 Dec | Practice presentation |
| 16 Dec | Final Capstone I presentation (official) |

Objective target dates in the proposal: plant information 31 Oct; Plant Library 20 Nov; Personal Garden 20 Nov; reminders 27 Nov; testing 4-10 Dec; Android build by 8 Dec if time allows.

---

## 6. Open questions / things the user may still decide

1. **Hosting service** for the Mini App (free static host).
2. **Exact local-storage method** (Mini App browser storage versus a local database in Android).
3. **Whether the teacher accepts "Mini App plus stretch Android build"** as satisfying the "mobile application" requirement for Capstone I.
4. **Final plant list** (20-30 plants) and **image sources**.
5. **Flutter packages** for Telegram Mini App integration, local storage and caching. These have **not been verified**; check current options before choosing.
6. **Team roles** (who does what): not yet defined.
7. **Version control and project-management tools:** not yet chosen.
8. **Testing approach** (devices, test users): not yet defined.

---

## 7. Known risks

- **Offline in a Mini App is the weakest point**: it depends on browser caching inside Telegram and needs real testing. The Android build would be the dependable route.
- **Local storage in a Mini App can be cleared** and does not sync between devices.
- **Reminders**: a Mini App cannot create phone notifications. Only a Telegram bot (which needs a small server) or the Android app can. For now: in-app alerts only.
- **The team is new to mobile/web app deployment**, so keep tasks small and test early.
- **Scope creep**: community, accounts, notifications and the AI scanner are deliberately excluded from Capstone I.

---

## 8. Capstone II: AI Health Scanner (preliminary research only; NOT decided)

> The user has said: "Let's not think about this yet; we confirm it later." Treat everything here as background, not decisions. Do not present any of it as final.

**Goal:** the user submits a photo of a plant leaf and receives a **text prediction** of the plant and its health condition. The scanner is an **educational prediction tool, not a guaranteed diagnosis**.

**Task type (recommended in research):** single-label **image classification** (for example "Snake Plant - Healthy" or "Money Plant - Bacterial Wilt"). Object detection (bounding boxes) was judged too complex.

**Approach (proposed, not final):** **transfer learning** with a pretrained model such as **MobileNetV2** (preferred over training from scratch for a small student dataset). Training could be done in Google Colab. **Frameworks and tools are not chosen.**

**Suggested data workflow**
1. Organize images into class folders (plus an optional "unsupported/background" class).
2. Split the raw data **70% train / 15% validation / 15% test, before augmentation**.
3. Resize to 224 x 224 and normalize.
4. Augment **training images only** (simple rotations, flips, slight zoom).
5. Train (freeze the pretrained base first, add a classification head).
6. Evaluate on the held-out test set.
7. Integrate (how the model reaches the app is **OPEN**: an API service or on-device).

**Metrics to report:** accuracy, precision, recall, F1-score, confusion matrix. **Do not promise a target accuracy before testing.**

**Safety and limits**
- Low-confidence predictions should return an uncertainty message (the research suggested ~70% as an example threshold, not fixed).
- Unsupported images (desks, hands, walls) could be handled with a background class; this does not guarantee correct rejection.
- State limits: a small dataset may not represent real conditions; performance depends on lighting, camera, background and leaf angle; a high test score does not guarantee real-world performance.

**Datasets considered (verify the pages and licences before using)**
| Dataset | Content | Size | Licence noted in research |
|---|---|---|---|
| Indoor Plant Disease (v2) | Money Plant, Snake Plant, Spider Plant; 9 classes | 787 raw images (~81-93 per class) | CC BY 4.0 (first-choice candidate) |
| PlantDoc (Cropped) | 13 species, mostly crops; up to 17 disease classes | 2,598 | CC BY 4.0 noted |
| PlantVillage | 14 crop species; 26 diseases | 54,306 | Licence unconfirmed in the source; not recommended for the houseplant focus |

**Suggested first experiment (not committed):** two plants (for example Money Plant and Snake Plant) with Healthy/Diseased labels, four classes, fine-tune MobileNetV2 for about 10 epochs.

**Open advisor questions:** how many species/classes are enough (the research gave conflicting numbers: 5-10 and 8-12; the first dataset has 3 species and 9 classes); whether the team may collect its own photos; whether the scanner should fall back to healthy/unhealthy when confidence is low; how the model connects to the app.

**Capstone II proposed internal periods (not official):** 17 Dec-31 Jan confirm scope and dataset; 1-7 Feb preprocess and baseline; 8-19 Feb mid-term (official window); 20 Feb-5 Mar train; 6-12 Mar evaluate; 13-19 Mar integrate; 20-23 Mar test and write; 24 Mar documents (official); 31 Mar final presentation (official).

---

## 9. The proposal document

A formal **Capstone Proposal PDF** exists (CADT template, A4) covering both stages: description, objectives, methodology, milestones, and an advisor approval line. It follows these rules:
- The header, team table, names, group number and title must stay unchanged.
- It must not claim completed work, trained models or achieved accuracy.
- Official dates are fixed.
- Capstone II details are flagged as proposals needing advisor confirmation.
- The advisor signature area is left blank for the advisor to sign. Never invent signatures or approvals.

---

## 10. Suggested prompts to use with this file

- "Using this context, explain step by step how to set up a Flutter web app as a Telegram Mini App, for a beginner."
- "Help me design the JSON structure for the plant library and the personal garden templates."
- "Suggest the simplest way to store the user's garden locally in a Flutter web app, and what to test for offline use."
- "Review my plant care text for plant #X and tell me what is missing, without inventing facts."
- "Help me plan the 20-24 Oct to 4 Dec tasks across 6 team members."
- "Compare free static hosts for a Flutter web Mini App; tell me what I should verify myself."
