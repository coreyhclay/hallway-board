# Hallway Board

A daily checklist for an iPad mini on the wall. Everything is in one page, with no app store, no account, and no notifications.

**Files**

- `index.html`: the whole app
- `apple-touch-icon.png`: the home screen icon
- `Manrope-OFL.txt`: license for the embedded font

## 1. Edit your tasks

Open `index.html` in a text editor. The task list is at the very top:

```js
const TASKS = [
  { id: 'peloton', name: 'Peloton ride',      every: 1, highlight: { label: 'Peloton', unit: 'ride' } },
  { id: 'trash',   name: 'Take out trash',    on: ['mon'] },
  { id: 'dust',    name: 'Dust',              every: 'weekend', verb: 'dusted' },
  { id: 'sheets',  name: 'Change bed sheets', every: 30, verb: 'changed' },
  // ...
];
```

- `every: 1` is daily. `every: 2` means 2 days after you last checked it off, `every: 30` is monthly, and so on. If you do something late, the next one moves back with it.
- `every: 'weekend'` is once each weekend. The task shows up on Saturday, stays on Sunday if it isn't done yet, and never appears Monday to Friday. If a whole weekend goes by, it's back the next Saturday.
- `on: ['mon']` pins a task to fixed weekdays instead.
- `verb: 'watered'` changes "Last done 3 days ago" to "Last watered 3 days ago".
- Tasks show on the board in the order they're listed.
- `highlight` (one task) is what fills the 30-day grid on the All done screen.
- Keep each `id` the same once you start; changing it starts that task's history over.

## 2. Preview it

Open `index.html` in any browser. To see it with sample history, add `?demo` to the end of the address. Nothing is saved in demo mode.

## 3. Put it online

The iPad needs a web address to load it from. GitHub Pages is free and easy:

1. Create a new repository on GitHub and upload the three files.
2. Go to **Settings → Pages**, set **Source** to **Deploy from a branch**, choose **main** and **/ (root)**, then **Save**.
3. After a minute, it's live at `https://<your-username>.github.io/<repository-name>/`.

Any static host works just as well (Netlify, Cloudflare Pages, your own server). The page only contains your task names. Your checkmarks never leave the iPad.

## 4. Set up the iPad

1. Open the address in **Safari**, tap **Share → Add to Home Screen**, and open the board from the new **Hallway** icon. It runs full screen with no browser bars.
2. **Settings → Display & Brightness → Auto-Lock → Never**, so the screen stays on.
3. Turn off notifications on this iPad (Settings → Notifications), so nothing pops up over the board.
4. Lock it to the board with **Settings → Accessibility → Guided Access**: turn it on and set a passcode. Then open the board and triple-click the top button to start. Triple-click again and enter the passcode to get out.
5. Keep it plugged in.

## How it behaves

- Each day shows what's due. Daily tasks always appear; the others appear once enough days have passed since you last did them, or on their day.
- On the very first day, tasks like the monthly ones appear right away because there's no history yet. Check off anything you did recently, and its clock starts from there.
- Tap a task to check it off and tap again to undo.
- The squares on the right are the last 7 days, with today on the far right (dashed until it's done).
- When everything is checked, the board switches to the All done screen after a moment. **Show today's list** brings the list back, and after a minute without taps it returns to All done.
- At midnight it starts the new day on its own.
- Up to 10 tasks are shown in one column. Past that, it switches to two columns and hides the week squares so everything still fits on one screen.

## Your data

Checkmarks are saved on the iPad, inside the home screen app. A few things to know:

- Always use the home screen icon. A regular Safari tab keeps its own, separate checkmarks.
- Deleting the home screen icon or clearing Safari's website data erases the history.
- Updating `index.html` on your host keeps the history, as long as the address stays the same.
