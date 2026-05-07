We are working in /Users/ashrocket/ashcode/garden on the Garden camera-gesture web app.

Current production URL:
https://garden.grouchobarks.bandmusicgames.party

Latest pushed commit on main:
fe6e004 Improve camera startup diagnostics

Recent work:
- Added camera setup/calibration phase.
- Added grey ghost hand outlines behind the scene.
- Added spread-finger hand guides.
- Tuned guide placement and size using HEIC reference photos.
- Added protection against macOS Continuity Camera/iPhone camera sources.
- Added clearer camera/hand-tracking startup diagnostics.
- Added MediaPipe GPU-to-CPU fallback.

Important issue to continue:
The app is still showing camera startup failures in ChatGPT Atlas. We need to test the latest deployed build and determine whether the failure is:
- iPhone/Continuity Camera being blocked,
- camera permission denied,
- no usable MacBook camera selected,
- MediaPipe hand tracking failing,
- or Atlas/browser-specific camera behavior.

User preference:
Do not use iPhone/Continuity Camera. Prefer the MacBook built-in camera only.

Useful commands:
- Check status: git status --short
- Syntax check inline JS:
  node -e "const fs=require('fs'); const html=fs.readFileSync('index.html','utf8'); const scripts=[...html.matchAll(/<script>([\s\S]*?)<\/script>/g)].map(m=>m[1]).join('\n'); new Function(scripts); console.log('inline script syntax ok');"
- Whitespace check: git diff --check
- Open in Atlas:
  open -a "ChatGPT Atlas" https://garden.grouchobarks.bandmusicgames.party
- Push main:
  git push origin main

Next best step:
Open the production URL in Atlas, click `camera garden`, read the exact new diagnostic message, then fix the specific failure path. Do not continue guessing from the old generic "Camera permission or hand tracking failed" message.
