# readseal-site

The public pages the Atlassian Marketplace asks for: documentation, privacy policy, security summary and
support. Plain HTML and one stylesheet, served by GitHub Pages. No build step, no framework, no external
request: the pages load nothing but themselves.

| Page | URL once published | Used by |
|---|---|---|
| `index.html` | `/` | The listing's home link |
| `docs.html` | `/docs.html` | The listing's documentation URL |
| `privacy.html` | `/privacy.html` | The listing's privacy policy URL, required |
| `security.html` | `/security.html` | The Privacy and Security tab, and buyers' questionnaires |
| `support.html` | `/support.html` | The listing's support URL |

## Before publishing

1. **Fill the last placeholder** in `privacy.html`: `[[CODE POSTAL ET VILLE]]`, in "Who we are" and in
   "Contact". The legal form, the street and the SIRET are in.
2. **Have the privacy policy read by a lawyer**, along with the question of whether a data processing addendum
   is needed at all: the app holds account identifiers, yet everything stays inside the customer's Atlassian
   site and OwlWorks has no access to it.
3. **Create the two mailboxes**: `support@owlworks.dev` and `security@owlworks.dev`, or point them at
   `contact@owlworks.dev`.

## Publishing

```bash
gh repo create readseal-site --public --source=. --remote=origin --push
```

Then in the repository: Settings, Pages, Source "Deploy from a branch", branch `main`, folder `/ (root)`.
The pages appear at `https://<account>.github.io/readseal-site/` within a minute or two.

A custom domain later (`readseal.owlworks.dev`, say) only takes a `CNAME` file here and one DNS record; the
Marketplace URLs would then be changed once, in the listing.

## Keeping it honest

Every factual claim on these pages matches what the app does today: the scopes it asks for, what it stores,
what it refuses, and its known limits. When the app changes, these pages change in the same breath, and the
claims are the ones checked in `docs/01-read-confirmations/security.md` in the documentation folder.
