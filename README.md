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

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/a8470c5cc285f7fa99ba3ee009963e833edd280d/Screenshot%202026-09-01%20201611.png)

In the note pad past this and save it. Close the not pad

![image alt](https://github.com/Kevinolee1/Research-Environment/blob/de8e8b1bbcea9c87e8eed9641b221fed80713cdf/Research-Environment/Screenshot%202026-09-01%20012932.png)

to create private research directories run:
mkdir private

mkdir draft-disclosures

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/dd281bcabe238302ddf88e6f188c81cce2a4b2f0/Research-Environment/Screenshot%202026-09-01%20013205.png)

Now check run: git status

Before committing, let's also make sure RESEARCH_RULES.md exists and run: Test-Path RESEARCH_RULES.md

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/3b4b8f61e076ea2c50947e75efa90f332d070e69/Research-Environment/Screenshot%202026-09-01%20013525.png)

If you get false, don't commit yet. We'll create RESEARCH_RULES.md next.

![image alt](https://github.com/Kevinolee1/Research-Environment/blob/492e41a690bebf4e7a075a4934285825268bd700/Research-Environment/Screenshot%202026-09-01%20013849.png)

From your current PowerShell window, run: notepad RESEARCH_RULES.md

Notepad will ask if you want to create a new file. Click Yes.

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/b76b42d220c490745d6567d2d11b0701a7744f8a/Screenshot%202026-09-01%20201328.png)

Paste this into it:

Save and close the note pad

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/5739fb236d9367600bad87af40cff71ee8ee7801/Research-Environment/Screenshot%202026-09-01%20014038.png)

Verify it in PowerShell, run: Test-Path RESEARCH_RULES.md

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/ae07877243d568d2a4211c414aba5cfbf3e4d4a8/Research-Environment/Screenshot%202026-09-01%20014453.png)

If it's true, run: git status

You should see 

Changes to be committed:
        new file:   .gitignore
        new file:   RESEARCH_RULES.md

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/e76a8ae5d42042056abde2f8225ef237578d8f66/Research-Environment/Screenshot%202026-09-01%20014728.png)

Make your first commit run: git commit -m "Set up vulnerability research environment"

You should get output showing something similar to:

2 files changed

create mode 100644 .gitignore

create mode 100644 RESEARCH_RULES.md

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/5a2a86eb0e5c1e6e39e8cbb559cce1aee2d918e8/Research-Environment/Screenshot%202026-09-01%20014936.png)

Verify run: git status

We want:nothing to commit, working tree clean

Next we'll Install Semgrep

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/e87c6e2729cbb6547f3780b67e243159c9387d71/Research-Environment/Screenshot%202026-09-01%20015824.png)

Since your Python virtual environment is active, first try running: python -m pip install semgrep

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/8a3d73c3d62457dcd512e344e3a134f5cd110b2a/Research-Environment/Screenshot%202026-09-01%20020045.png)

After installation completes, verify it and run:semgrep --version

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/9cf769157a84ccba09fe4e7b6946c7c3652efff0/Research-Environment/Screenshot%202026-09-01%20020353.png)
Save your Python dependencies, run: python -m pip freeze > requirements.txt

![image alt](https://github.com/Kevinolee1/Research-Environment/blob/e13145965686c10f589092acdda29a5b0eab83e4/Research-Environment/Screenshot%202026-09-01%20020525.png)

Verify the file: git-Content requirements.txt

You should see semgrep among the packages.

add and commit it run: git add requirements.txt
git commit -m "Add Semgrep static analysis tooling"

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/2cbb5f67c09323a58f4695aa00eca08db3c251bf/Research-Environment/Screenshot%202026-09-01%20020620.png)

Verify run: git status

We want: nothing to commit, working tree clean

![image alt](https://github.com/Kevinolee1/Research-Environment/blob/505f3758340ff21d42b0a5e5b22296ee869f8b68/Research-Environment/Screenshot%202026-09-01%20020952.png)

Create a CodeQL tools folder run:  

mkdir C:\

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/b9355efc426dce4e0295ef3834d88dd47e9810b8/Research-Environment/Screenshot%202026-09-01%20021050.png)

to Verify run: Get-ChildItem C:\Tools

You should see: CodeQL

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/40165af3d10173ea0f954eae80f36aa95bcfeab9/Research-Environment/Screenshot%202026-09-01%20021731.png)

Download the official CodeQL bundle from Official GitHub CodeQL bundle releases

Download codeql-bundle-win64.tar.gz

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/056f904198510359329e3d5e84f4c5b34e504371/Research-Environment/Screenshot%202026-09-01%20022148.png)

Open PowerShell and verify that Windows can see it, run: Get-ChildItem "$HOME\Downloads\codeql-bundle-win64.tar.gz"

Before extracting CodeQL, First make sure the destination exists, Run: New-Item -ItemType Directory -Force -Path "C:\Tools\CodeQL"
mkdir C:\Tools\CodeQL

![image alt](https://github.com/Kevinolee1/Research-Environment/blob/6ccd555a5c46ba3e4bb4049cbb0cb9f03b049756/Research-Environment/Screenshot%202026-09-01%20024139.png)

Now extract the bundle run: tar -xzf "$HOME\Downloads\codeql-bundle-win64.tar.gz" -C "C:\Tools\CodeQL"

Then check what was extracted run: Get-ChildItem "C:\Tools\CodeQL"

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/af9d9c7345131032822b106cb20c94b6ea411b07/Research-Environment/Screenshot%202026-09-01%20024240.png)

Next check for the executable run: Test-Path "C:\Tools\CodeQL\codeql\codeql.exe"

We want: True

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/5118057e256c8e5c0dcd8b7836a01e467d2a1629/Research-Environment/Screenshot%202026-09-01%20024616.png)

run CodeQL directly for the first time and add it to your Windows PATH so you can simply type: codeql version

Add CodeQL to PATH permanently Run this in PowerShell:

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/8ccaeb520dc269a5938bcf2e843ae731adf23814/Research-Environment/Screenshot%202026-09-01%20024937.png)

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

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/56c07c8400d9999eb6ba99a4e75e54c5974b737a/Research-Environment/Screenshot%202026-09-01%20025418.png)

Return to your project run: cd C:\Users\eelve\Vulnerability-Research-Lab

cd C:\Users\eelve\Vulnerability-Research-Lab

Reactivate your virtual environment run: Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.venv\Scripts\Activate.ps1

Now test: codeql version

![Image alt](https://github.com/Kevinolee1/Research-Environment/blob/1b1dc3e427a983040179c505ba062f8233c433db/Research-Environment/Screenshot%202026-09-01%20025604.png)

After that, I’d do one final verification: codeql resolve languages

Your output shows support for languages including C/C++, C#, Go, Java, JavaScript, Python, Ruby, Rust, Swift, XML, and YAML.
