# Lab 4 — Git & GitHub: Answers

**Question 1 — What does `--global` mean, and what if you leave it out?**
`--global` writes the setting to your user-level config (`~/.gitconfig`), so it applies to every repository you work in on this machine. Without it, Git writes to the local config (`.git/config`) and the setting applies only to the current repository — and if you run it outside any repo, it errors out.

**Question 2 — What appeared in `ls -a` but not `ls`, and what's inside it?**
The hidden `.git/` directory appeared. It holds the entire repository database and metadata — `config`, the `HEAD` file, `objects/` (your commits and file snapshots), `refs/` (branches and tags), and `hooks/`.

**Question 3 — Roughly how many files is Git offering to track, and does anything look like code you didn't write?**
It's offering hundreds of entries, the vast majority of them inside `.venv/`. Yes — everything under `.venv/` is third-party package code I never wrote, which is exactly what shouldn't go into the repo.

**Question 4 — What disappeared after creating `.gitignore`?**
Everything under `.venv/` (plus `__pycache__/`, `.pyc` files, and `.DS_Store`) vanished from the untracked list. Now `git status` only shows my own files and the new `.gitignore`.

**Question 5 — Should `.gitignore` be committed or ignored? Why?**
It should be committed. It's a small, human-written project file that documents which files the repo ignores, so every collaborator who clones gets the same ignore rules automatically — ignoring it would defeat its purpose.

**Question 6 — Which two headings did `README.md` move between, and what happened to it?**
It moved from "Untracked files" to "Changes to be committed." In the three-places model, it went from the working directory into the staging area (the index), ready to be saved in the next commit.

**Question 7 — What did Git print after the commit, and how many files changed?**
Git printed the branch and short commit hash, the commit message, and a summary line like `N files changed, M insertions(+)`. (Check your own output — the number is whatever your first commit staged.)

**Question 8 — What are the first seven characters called, and what are they for?**
They're the abbreviated commit hash (the short SHA). It's a unique identifier for that commit, used to reference it in commands like `git show` or `git checkout` without typing the full 40-character hash.

**Question 9 — What are the four steps of the loop?**
Edit a file, stage it with `git add`, save it with `git commit`, and check the result with `git status` / `git log`.

**Question 10 — Why does `README.md` get a special name and place?**
GitHub automatically renders the root `README.md` as the repository's landing page, so the name and location are a convention that makes it the project's front door. Any file named `notes.md` would just sit in the file list, unrendered.

**Question 11 — What did `gh auth login` do so you're not asked for a password?**
It authenticated me with GitHub and stored a credential (an access token) through Git's credential helper. From then on Git pulls that token automatically instead of prompting for a username and password.

**Question 12 — What's showing on the GitHub front page, and why that file?**
The `README.md` is showing, rendered as formatted text. GitHub automatically displays the root README on the repository's front page.

**Question 13 — Did pushing change your local history?**
No. Pushing only uploads existing commits to the remote — my local commits, their hashes, messages, and order are all unchanged. The only thing it updates is the remote-tracking pointer `origin/main`.

**Question 14 — Private repo vs. no repo on GitHub at all?**
A private repo exists on GitHub's servers: it's backed up, has a URL, and can be shared with people you invite as collaborators. A repo that doesn't exist on GitHub has no remote copy at all — no off-site backup, no link, and nothing anyone else can access even with permission.
