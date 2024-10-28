# zenith

This repository contains the Zenith website: <https://zenithhacks.org/>

## Contribution process

### I'm not part of the Zenith orga team

No worries! For any substantial changes, please discuss in the [#zenith-bts channel on the Slack](https://hackclub.slack.com/archives/C07HX4VJXUP) or open a new issue.

### I'm a Zenith team member

Coordinate with Leo before opening a PR.

## Get started

```
bun run dev -- --open  # opens website in your browser (hot reloads)
bun run build          # builds the website
```

For specific situations:

```
make favicon           # generate favicon.ico
make fonts             # generate font subsets
```

## Guidelines

- Use [Bun](https://bun.sh) as your package manager.
- Use meaningful CSS class names. Do not use Tailwind.
- Avoid using px.
- Without good reason, do not override the default text size.

## Compatibility

The built website **must**:

- Be compatible with Baseline 2023 browsers.
- Have all features work without JavaScript enabled, unless it's simply unviable to do so.
- Meet Lighthouse targets. Every metric should be above 95.
- Support reduced motion
- Comply with the WCAG AA checklist (pending)
