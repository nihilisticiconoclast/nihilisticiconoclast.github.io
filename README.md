# nihilisticiconoclast.github.io

The landing page for my GitHub Pages projects: a live index that lists every
public repository with Pages enabled and links straight to each site.

The grid is generated at load time from the GitHub REST API — there is no build
step and no hand-maintained list. Each card shows the repository name, the
opening paragraph of its README (falling back to the GitHub description), the
last-updated date, and a link to the source. The home repository itself is
hidden, as are forks and archived repositories.

## How it works

- `index.html` fetches `https://api.github.com/users/nihilisticiconoclast/repos`,
  keeps the public, Pages-enabled, non-fork, non-archived repositories, and
  renders one card per repo.
- Blurbs are read from
  `raw.githubusercontent.com/<user>/<repo>/<branch>/README.md` — the **first
  prose paragraph**. So the opening paragraph of every README in these repos is
  public-facing copy: keep it tight and self-contained.
- The unauthenticated GitHub API allows 60 requests/hour per IP; if that limit
  is reached the page says so and recovers on its own.

## Design

Built in the in-house **Tunnel** aesthetic (see
[`cuddly-lamp`](https://github.com/nihilisticiconoclast/cuddly-lamp)): the locked
chart-paper palette and Fraunces / Public Sans / IBM Plex Mono type, hard edges,
no shadows or gradients. The locked layer and the signature generator are
**linked from cuddly-lamp's CDN, never inlined**, so a design-system update
propagates here automatically. The fixed house mark sits in the masthead and a
single per-page doodle is tucked into the margin behind the content.

No secrets, no build, no dependencies beyond the CDN-hosted Tunnel assets and the
public GitHub API.
