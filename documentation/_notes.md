# Notes

https://cilogon.org/

## CYVERSE

Min memory 16
CPU COres 4

sk-iSOxZN_hc6Sq20aCaAe6UA

sk-Hnb8WzsNtUQyf5ZKSqwjoQ

## Places to get API access

- AI VERDE
- Nautilus Cluster

https://github.com/CU-ESIIL/LLM_lesson_exemplar.git

I am most interested in fit – can I get along, can I joke, do I feel comfortable with the other members of the group.

I am most interested in a question that focuses on building skills with AI workflows at present.

~/Rprojects/esiil-innovation-summit-2026/

groups: cannot find name for group ID 1000
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git remote -v
origin https://github.com/CU-ESIIL/LLM_lesson_exemplar (fetch)
origin https://github.com/CU-ESIIL/LLM_lesson_exemplar (push)
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git fetch --
unshallow
remote: Enumerating objects: 747, done.
remote: Counting objects: 100% (747/747), done.
remote: Compressing objects: 100% (265/265), done.
remote: Total 683 (delta 445), reused 607 (delta 375), pack-reused 0 (from 0)
Receiving objects: 100% (683/683), 35.27 MiB | 10.35 MiB/s, done.
Resolving deltas: 100% (445/445), completed with 43 local objects.
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git remote add cjt-origin https://github.com/cjtinant/LLM_exemplar.git
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git status
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git pull
Already up to date.
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git pull cjt-origin main
remote: Enumerating objects: 7, done.
remote: Counting objects: 100% (7/7), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 7 (delta 4), reused 7 (delta 4), pack-reused 0 (from 0)
Unpacking objects: 100% (7/7), 4.05 KiB | 828.00 KiB/s, done.
From https://github.com/cjtinant/LLM_exemplar

- branch main -> FETCH_HEAD
- [new branch] main -> cjt-origin/main
  hint: You have divergent branches and need to specify how to reconcile them.
  hint: You can do so by running one of the following commands sometime before
  hint: your next pull:
  hint:
  hint: git config pull.rebase false # merge (the default strategy)
  hint: git config pull.rebase true # rebase
  hint: git config pull.ff only # fast-forward only
  hint:
  hint: You can replace "git config" with "git config --global" to set a default
  hint: preference for all repositories. You can also pass --rebase, --no-rebase,
  hint: or --ff-only on the command line to override the configured default per
  hint: invocation.
  fatal: Need to specify how to reconcile divergent branches.
  (base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git config pull.rebase false
  (base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git pull cjt-origin main
  From https://github.com/cjtinant/LLM_exemplar
- branch main -> FETCH_HEAD
  Committer identity unknown

\*\*\* Please tell me who you are.

Run

git config --global user.email "you@example.com"
git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'jovyan@aa40dd724.(none)')
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git config --global user.email "jtinant@olc.edu"
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git config --global user.name "C. Jason Tinant"
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git pull cjt-origin main
From https://github.com/cjtinant/LLM_exemplar

- branch main -> FETCH_HEAD
  hint: Waiting for your editor to close the file... E1187: Failed to source defaults.vim
  Press ENTER or type command to continue
  Merge made by the 'ort' strategy.
  docs/{data-harmonizer.md => data-harmonizer-1.md} | 66 ++++++++++++++++++++++++++++----------------------------
  1 file changed, 33 insertions(+), 33 deletions(-)
  rename docs/{data-harmonizer.md => data-harmonizer-1.md} (58%)
  (base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git push -u cjt-origin main
  Enumerating objects: 26, done.
  Counting objects: 100% (24/24), done.
  Delta compression using up to 40 threads
  Compressing objects: 100% (13/13), done.
  Writing objects: 100% (18/18), 1.72 KiB | 1.72 MiB/s, done.
  Total 18 (delta 13), reused 8 (delta 5), pack-reused 0
  remote: Resolving deltas: 100% (13/13), completed with 4 local objects.
  To https://github.com/cjtinant/LLM_exemplar.git
  0f824dd..e4fbe1a main -> main
  Branch 'main' set up to track remote branch 'main' from 'cjt-origin'.
  (base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$ git status
  On branch main
  Your branch is up to date with 'cjt-origin/main'.

nothing to commit, working tree clean
(base) jovyan@aa40dd724:~/data-store/LLM_lesson_exemplar$

Set up a Umbutu in Parallels

Claude Code

Read this paper Implent method in R.

College Risk Dashboard
