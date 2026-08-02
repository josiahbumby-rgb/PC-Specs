# PC-Specs
Opens a spec list whenever you unlock your device
you will have to program task scheduler to open the pythonw.exe file on unlock
r"""
spec_overlay.py — shows a small always-on-top overlay with your PC specs
for 30 seconds, then closes itself. Now includes GPU, temps, and network info.
 
SETUP (Windows) — run every time you unlock your PC:
1. Install Python from python.org if you don't have it (check "Add to PATH").
2. Save this file, e.g. C:\Tools\spec_overlay.py
3. Open Task Scheduler (search for it in the Start menu).
4. Click "Create Task..." (right panel, not "Create Basic Task").
5. General tab: give it a name, e.g. "Spec Overlay".
6. Triggers tab > New:
   - Begin the task: "On workstation unlock"
   - Click OK.
7. Actions tab > New:
   - Action: "Start a program"
   - Program/script: pythonw.exe
     (use the full path if it's not on PATH, e.g.
      C:\Users\<you>\AppData\Local\Programs\Python\Python312\pythonw.exe)
   - Add arguments: "C:\Tools\spec_overlay.py"
   - Click OK.
8. Click OK to save the task.
9. Done — lock your PC (Win+L) and unlock it to test. It'll pop up
   top-right for 30 seconds.
 
Optional installs for full data (fine without them — those lines just skip):
   pip install psutil GPUtil
 
Note on temps: Windows blocks most temp sensors without vendor tools.
This script tries GPU temp via nvidia-smi (NVIDIA only) and CPU temp via
psutil (works on some laptops, rarely on desktops). If nothing is found,
it just won't show a temp line — no crash.
"""
