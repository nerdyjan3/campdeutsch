Put this exactly as your first file. It defines your full project for Codex.

---

**Filename:** `docs/PROJECT_OVERVIEW.md`

**Content:**

```markdown
# MitMut WorkAdventure Game Platform

## 1. Goal
Build a tile-based multiplayer learning game inside **WorkAdventure**.  
Players explore rooms (maps made in **Tiled**) and complete interactive language-learning exercises.  
Tasks are served by a **custom backend** you control — not external tools like Wordwall or Kahoot.

---

## 2. Architecture Overview

| Component | Tech Stack | Description |
|------------|-------------|--------------|
| **Frontend / Game** | WorkAdventure + TypeScript | Map, characters, UI popups, puzzles |
| **Map Editor** | Tiled (.tmj maps) | Level design, triggers, zones |
| **Backend API** | Node.js (Express/Fastify) | Sends tasks, checks answers, stores progress |
| **Database** | SQLite (local) → PostgreSQL (production) | Saves users, scores, game state |
| **Static Hosting** | GitHub Pages / Vercel | For maps, assets, docs |
| **Server Hosting** | Render / Oracle Cloud | For backend API |
| **Version Control** | GitHub | Central repo for all assets and code |

---

## 3. Core Features

1. **Map Interaction**
   - Player enters a zone → script triggers popup
   - Popup shows question or puzzle
   - Solving it unlocks next area or triggers visual changes

2. **Exercise System**
   - Game fetches JSON task from backend (`/api/tasks/:id`)
   - Player submits answer → backend validates → returns feedback

3. **Progress Tracking**
   - Each player has a UUID
   - Progress saved in local storage or DB
   - Unlocks persist between sessions

4. **Admin Panel (future)**
   - Upload new tasks
   - View progress data

---

## 4. Folder Structure

```

/maps/
main.tmj
assets/
/scripts/
main.ts
/api/
server.ts
routes/
tasks.ts
players.ts
db/
schema.sql
/docs/
PROJECT_OVERVIEW.md
API_REFERENCE.md
package.json

````

---

## 5. API Example

```ts
GET /api/tasks/:id
→ { id: 1, question: "Was ist rot?", options: ["Apfel", "Banane"], answer: 0 }

POST /api/answer
Body: { playerId, taskId, selected }
→ { correct: true, nextTask: 2 }
````

---

## 6. Development Flow

1. Local setup:

   ```bash
   npm install
   npm run dev
   ```
2. Edit `main.ts` to add zones and popups.
3. Backend runs on `localhost:3000`.
4. WorkAdventure connects to that API via `fetch()`.
5. Push all code to GitHub.

---

## 7. Deployment Plan

| Environment                  | Platform               | Notes                  |
| ---------------------------- | ---------------------- | ---------------------- |
| **Frontend (map + scripts)** | GitHub Pages or Vercel | Hosts static assets    |
| **Backend API**              | Render / Oracle Cloud  | Node.js server         |
| **Database**                 | PostgreSQL             | Persistent progress    |
| **Domain**                   | mitmut.studio/game     | Optional custom domain |

---

## 8. Next Steps

* [ ] Set up repo and folders
* [ ] Integrate WorkAdventure scripting
* [ ] Connect API backend
* [ ] Build one sample exercise
* [ ] Store progress
* [ ] Design visual theme

---

## 9. Reference Links

* [WorkAdventure Docs](https://workadventu.re/map-building)
* [Tiled Editor](https://www.mapeditor.org/)
* [Express Framework](https://expressjs.com/)
* [TypeScript Docs](https://www.typescriptlang.org/docs/)

```

---

After saving, go to your repo’s **Code** tab. You’ll see a `/docs` folder containing `PROJECT_OVERVIEW.md`.  
That’s your master document for Codex and any developer joining the project.  

Do you want me to make the second file (`API_REFERENCE.md`) next so Codex knows how to build your backend endpoints?
```
