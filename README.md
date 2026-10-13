# timetable-generator
“Automated academic timetable generation system”.
**Live demo:** https://dharnak22.github.io/timetable-generator/
## How to run
Open the live demo link above, or download `index.html` and double-click it to open in your browser. No installation needed.
## About the project

Creating a college timetable by hand means juggling teachers, rooms, labs and student batches, and one clash can break the whole schedule. This project automates that work. The timetable coordinator enters the teaching requirements, rooms, faculty availability and university timings, and the system generates a conflict-free timetable. It is built for the School of Cyber Security and Digital Forensics, NFSU, Gandhinagar, and comes preloaded with the M.Sc. Digital Forensics and Information Security – I (2026-27) timetable.

## Features

- **Coordinator inputs:** working days, period timings and breaks, classrooms and labs (type and capacity), student groups and practical batches, subjects, faculty availability, fixed sessions.
- **Automatic generation:** a backtracking scheduler places every theory period and practical session.
- **Mandatory rules, never broken:**
  - sessions stay inside working hours and avoid breaks
  - faculty teach only when available
  - no faculty, room or student group has overlapping sessions
  - a whole-class session never overlaps a practical for any batch of that class
  - room capacity fits the class or batch
  - practicals use a suitable lab and the required consecutive periods
  - every subject gets its full weekly theory periods and practical sessions
  - fixed sessions stay in their assigned slots
- **Preferences:** preferred teaching slots are honoured where possible, and the result shows how many were met.
- **Impossible timetable report:** if the inputs cannot work, the system says why instead of showing an incomplete timetable. For example: "Subject X requires 5 weekly periods, but its assigned faculty is available for only 3 periods."
- **Three views:** programme/student-wise, faculty-wise (a timetable for every faculty member), and classroom/lab-wise.
- **Manual editing:** move any session and get an instant conflict check, with a clear reason if the move is rejected.
- **Lock and regenerate:** lock chosen sessions and regenerate only the rest.
- **Draft and publish:** save a draft, and publish only after the whole timetable passes full validation.
- **Print and export:** print the timetable or export it as CSV.
- **Colour-coded subjects** with a legend.

## How it works

1. **Sessions:** each requirement is turned into individual sessions. "3 theory periods" becomes 3 sessions.
2. **One rule checker:** a single function decides whether a session can go in a given day, period and room. The solver and manual edits both use it, so the rules live in one place.
3. **Solver:** it places the hardest sessions first, tries slots one at a time, and backs up when it gets stuck. Preferences only change the order in which slots are tried, so mandatory rules are never relaxed.
4. **Pre-check:** before solving, the system compares each faculty member's workload with their availability and flags impossible inputs early.

## Tech used

- HTML, CSS and JavaScript in a single `index.html` file
- No frameworks, no backend, no installation
- Browser `localStorage` for saving drafts

## Assumptions in the sample data

The source timetable does not list these, so they are assumed and can be edited in the app:
- Student strength of 40, split into two practical
