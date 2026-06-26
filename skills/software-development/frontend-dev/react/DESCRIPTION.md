# .agents/skills/react

A collection of AI skills for React development, curated from the best public repositories.

## Skills

| Folder                                                                 | Source | Purpose |
|------------------------------------------------------------------------|--------|---------|
| [`vercel-react-best-practices/`](vercel-react-best-practices/SKILL.md) | vercel-labs/agent-skills | 70 React/Next.js performance rules across 8 categories (waterfalls, bundle, SSR, re-renders...) |
| [`beforemerge-react-review/`](beforemerge-react-review/SKILL.md)      | BeforeMerge/beforemerge-skills | React code review: XSS, re-renders, architecture, quality (with CWE mapping) |
| [`beforemerge-nextjs-review/`](beforemerge-nextjs-review/SKILL.md)    | BeforeMerge/beforemerge-skills | Next.js code review: security (OWASP), RSC, server actions, architecture |
| [`softaworks-react-dev/`](softaworks-react-dev/SKILL.md)              | softaworks/agent-toolkit | React 18/19 + TypeScript: hook/event typing, generic components, Server Components, routing |
| [`react-router-framework-mode/`](react-router-framework-mode/SKILL.md) | remix-run/agent-skills | React Router v7 framework mode: file-based routing, loaders, actions, SSR/SPA |
| [`react-router-data-mode/`](react-router-data-mode/SKILL.md)          | remix-run/agent-skills | React Router data mode: createBrowserRouter, loaders, actions, optimistic UI |
| [`react-router-declarative-mode/`](react-router-declarative-mode/SKILL.md) | remix-run/agent-skills | React Router declarative mode: BrowserRouter, Routes, NavLink, useParams |
| [`react-native-best-practices/`](react-native-best-practices/SKILL.md) | callstackincubator/agent-skills | React Native performance: FPS, TTI, bundle size, Hermes, FlashList, Reanimated |
| [`mindrally-react/`](mindrally-react/SKILL.md)                        | Mindrally/skills | Core React rules: component patterns, hooks, Tailwind, TypeScript |
| [`mindrally-nextjs-react-typescript/`](mindrally-nextjs-react-typescript/SKILL.md) | Mindrally/skills | Next.js App Router + TypeScript + Shadcn UI + Tailwind: conventions and optimization |

## Which one to choose

- **New React/Next.js project** → `vercel-react-best-practices` + `mindrally-nextjs-react-typescript`
- **Code review before merge** → `beforemerge-react-review` (React) or `beforemerge-nextjs-review` (Next.js)
- **React 18/19 component typing** → `softaworks-react-dev`
- **Routing** → one of the three `react-router-*` depending on the mode
- **React Native** → `react-native-best-practices`

