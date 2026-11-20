# cicd-compliance

What the information system owner keeps for IT Security, next to [cicd-ref-arch](https://forge.goblincorps.com/ffwf/cicd-ref-arch) and [cicd-dashboard](https://forge.goblincorps.com/ffwf/cicd-dashboard). **Demo data.**

| Path | What | Written by |
|---|---|---|
| `catalogs/` | NIST SP 800-53 Rev 5.2.0 with 800-53A objectives, cut to the profiles' controls (OSCAL 1.2.3) | `tools/oscal.py excerpt` |
| `profiles/` | Control selections | security |
| `apps/<app>/app.yaml` | The application as its owner describes it: profile, impact, release rule, promotion requirement | owner |
| `apps/<app>/component.yaml` | The owner's sysadmin layer (layer 3): statements the pipeline can't make | owner's sysadmins |
| `ledger/<app>.yaml` | Findings imported from IT Security; each one is a failing test until its check passes or the owner accepts the risk | dashboard, as the person importing |
| `advisories/` | Vulnerability announcements entered by hand, matched against every live SBOM | dashboard |
| `releases/<id>/` | Packages released to IT Security: unaltered records with sha256 manifests | dashboard, merged by a second person |

The pipeline's own statements (layer 1) are in cicd-ref-arch `oscal/platform.yaml`; an app may add layer 2 in its own repo (`oscal/component.yaml`), never required.

Nothing here is sent to IT Security automatically. A release is a pull request; merging it is the release, and git history is the release log.
