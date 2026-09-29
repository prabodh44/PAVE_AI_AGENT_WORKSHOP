# Setup Guide — Google ADK Agent Lessons

Follow these steps once before running `step1_simple_agent.py`, `step2_tool_agent.py`, or `step3_multi_agent.py`.

---

## 1. Check Python is installed

Open a terminal and run:

```bash
python3 --version
```

You need Python 3.9 or newer. If this command fails, install Python from [python.org](https://www.python.org/downloads/) first.

> On Windows, you may need to use `python` instead of `python3` in the commands below — try both if one doesn't work.

---

## 2. Create a virtual environment

A virtual environment keeps this project's packages separate from everything else on your computer.

Navigate to your project folder (the one containing the three `.py` files), then run:

**macOS / Linux**
```bash
python3 -m venv venv
```

**Windows**
```bash
python -m venv venv
```

This creates a new folder called `venv` inside your project.

---

## 3. Activate the virtual environment

You must do this every time you open a new terminal to work on this project.

**macOS / Linux**
```bash
source venv/bin/activate
```

**Windows (Command Prompt)**
```bash
venv\Scripts\activate.bat
```

**Windows (PowerShell)**
```bash
venv\Scripts\Activate.ps1
```

When it's active, you'll see `(venv)` at the start of your terminal prompt. That means Python and pip now point inside this project only.

> If PowerShell gives a "running scripts is disabled" error, run this once: `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned`, then try activating again.

To turn it off later, just run:
```bash
deactivate
```

---

## 4. Install the required packages

With the virtual environment active, run:

```bash
pip install google-adk google-genai python-dotenv
```

This installs:
- `google-adk` — the Agent Development Kit (used in Step 2 and Step 3)
- `google-genai` — the base Gemini SDK (used in Step 1)
- `python-dotenv` — loads your API key from a `.env` file

---

## 5. Get a Gemini API key

1. Go to [Google AI Studio](https://aistudio.google.com/apikey).
2. Sign in with a Google account.
3. Click **Create API key** and copy it (it's a long string of letters and numbers).

Keep this key private — treat it like a password.

---

## 6. Add the key to a `.env` file

In your project folder (the same folder as the `.py` files), create a new file named exactly:

```
.env
```

Open it in a text editor and add this one line, replacing the placeholder with your real key:

```
GEMINI_API_KEY=your_key_here
```

Save the file. `load_dotenv()` in each script reads this file automatically — you don't need to do anything else in the code.

> **Do not** put quotes around the key and **do not** commit this file to GitHub. If you use Git, add a `.gitignore` file containing the line `.env` so it's never uploaded by accident.

---

## 7. Run a lesson file

With the virtual environment still active:

```bash
python step1_simple_agent.py
```

```bash
python step2_tool_agent.py
```

```bash
python step3_multi_agent.py
```

---

## Troubleshooting

| Problem | Likely cause / fix |
|---|---|
| `RuntimeError: GEMINI_API_KEY not found` | The `.env` file is missing, misnamed, or not in the same folder as the script. |
| `ModuleNotFoundError: No module named 'google.adk'` | The virtual environment isn't active, or step 4 wasn't run. Activate it (step 3) and reinstall. |
| `(venv)` not showing in terminal | The activation command didn't run correctly — recheck step 3 for your operating system. |
| API errors mentioning quota or billing | Check your key is valid and that the Gemini API is enabled for your Google account/project. |
