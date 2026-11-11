Molly's Pomodoro timer for OBS
==============================
Files (keep them together in one folder you won't move or delete):
  molly-pomodoro-timer.html   the timer
  chime-break.wav             plays when a break starts
  chime-focus.wav             plays when focus starts

Setup, in OBS:
  1. Sources > + > Browser. Name it anything.
  2. Check "Local file" and Browse to molly-pomodoro-timer.html.
  3. Width 380, Height 230.
  4. Check "Control audio via OBS".
  5. Page permissions: "Read access to OBS status information" (this is what lets it auto-start when you go live).
  6. OK. To hear the chimes in your headset: Audio Mixer > gear icon > Advanced Audio Properties > set the source to "Monitor and Output".
  7. Right-click the source > Interact for Start / Pause / Skip / Reset.

Change the lengths: open the .html in Notepad and edit the numbers in the CONFIG block near the top.
Own sounds: replace the two .wav files (or change their names in CONFIG).

Full walkthrough: https://mollypw.com/projects/obs-pomodoro-timer/
