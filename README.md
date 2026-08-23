<div align="center">

# \\\ ~ 🐢⚡ KAME — API Rotation ⚡🐢 ~ //

### One engine. One port per host. Your agent stops at the first 429 — mine does not.

[![Agent Zero port](https://img.shields.io/github/stars/Kame696/kame-api-rotation-for-agent-zero?label=Agent%20Zero%20port&style=social)](https://github.com/Kame696/kame-api-rotation-for-agent-zero)
[![Hermes port](https://img.shields.io/github/stars/Kame696/kame-api-rotation-for-hermes?label=Hermes%20port&style=social)](https://github.com/Kame696/kame-api-rotation-for-hermes)
[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](#-licence)
[![Version](https://img.shields.io/badge/both_ports-1.2.0-blue.svg)](#-version-parity)
[![Donate Bitcoin](https://img.shields.io/badge/donate-bitcoin-f7931a.svg)](#-support-the-project)

<img src="https://raw.githubusercontent.com/Kame696/kame-api-rotation-for-agent-zero/main/webui/kame_banner.jpg" width="560" alt="KAME — Key-Aware Management Engine" />

### *4P1 R0T4T10N — 4FRE3D0M*

**This repository is the front door.** The code lives in one repository per host —
pick yours below.

</div>

---

## 🎯 The problem, in one paragraph

You own several API keys. Your agent uses one of them. When that key hits a rate
limit, runs out of daily quota, or the provider has a bad ten minutes, the call
fails and **your turn ends** — while the other fourteen keys sit there, healthy,
untouched.

**KAME picks a key per call and, when a call fails, tries the next one instead of
giving up.** It reads the provider's own retry timing and rests that key for
exactly that long. It tells a per-minute throttle from a daily cap. It remembers
which model spent which quota. And when the whole pool is cooling, it waits for
the exact moment one recovers rather than burning requests proving they are still
down.

There is **no provider allowlist anywhere in it.** Every decision is made on
evidence in the response — retry timing, rate-limit headers, the shape of the
error body. A provider released next year is covered by the same rule.

---

## 🚪 Pick your host

<table>
<tr>
<td width="50%" valign="top">

### 🅰️ Agent Zero

**[kame-api-rotation-for-agent-zero →](https://github.com/Kame696/kame-api-rotation-for-agent-zero)**

Install through the **Plugin Hub** inside the app, or drop the folder into
`/a0/usr/plugins/`.

Verified end-to-end on **v1.14, v1.20, v2.1, v2.4, v2.7, v2.8 and v2.10** —
one code path for every one of them.

</td>
<td width="50%" valign="top">

### 🅷 Hermes

**[kame-api-rotation-for-hermes →](https://github.com/Kame696/kame-api-rotation-for-hermes)**

```bash
hermes plugins install \
  Kame696/kame-api-rotation-for-hermes/hermes-kame-api-rotation
```

Built against **Hermes v0.20.x**, Python 3.9+, **no third-party packages at all**.

</td>
</tr>
</table>

---

## 🔢 Version parity

The two ports share a version line on purpose:

> **The same MAJOR.MINOR means the same generation of behaviour on both hosts.
> The patch number moves independently.**

So `1.2.x` on Agent Zero and `1.2.x` on Hermes are the same KAME, wearing the
clothes of two different hosts. A gap in the line is not a mistake — it means one
host had a problem the other one does not have. **There is no 1.1.x on Agent
Zero**, because 1.1.0–1.1.3 fixed stream handling that Agent Zero has owned
itself since 1.0.9, so there was nothing to port. The lines rejoin at 1.2.0.

| | Agent Zero | Hermes |
|---|---|---|
| Current | **1.2.0** | **1.2.0** |
| Picks the key per call | ✅ | ✅ |
| Reads the provider's own retry timing | ✅ | ✅ |
| Daily cap told apart from a per-minute throttle | ✅ | ✅ |
| Health remembered per `provider:model` | ✅ | ✅ |
| Invalid key quarantined instead of ending the run | ✅ | ✅ |
| Waits out a fully-cooled pool, and says so on screen | ✅ | ✅ |
| Continues an answer the provider cut mid-stream | — *(host owns the stream)* | ✅ |
| Repairs merged Gemini tool calls | — *(host owns the stream)* | ✅ |
| Bulk key import from chat (`/kame-keys`) | — | ✅ |
| Status chip + panel in a desktop shell | — | ✅ |
| Settings screen inside the host's own UI | ✅ | ✅ |

The dashes are not missing features. They are jobs the other host already does
itself — and the whole design rule of this project is that **KAME does not
re-implement its host.**

---

## 🧠 The one design rule

Since 1.0.9, KAME **only chooses the key**. The request, the stream, the parsing
and the result belong to the host, untouched.

That is the reason a single build survives seven Agent Zero versions across two
major lines. The earlier design had a copy of the host's model call living inside
the plugin, and that copy went stale on every release — a permanent maintenance
tax paid by whoever was still using it. Deleting the copy deleted the tax.

---

## ❤️ Support the project

KAME is free, MIT, and written by one person against real quotas on a real free
tier. No company, no telemetry, nothing to upsell.

If it saved you a run — or an afternoon — a tip keeps it going:

**Bitcoin** — `36BGYhMEVFgY8PLGMVux93pjGt92KVM6dJ`

*Any amount helps, genuinely.* And if money is not on the table, a ⭐ on either
port costs nothing and helps other people find it.

---

## 📜 Licence

MIT, both ports. See each repository's `LICENSE`.

---

<div align="center">

Built by [**KAME**](https://github.com/Kame696) · Discord `kame055856`

*Not affiliated with Agent Zero or Nous Research. Just a person with too many
API keys and not enough quota.*

</div>
