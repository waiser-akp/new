# memory new Protocol - Final Specification

**Trigger:** User types `memory new` in any new chat

**Execution:** Single tool call
```
ConfigureReferenceWorkspace(
  action: "add_source",
  source: {
    type: "github-repo",
    gitRepo: {org: "waiser-akp", name: "new"}
  }
)
```

**Result:** Sandbox loads with 10 files from `waiser-akp/new`:

| File | Purpose |
|------|---------|
| package.json | Next 15, React 19, Supabase, Tailwind 4 |
| tsconfig.json | TypeScript config with @/* paths |
| next.config.mjs | Empty Next.js config |
| postcss.config.mjs | Tailwind PostCSS plugin |
| app/globals.css | Single line: `@import "tailwindcss"` |
| app/layout.tsx | Bare HTML shell |
| app/page.tsx | Returns `<main>wilkommen</main>` |
| lib/supabase/client.ts | Browser Supabase client |
| lib/supabase/server.ts | Server Supabase client with cookies |
| .gitignore | node_modules, .next, .env*.local |

**What user sees:** Preview displays "wilkommen"

**What is NOT present:** No shadcn, no radix, no component libraries, no utils.ts, no hooks, no placeholder images, no template bloat

**Time:** ~10 seconds
**Cost:** ~0.01 credits
**Tool calls:** 1

**Philosophy:** Anti-template. Clean slate. Build from raw text and function. Supabase ready when env vars are added. User names everything.
