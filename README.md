<p>
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="brand/png/lockup-white.png">
    <img src="brand/png/lockup-ink.png" alt="Plumb" height="72">
  </picture>
</p>

# Plumb

**Keeps every tenant true.**

Plumb is open-source tenant as code for Microsoft 365 and the services around it. You write down how your tenant should be set up. Plumb saves the live configuration every day, compares it with what you agreed, and an AI agent explains every difference in plain language. It proposes the fix as a pull request, or puts it back on its own where you allowed that.

> **Status: early development.** There is nothing to install yet. Watch or star this repository to follow along.

## How it works

1. **Save:** a daily snapshot of the live configuration, kept in git.
2. **Compare:** live configuration against your desired state.
3. **Explain:** the agent says who changed what, when, and why it matters.
4. **Fix:** depending on the risk it reports, opens a pull request, or restores the approved state.
5. **Verify:** checks again and reports.

## You decide how much it does

| Level | What the agent does | Example |
|---|---|---|
| 0 · Report | Signals and explains | A new app registration with broad permissions |
| 1 · Propose | Opens a pull request, a person approves | A Conditional Access change |
| 2 · Restore | Puts the approved state back, then reports | Mail forwarding switched back on |
| Never automatic | Always a person | Break-glass accounts, anything that can lock people out |

## One rule, every provider

You describe an intent once, for example "files are only shared inside the organisation". Plumb maps it to each provider's own settings and checks them together, including chains across providers, such as whether multi-factor sign-in really applies in every app that signs in through your identity provider.

Planned order: Microsoft 365 first, then Cloudflare and GitHub, then Okta, Google Workspace and Slack. Coverage per setting is published honestly: set and checked, checked only, or documented.

## Principles

- **Read-only first.** Write access only when you choose it.
- **Every change is reviewable.** Pull requests, approvals and a full history in your own repository.
- **Your configuration stays yours.** Your desired state lives in your repository, not in a vendor's portal.
- **Builds on what exists.** Uses Microsoft365DSC, Microsoft's configuration APIs and existing Terraform providers, and fills the gaps.
- **Bring your own AI model.** Not tied to one vendor's agent.

## Licence

[AGPL-3.0](LICENSE). Free to use and change. If you offer Plumb as a service, you share your changes.

## Who builds it

Plumb is built and maintained by [Entelech](https://entelech.ai), forward deployed AI engineers in Venlo, the Netherlands. Questions or want to be an early user: hello@entelech.ai.

Product names mentioned here are trademarks of their owners. Plumb is not affiliated with or endorsed by them.
