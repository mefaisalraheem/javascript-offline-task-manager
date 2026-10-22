# Offline Task Manager

A browser-based task manager with drag-and-drop boards, filters, keyboard shortcuts, and full offline persistence via IndexedDB.



https://github.com/mefaisalraheem/javascript-offline-task-manager.git


## Features

- **Kanban board** — To Do / In Progress / Done columns
- **Drag & drop** — Move tasks between columns
- **Offline-first** — All data stored in IndexedDB (works with no internet)
- **Filters** — Search, priority, and tag filtering
- **Keyboard shortcuts**
  - `N` — New task
  - `/` — Focus search
  - `Esc` — Close modal / blur input
  - `Ctrl/Cmd + Z` — Undo last delete
- **Export / Import** — JSON backup and restore
- **Accessible** — ARIA roles, keyboard-navigable cards, focus management
- **Online/offline indicator**

## Run

Open `index.html` directly, or serve locally:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000




Data model
js
{
  id: string,
  title: string,
  description: string,
  priority: 'low' | 'medium' | 'high',
  status: 'todo' | 'inprogress' | 'done',
  tags: string[],
  due: string,        // 'YYYY-MM-DD' or ''
  createdAt: number,  // ms
  updatedAt: number,  // ms
  order: number
}




## ✅ Verification Checklist

| Requirement | Implementation | Status |
|---|---|---|
| DOM manipulation | Templates, cloning, dynamic rendering | ✅ |
| Event handling | Delegation for cards, drag, filters, keyboard | ✅ |
| Async programming | `async/await` throughout, `Promise` wrappers for IDB | ✅ |
| IndexedDB | `db.js` full wrapper with upgrade, transactions, bulk ops | ✅ |
| Drag & drop | HTML5 DnD with visual feedback, drop zones | ✅ |
| Filters | Search + priority + tag, "Clear" button | ✅ |
| Keyboard shortcuts | N, /, Esc, Ctrl+Z | ✅ |
| Offline persistence | IndexedDB, no network deps, connection indicator | ✅ |
| Export/Import | JSON download + file reader | ✅ |
| Accessibility | ARIA, focus management, keyboard card activation | ✅ |
| Error resilience | try/catch, toasts, import validation, normalization | ✅ |
| XSS safety | `textContent` used for user data (no `innerHTML`) | ✅ |

## How to Test Everything Works

1. **Persistence** — Create a task, refresh the page → task is still there.
2. **Offline** — DevTools → Network → "Offline". Everything still works. Indicator shows "Offline".
3. **Drag & drop** — Drag a card between columns. Status persists after refresh.
4. **Filters** — Type in search, change priority/tag selects. Counts stay accurate.
5. **Shortcuts** — Press `N`, `/`, `Esc`. Delete a task then `Ctrl+Z`.
6. **Import/Export** — Export, delete a task, import the file → task returns.
7. **Keyboard nav** — Tab to a card, press `Enter` → modal opens.
8. **Edit** — Click a card, modify, save → changes persist.

All code is dependency-free and runs from `file://` or any static server.