# ClassTrac

A desktop attendance tracker written in C with [raylib](https://www.raylib.com/). You pick a subject, mark each student as Present, Absent or Late, and save the session as a dated CSV file. Saved sessions can be reopened or deleted from inside the app.

This is our group project for AISP 121 (First Year / First Semester, BIT) at Kathmandu University, Department of Engineering. It was built to practise structs, enums, arrays, file handling and splitting a C program into modules.

## Screenshots

<table>
  <tr>
    <td><img src="docs/screenshots/home.png" alt="Home screen"><br><sub>Home</sub></td>
    <td><img src="docs/screenshots/subjects.png" alt="Subject list"><br><sub>Subject list</sub></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/add-subject.png" alt="Add subject popup"><br><sub>Adding a subject</sub></td>
    <td><img src="docs/screenshots/attendance.png" alt="Attendance screen"><br><sub>Attendance screen</sub></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/marking.png" alt="Marking attendance"><br><sub>Marking P / A / L</sub></td>
    <td><img src="docs/screenshots/add-student.png" alt="Add student popup"><br><sub>Adding a student</sub></td>
  </tr>
  <tr>
    <td><img src="docs/screenshots/reports.png" alt="Saved reports list"><br><sub>Saved reports</sub></td>
    <td><img src="docs/screenshots/report-view.png" alt="Report view"><br><sub>Opening a report</sub></td>
  </tr>
</table>

## What it does

- Add and delete subjects
- Add and remove students for the session
- Mark each student Present, Absent or Late with one click
- Save the session as `<Subject>_<YYYY-MM-DD>_<HH-MM-SS>.csv` in the `records/` folder
- List saved reports newest first, open them in a colour-coded table, or delete them

Reports are plain CSV, so they also open in Excel or Google Sheets:

```
Roll No,Name,Status
BIT202601,RIYA SHRESTHA,Present
BIT202602,PUKAR RAI,Absent
```

## Running it

You need `gcc`, `make` and raylib installed.

```
git clone https://github.com/nobeliumjuju/ClasstracF.git
cd ClasstracF
make run
```

The Makefile picks linker flags for Windows (MinGW), macOS (Homebrew raylib) and Linux. Our screenshots were taken on macOS, so that is the setup we have actually used. `make clean` removes the build output.

## Project layout

| File | What it holds |
| --- | --- |
| `main.c` | Window setup, main loop, the subject and student lists in memory |
| `classtrac.h` | Shared enums, structs, constants and colours |
| `ui.c` | Button, text input box and keyboard input |
| `home_screen.c`, `subject_screen.c`, `attendance_screen.c`, `report_screen.c` | One file per screen |
| `storage.c` | Creating the records folder, saving, listing, reading and deleting CSV files |

`currentScreen` decides which screen is drawn each frame, and every screen redraws completely on every frame (raylib's immediate-mode style).

## Limitations

- The starting subjects and the student roster are written directly in `main.c`. Changes made while the app is running are lost when it closes. Only saved attendance sessions persist.
- Deleted subjects, students and reports cannot be recovered.
- Single user, mouse only.

## Contributors

| Name | Roll no. |
| --- | --- |
| Nobel Devkota | 21 |
| Manish Karki | 11 |
| Ralen Shrestha | 14 |
| Bilisha Khatri | 18 |
| Sadikshya Neupane | 23 |


