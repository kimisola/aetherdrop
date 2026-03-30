# Memo Capture

iOS Shortcut that captures links and notes from any app's Share Sheet and saves them to a GitHub repo — powered by GitHub Actions.

```
Shortcut → GitHub API (repository_dispatch) → GitHub Actions → commit to repo
```

## Setup

### 1. Create a GitHub Fine-grained Token

1. Go to GitHub → Settings → Developer settings → **Fine-grained personal access tokens**
2. Token name: anything you like (e.g. `memo-capture`)
3. Repository access: **Only select repositories** → select your target repo
4. Permissions: **Contents** → **Read and write**
5. Generate → copy the token

### 2. Add the GitHub Actions Workflow

Copy [`memo-append.yml`](memo-append.yml) to your repo's `.github/workflows/` directory.

The default config appends entries to `memo/inbox.md`. Edit the `FILE` variable in the workflow if you want a different path.

### 3. Install the Shortcut

[Download Memo Capture](https://www.icloud.com/shortcuts/896bd29767d94e54863b32c8059f9fe0)

After installing, open the shortcut and replace the two placeholders:

| Placeholder | Replace with |
|---|---|
| `YOUR_GITHUB_REPO_URL` | `https://api.github.com/repos/{owner}/{repo}/dispatches` |
| `YOUR_GITHUB_TOKEN` | The token you created in step 1 |

## Usage

1. In any app, tap **Share** → select **Memo Capture**
2. Enter a note (or leave blank)
3. Done — the entry is committed to your repo

## Customization

- **Target file path**: Edit the `FILE` variable in `memo-append.yml`
- **Entry format**: Edit the `echo` line in the workflow (default: `- {date} [{note}]({url})`)
- **Commit message**: Edit the `git commit -m` line
