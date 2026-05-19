# Firebase Hosting Deployment Guide

Project ID: `pp-academic-skill`

## Recommended Setup

Use GitHub as the source repository and Firebase Hosting as the public website.

```text
GitHub repo
  -> index.html
  -> manifest.json
  -> packages/*.zip
  -> firebase.json
  -> .firebaserc
Firebase Hosting
  -> public URL for lab members to download skills
```

## First-Time Manual Deploy

Run these commands from this folder:

```powershell
npm install -g firebase-tools
firebase login
firebase deploy --only hosting --project pp-academic-skill
```

After deploy, Firebase will print URLs like:

```text
https://pp-academic-skill.web.app
https://pp-academic-skill.firebaseapp.com
```

## Better Long-Term Workflow

1. Create a GitHub repo, for example `pp-academic-skill-site`.
2. Put this whole folder's contents into that repo.
3. Push to GitHub.
4. In Firebase Console, open project `pp-academic-skill`.
5. Go to `Build -> Hosting`.
6. Connect the GitHub repo or run:

```powershell
firebase init hosting:github
```

7. Let Firebase create a GitHub Actions workflow.
8. Future changes can be deployed by pushing to the main branch.

## Important Notes

- Use Firebase **Hosting**, not App Hosting. This is a static site.
- Keep `firebase.json` and `.firebaserc` in GitHub, but they are excluded from the public hosted files.
- The `packages/` folder contains downloadable ZIP files. Regenerate ZIPs whenever skills change.
- Skills marked as `Needs local setup` require users to adapt paths for their own Zotero/Obsidian setup.
- Firebase Hosting is public by default. Do not publish private notes, private PDFs, API keys, or personal data.
