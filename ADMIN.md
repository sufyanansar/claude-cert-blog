# Admin guide

Notes for the repo owner. Nothing here is automated — every step is deliberate.

## Approving a collaborator request

Requests arrive as GitHub issues labelled `join-request` (template:
`.github/ISSUE_TEMPLATE/join-request.yml`, linked from the Team page).

List open ones:

```
gh issue list --label join-request
```

To approve a request:

1. **Add them to the Team page.** Append an entry to `_data/authors.yml`. The key
   is what goes in a post's `author:` field, so keep it short and lowercase:

   ```yaml
   jdoe:
     name: Jane Doe
     github: janedoe
     bio: Working through the tool-use track
   ```

2. **Invite them to the repo.** `push` lets them commit posts directly:

   ```
   gh api -X PUT repos/sufyanansar/claude-cert-blog/collaborators/janedoe -f permission=push
   ```

   Use `permission=triage` instead if you'd rather they open pull requests than
   push to `main`.

3. **Commit and close.**

   ```
   git add _data/authors.yml && git commit -m "Add Jane Doe as a collaborator" && git push
   gh issue close <number> --comment "Invite sent — welcome aboard."
   ```

To decline, just close the issue with a comment; nothing else to undo.

## Removing a collaborator

```
gh api -X DELETE repos/sufyanansar/claude-cert-blog/collaborators/janedoe
```

Then remove their block from `_data/authors.yml`. Their existing posts stay
published; the Team page simply stops listing them.

## Post submissions

The `/write/` form emails submissions to `submissions_email` in `_config.yml`
(currently the owner's address) via formsubmit.co. To publish one, save the
attached markdown as `_posts/YYYY-MM-DD-slug.md`, check the front matter
`author:` matches a key in `_data/authors.yml`, then commit and push. GitHub
Pages rebuilds automatically.
