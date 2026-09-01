# Research-Environment


![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/a8b90cf25a985601f60a8d45f49a35594840e9c4/Research-Environment/Screenshot%202026-09-01%20005609.png)

open PowerShell and run:

cd C:\Users\eelve

mkdir Vulnerability-Research-Lab

cd Vulnerability-Research-Lab

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/f077544d42d018ed2b1d8ec924d5a35f10873654/Research-Environment/Screenshot%202026-09-01%20005721.png)

Verify: Get-Location

You should see something similar to:

Path
----
C:\Users\eelve\Vulnerability-Research-Lab

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/2a0406db0095bf21c9d150b68b4cc0749872204a/Research-Environment/Screenshot%202026-09-01%20005936.png)
![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/383ce32ef873822d2175401e3d83eb6a52699aab/Research-Environment/Screenshot%202026-09-01%20010021.png)

Now create the research directories:

mkdir targets

mkdir reports

mkdir notes

mkdir evidence

mkdir scripts

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/080aeecb6b8c3783fdd4f272c506527ebd6e78ab/Research-Environment/Screenshot%202026-09-01%20010150.png)

Check them run: Get-ChildItem

You should have:
Vulnerability-Research-Lab
│
├── targets
├── reports
├── notes
├── evidence
└── scripts

**Create our Python environment**

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/93f624242fbaed999d8b9d4a416335d8eafb622e/Research-Environment/Screenshot%202026-09-01%20010636.png)

From: PS C:\Users\eelve\Vulnerability-Research-Lab>

Run: python -m venv .venv

Then: Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass

Activate it:.venv\Scripts\Activate.ps1

You should now see: (.venv) PS C:\Users\eelve\Vulnerability-Research-Lab>

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/f06e5111567ca9aa33e4876ef9242bd2e34d6357/Research-Environment/Screenshot%202026-09-01%20011005.png)

Verify Python run: python --version

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/a12024543fbe256f8127964b0da8898e165fdf83/Research-Environment/Screenshot%202026-09-01%20011810.png)

Verify Git run: git --version

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/530a0f319a763f7efa8081c6e275869dc0981805/Research-Environment/Screenshot%202026-09-01%20012444.png)

Run:git init

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/318aa686edf715ff641bd28baa1a79bd99a8f424/Research-Environment/Screenshot%202026-09-01%20012653.png)

Create .gitignore run: notepad .gitignore
In the note pad past this and save it. Close the not pad

to create private research directories run:
mkdir private

mkdir draft-disclosures

Now check run: git status

Before committing, let's also make sure RESEARCH_RULES.md exists and run: Test-Path RESEARCH_RULES.md

If you get:don't commit yet. We'll create RESEARCH_RULES.md next.

From your current PowerShell window, run: notepad RESEARCH_RULES.md

Notepad will ask if you want to create a new file. Click Yes.

Paste this into it:

Save and close the note pad

Verify it in PowerShell, run: Test-Path RESEARCH_RULES.md

If it's true, run: git status

Add the research rules run: git add RESEARCH_RULES.md

The run: git status

You should see 

Changes to be committed:
        new file:   .gitignore
        new file:   RESEARCH_RULES.md

Make your first commit run: git commit -m "Set up vulnerability research environment"

You should get output showing something similar to:

2 files changed

create mode 100644 .gitignore

create mode 100644 RESEARCH_RULES.md

Verify run: git status

We want:nothing to commit, working tree clean

Next we'll Install Semgrep

Since your Python virtual environment is active, first try running: python -m pip install semgrep

After installation completes, verify it and run:semgrep --version

Save your Python dependencies, run: python -m pip freeze > requirements.txt

Verify the file: Get-Content requirements.txt

You should see semgrep among the packages.

add and commit it run: git add requirements.txt
git commit -m "Add Semgrep static analysis tooling"

Verify run: git status

We want: nothing to commit, working tree clean

Create a CodeQL tools folder run:  

mkdir C:\
to Verify run: Get-ChildItem C:\Tools

You should see: CodeQL

Download the official CodeQL bundle from Official GitHub CodeQL bundle releases

Download codeql-bundle-win64.tar.gz

Open PowerShell and verify that Windows can see it, run: Get-ChildItem "$HOME\Downloads\codeql-bundle-win64.tar.gz"

Before extracting CodeQL, First make sure the destination exists, Run: New-Item -ItemType Directory -Force -Path "C:\Tools\CodeQL"
mkdir C:\Tools\CodeQL

Now extract the bundle run: tar -xzf "$HOME\Downloads\codeql-bundle-win64.tar.gz" -C "C:\Tools\CodeQL"

Then check what was extracted run: Get-ChildItem "C:\Tools\CodeQL"

Next check for the executable run: Test-Path "C:\Tools\CodeQL\codeql\codeql.exe"

We want: True

run CodeQL directly for the first time and add it to your Windows PATH so you can simply type: codeql version

Add CodeQL to PATH permanently Run this in PowerShell:
$codeqlPath = "C:\Tools\CodeQL\codeql"
$currentUserPath = [Environment]::GetEnvironmentVariable("Path", "User")

if ($currentUserPath -notlike "*$codeqlPath*") {
    [Environment]::SetEnvironmentVariable(
        "Path",
        "$currentUserPath;$codeqlPath",
        "User"
    )
} 

Then close PowerShell completely and reopen it.

Return to your project run: cd C:\Users\eelve\Vulnerability-Research-Lab

cd C:\Users\eelve\Vulnerability-Research-Lab

Reactivate your virtual environment run:

Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.venv\Scripts\Activate.ps1

Now test: codeql version

After that, I’d do one final verification: codeql resolve languages

Your output shows support for languages including C/C++, C#, Go, Java, JavaScript, Python, Ruby, Rust, Swift, XML, and YAML.
