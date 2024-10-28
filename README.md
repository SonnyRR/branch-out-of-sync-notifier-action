# 📣 Branch out-of-sync notifier action 

### 🖋 Description
A github action that notifies pull-request owners that their base branch is behind the target branch via a comment on the pull request itself.

It utilizes tools such as `git` and [github-script](https://github.com/actions/github-script) to write workflows in `JavaScript`.

![image](https://github.com/user-attachments/assets/b4e7b947-fef0-4250-853e-09c48afcb98e)


### 🔨 Setup
Below is the bare minimum step in order to utilize this action, by default each of the inputs has a default value.
```yml
name: Check if base branch is synchronized

on:
  pull_request:
    types: [opened, synchronize, reopened, edited]

jobs:
  check-branch-sync:
    name: Check if head & base branches are in sync
    runs-on: ubuntu-latest

    steps:
      - name: Notify PR owner if branch is out of sync
        uses: SonnyRR/branch-out-of-sync-notifier-action@0.1.1
```

### 📩 Inputs
```yml
base-ref:
  description: "The base git reference, used for comparison."
  default: ${{ github.event.pull_request.base.ref }}
  required: true
head-ref:
  description: "The head git reference, used for comparison."
  default: ${{ github.event.pull_request.head.ref }}
  required: true
request-owner:
  description: "The owner of the pull request"
  default: ${{ github.event.pull_request.user.login }}
  required: true
request-number:
  descripton: "The pull request number"
  default: ${{ github.event.pull_request.number }}
  required: true
```
