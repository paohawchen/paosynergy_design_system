# PaoSynergy Design System Package

這份文件包含三個交付項目：

1. Tailwind theme config
2. Figma Tokens JSON
3. React component library

---

# 1. Tailwind Theme Config

建議檔案：`tailwind.config.ts`

```ts
import type { Config } from "tailwindcss";

const config: Config = {
  darkMode: ["class"],
  content: [
    "./pages/**/*.{ts,tsx}",
    "./components/**/*.{ts,tsx}",
    "./app/**/*.{ts,tsx}",
    "./src/**/*.{ts,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        ocean: {
          abyss: "#021B3D",
          deep: "#063B65",
          lagoon: "#2698E6",
        },
        aqua: {
          glow: "#3CEBFF",
          bubble: "#73F5FF",
          mist: "#A7EFFF",
          foam: "#EFFFFF",
        },
        violet: {
          orb: "#6656FF",
        },
      },
      backgroundImage: {
        "ocean-radial":
          "radial-gradient(circle at 50% 48%, rgba(63,239,255,.55), transparent 0 16%, rgba(3,38,72,.78) 38%, #021B3D 76%)",
        "surface-light":
          "linear-gradient(to bottom, rgba(115,245,255,.55), rgba(2,27,61,.05))",
        "primary-glow":
          "linear-gradient(to right, #A7F3FF, #73F5FF, #3CEBFF)",
        "primary-glow-hover":
          "linear-gradient(to right, #73F5FF, #A7F3FF, #6656FF)",
        "glass-panel":
          "linear-gradient(135deg, rgba(255,255,255,.12), rgba(255,255,255,.03))",
        "violet-glass":
          "linear-gradient(135deg, rgba(102,86,255,.2), rgba(60,235,255,.1))",
      },
      boxShadow: {
        "glow-sm": "0 0 24px rgba(60,235,255,.22)",
        "glow-md": "0 0 42px rgba(60,235,255,.35)",
        "glow-lg": "0 0 64px rgba(60,235,255,.62)",
        "violet-glow": "0 0 54px rgba(102,86,255,.28)",
        "inner-glow": "inset 0 0 22px rgba(60,235,255,.22)",
        "glass-inset": "inset 0 1px 0 rgba(255,255,255,.12)",
      },
      borderRadius: {
        glass: "2rem",
        pill: "999px",
      },
      textShadow: {
        glow: "0 0 12px rgba(115,245,255,.3)",
      },
      transitionTimingFunction: {
        fluid: "cubic-bezier(.16,1,.3,1)",
      },
      keyframes: {
        floatBubble: {
          "0%, 100%": { transform: "translate3d(0,0,0) scale(1)" },
          "50%": { transform: "translate3d(8px,-18px,0) scale(1.05)" },
        },
        shimmer: {
          "0%": { transform: "translateX(-100%)" },
          "100%": { transform: "translateX(100%)" },
        },
      },
      animation: {
        "float-bubble": "floatBubble 5.5s ease-in-out infinite",
        shimmer: "shimmer .7s ease-out forwards",
      },
    },
  },
  plugins: [
    function ({ matchUtilities, theme }: any) {
      matchUtilities(
        {
          "text-shadow": (value: string) => ({ textShadow: value }),
        },
        { values: theme("textShadow") }
      );
    },
  ],
};

export default config;
```

---

# 2. Figma Tokens JSON

建議檔案：`tokens/paosynergy.tokens.json`

```json
{
  "$schema": "https://tokens.studio/schemas/tokens.json",
  "global": {
    "color": {
      "ocean": {
        "abyss": { "value": "#021B3D", "type": "color" },
        "deep": { "value": "#063B65", "type": "color" },
        "lagoon": { "value": "#2698E6", "type": "color" }
      },
      "aqua": {
        "glow": { "value": "#3CEBFF", "type": "color" },
        "bubble": { "value": "#73F5FF", "type": "color" },
        "mist": { "value": "#A7EFFF", "type": "color" },
        "foam": { "value": "#EFFFFF", "type": "color" }
      },
      "violet": {
        "orb": { "value": "#6656FF", "type": "color" }
      },
      "surface": {
        "glass": { "value": "rgba(255,255,255,0.06)", "type": "color" },
        "glassStrong": { "value": "rgba(255,255,255,0.12)", "type": "color" },
        "cyanTint": { "value": "rgba(115,245,255,0.10)", "type": "color" }
      },
      "text": {
        "primary": { "value": "{color.aqua.foam}", "type": "color" },
        "secondary": { "value": "rgba(239,255,255,0.70)", "type": "color" },
        "label": { "value": "rgba(167,239,255,0.70)", "type": "color" },
        "disabled": { "value": "rgba(239,255,255,0.40)", "type": "color" }
      },
      "border": {
        "subtle": { "value": "rgba(255,255,255,0.10)", "type": "color" },
        "cyan": { "value": "rgba(167,239,255,0.35)", "type": "color" },
        "cyanStrong": { "value": "rgba(167,239,255,0.60)", "type": "color" }
      }
    },
    "spacing": {
      "1": { "value": "4px", "type": "spacing" },
      "2": { "value": "8px", "type": "spacing" },
      "3": { "value": "12px", "type": "spacing" },
      "4": { "value": "16px", "type": "spacing" },
      "5": { "value": "20px", "type": "spacing" },
      "6": { "value": "24px", "type": "spacing" },
      "8": { "value": "32px", "type": "spacing" },
      "10": { "value": "40px", "type": "spacing" },
      "12": { "value": "48px", "type": "spacing" },
      "16": { "value": "64px", "type": "spacing" },
      "24": { "value": "96px", "type": "spacing" }
    },
    "radius": {
      "sm": { "value": "12px", "type": "borderRadius" },
      "md": { "value": "20px", "type": "borderRadius" },
      "lg": { "value": "24px", "type": "borderRadius" },
      "glass": { "value": "32px", "type": "borderRadius" },
      "pill": { "value": "999px", "type": "borderRadius" }
    },
    "typography": {
      "display": {
        "value": {
          "fontFamily": "Inter, ui-sans-serif, system-ui, sans-serif",
          "fontWeight": "900",
          "fontSize": "72px",
          "lineHeight": "1",
          "letterSpacing": "-0.04em"
        },
        "type": "typography"
      },
      "h1": {
        "value": {
          "fontFamily": "Inter, ui-sans-serif, system-ui, sans-serif",
          "fontWeight": "900",
          "fontSize": "64px",
          "lineHeight": "1.05",
          "letterSpacing": "-0.035em"
        },
        "type": "typography"
      },
      "h2": {
        "value": {
          "fontFamily": "Inter, ui-sans-serif, system-ui, sans-serif",
          "fontWeight": "800",
          "fontSize": "40px",
          "lineHeight": "1.1",
          "letterSpacing": "-0.025em"
        },
        "type": "typography"
      },
      "body": {
        "value": {
          "fontFamily": "Inter, ui-sans-serif, system-ui, sans-serif",
          "fontWeight": "400",
          "fontSize": "16px",
          "lineHeight": "1.75"
        },
        "type": "typography"
      },
      "label": {
        "value": {
          "fontFamily": "Inter, ui-sans-serif, system-ui, sans-serif",
          "fontWeight": "700",
          "fontSize": "12px",
          "lineHeight": "1.4",
          "letterSpacing": "0.3em"
        },
        "type": "typography"
      }
    },
    "shadow": {
      "glowSm": { "value": "0 0 24px rgba(60,235,255,0.22)", "type": "boxShadow" },
      "glowMd": { "value": "0 0 42px rgba(60,235,255,0.35)", "type": "boxShadow" },
      "glowLg": { "value": "0 0 64px rgba(60,235,255,0.62)", "type": "boxShadow" },
      "violetGlow": { "value": "0 0 54px rgba(102,86,255,0.28)", "type": "boxShadow" },
      "innerGlow": { "value": "inset 0 0 22px rgba(60,235,255,0.22)", "type": "boxShadow" }
    },
    "motion": {
      "duration": {
        "fast": { "value": "150ms", "type": "duration" },
        "base": { "value": "300ms", "type": "duration" },
        "slow": { "value": "700ms", "type": "duration" }
      },
      "easing": {
        "fluid": { "value": "cubic-bezier(.16,1,.3,1)", "type": "cubicBezier" }
      }
    }
  }
}
```

---

# 3. React Component Library

建議資料夾：`components/paosynergy/`

## 3.1 `components/paosynergy/theme.ts`

```ts
export const paoTheme = {
  interaction: {
    base: "transition-all duration-300 ease-out will-change-transform",
    lift: "hover:-translate-y-1 hover:scale-[1.025] active:translate-y-0 active:scale-[0.99]",
    focus:
      "focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-cyan-200/80 focus-visible:ring-offset-2 focus-visible:ring-offset-[#021B3D]",
    disabled: "disabled:pointer-events-none disabled:opacity-40 disabled:shadow-none",
  },
  text: {
    heading: "text-cyan-50 drop-shadow-[0_0_12px_rgba(115,245,255,0.28)]",
    body: "text-cyan-50/70",
    label: "text-cyan-200/70 uppercase tracking-[0.3em]",
  },
  surface: {
    glass:
      "border border-white/10 bg-white/[0.06] backdrop-blur-xl shadow-[inset_0_1px_0_rgba(255,255,255,.12)]",
    glassHover:
      "hover:border-cyan-200/35 hover:shadow-[0_0_42px_rgba(60,235,255,.18)]",
  },
};

export function cn(...classes: Array<string | false | null | undefined>) {
  return classes.filter(Boolean).join(" ");
}
```

---

## 3.2 `components/paosynergy/PaoButton.tsx`

```tsx
import * as React from "react";
import { paoTheme, cn } from "./theme";

type PaoButtonVariant = "primary" | "secondary" | "ghost";

type PaoButtonProps = React.ButtonHTMLAttributes<HTMLButtonElement> & {
  variant?: PaoButtonVariant;
};

const variants: Record<PaoButtonVariant, string> = {
  primary:
    "relative overflow-hidden rounded-full bg-gradient-to-r from-cyan-200 via-cyan-300 to-cyan-500 px-7 py-3 font-bold text-[#021B3D] shadow-[0_0_36px_rgba(60,235,255,.35)] before:absolute before:inset-0 before:-translate-x-full before:bg-[linear-gradient(110deg,transparent,rgba(255,255,255,.55),transparent)] before:transition-transform before:duration-700 hover:from-cyan-300 hover:via-cyan-200 hover:to-violet-400 hover:shadow-[0_0_64px_rgba(60,235,255,.62)] hover:before:translate-x-full",
  secondary:
    "relative overflow-hidden rounded-full border border-cyan-100/25 bg-white/5 px-7 py-3 text-cyan-50 shadow-[inset_0_1px_0_rgba(255,255,255,.12)] backdrop-blur-xl hover:border-cyan-200/60 hover:bg-cyan-300/12 hover:text-cyan-100 hover:shadow-[0_0_34px_rgba(60,235,255,.28),inset_0_1px_0_rgba(255,255,255,.2)]",
  ghost:
    "rounded-full border border-white/10 bg-white/[0.04] px-5 py-3 text-cyan-50/80 hover:border-cyan-200/40 hover:bg-cyan-200/10 hover:text-cyan-50",
};

export function PaoButton({ variant = "primary", className, children, ...props }: PaoButtonProps) {
  return (
    <button
      className={cn(
        variants[variant],
        paoTheme.interaction.base,
        paoTheme.interaction.lift,
        paoTheme.interaction.focus,
        paoTheme.interaction.disabled,
        className
      )}
      {...props}
    >
      {children}
    </button>
  );
}
```

---

## 3.3 `components/paosynergy/PaoCard.tsx`

```tsx
import * as React from "react";
import { paoTheme, cn } from "./theme";

type PaoCardProps = React.HTMLAttributes<HTMLDivElement> & {
  interactive?: boolean;
  tone?: "cyan" | "violet" | "neutral";
};

const tones = {
  cyan: "hover:border-cyan-200/35 hover:shadow-[0_0_42px_rgba(60,235,255,.18)]",
  violet: "bg-gradient-to-br from-violet-500/20 to-cyan-400/10 hover:border-violet-200/45 hover:shadow-[0_0_54px_rgba(102,86,255,.28)]",
  neutral: "hover:border-white/20",
};

export function PaoCard({ interactive = false, tone = "cyan", className, children, ...props }: PaoCardProps) {
  return (
    <div
      tabIndex={interactive ? 0 : undefined}
      className={cn(
        "rounded-[2rem] p-6",
        paoTheme.surface.glass,
        tones[tone],
        interactive && paoTheme.interaction.base,
        interactive && paoTheme.interaction.lift,
        interactive && paoTheme.interaction.focus,
        className
      )}
      {...props}
    >
      {children}
    </div>
  );
}
```

---

## 3.4 `components/paosynergy/PaoSectionTitle.tsx`

```tsx
import * as React from "react";
import { paoTheme, cn } from "./theme";

type PaoSectionTitleProps = {
  eyebrow: string;
  title: string;
  description?: string;
  align?: "left" | "center";
};

export function PaoSectionTitle({ eyebrow, title, description, align = "center" }: PaoSectionTitleProps) {
  return (
    <div className={cn("mb-10 max-w-3xl", align === "center" && "mx-auto text-center")}>
      <p className={cn("mb-3 text-sm font-semibold", paoTheme.text.label)}>{eyebrow}</p>
      <h2 className={cn("text-3xl font-bold tracking-tight md:text-5xl", paoTheme.text.heading)}>{title}</h2>
      {description && <p className={cn("mt-4 text-base leading-7", paoTheme.text.body)}>{description}</p>}
    </div>
  );
}
```

---

## 3.5 `components/paosynergy/PaoHero.tsx`

```tsx
import * as React from "react";
import { PaoButton } from "./PaoButton";
import { cn } from "./theme";

type PaoHeroProps = {
  title: string;
  highlight?: string;
  description: string;
  primaryLabel?: string;
  secondaryLabel?: string;
};

export function PaoHero({
  title,
  highlight,
  description,
  primaryLabel = "Start Building",
  secondaryLabel = "View Tokens",
}: PaoHeroProps) {
  return (
    <section className="relative isolate overflow-hidden bg-[#021B3D] px-6 py-28 text-white md:px-12">
      <div className="absolute inset-0 -z-10 bg-[radial-gradient(circle_at_50%_48%,rgba(63,239,255,.55),transparent_0_16%,rgba(3,38,72,.78)_38%,#021B3D_76%)]" />
      <div className="absolute inset-x-0 top-0 -z-10 h-52 bg-[linear-gradient(to_bottom,rgba(115,245,255,.55),rgba(2,27,61,.05))] opacity-80" />

      <div className="mx-auto flex max-w-5xl flex-col items-center text-center">
        <p className="mb-5 rounded-full border border-cyan-100/20 bg-cyan-100/10 px-5 py-2 text-sm text-cyan-50/80 backdrop-blur-lg">
          Oceanic Glass Design System
        </p>
        <h1 className="text-6xl font-black tracking-tight md:text-8xl">
          {title}
          {highlight && (
            <span className="bg-gradient-to-r from-cyan-100 via-cyan-300 to-violet-400 bg-clip-text text-transparent">
              {highlight}
            </span>
          )}
        </h1>
        <p className="mt-7 max-w-2xl text-lg leading-8 text-cyan-50/75">{description}</p>
        <div className="mt-10 flex flex-wrap justify-center gap-4">
          <PaoButton>{primaryLabel}</PaoButton>
          <PaoButton variant="secondary">{secondaryLabel}</PaoButton>
        </div>
      </div>
    </section>
  );
}
```

---

## 3.6 `components/paosynergy/index.ts`

```ts
export * from "./theme";
export * from "./PaoButton";
export * from "./PaoCard";
export * from "./PaoSectionTitle";
export * from "./PaoHero";
```

---

# Example Usage

```tsx
import { PaoHero, PaoCard, PaoButton, PaoSectionTitle } from "@/components/paosynergy";

export default function Page() {
  return (
    <main className="min-h-screen bg-ocean-abyss text-aqua-foam">
      <PaoHero
        title="Pao"
        highlight="Synergy"
        description="以深海光線、透明泡泡、藍紫折射為核心的產品級 Design System。"
      />

      <section className="px-6 py-24 md:px-12">
        <PaoSectionTitle
          eyebrow="Components"
          title="Ocean Glass UI"
          description="可重複使用的卡片、按鈕與互動狀態。"
        />

        <div className="mx-auto grid max-w-7xl gap-6 md:grid-cols-3">
          <PaoCard interactive>
            <h3 className="text-2xl font-bold text-cyan-50">Glass Card</h3>
            <p className="mt-3 text-cyan-50/70">透明玻璃層與柔和光暈。</p>
          </PaoCard>

          <PaoCard interactive tone="violet">
            <h3 className="text-2xl font-bold text-cyan-50">Violet Accent</h3>
            <p className="mt-3 text-cyan-50/70">紫藍折射層次。</p>
          </PaoCard>

          <PaoCard>
            <h3 className="text-2xl font-bold text-cyan-50">Actions</h3>
            <div className="mt-5 flex gap-3">
              <PaoButton>Primary</PaoButton>
              <PaoButton variant="secondary">Secondary</PaoButton>
            </div>
          </PaoCard>
        </div>
      </section>
    </main>
  );
}
```

---

# Recommended Repo Structure

```txt
src/
  components/
    paosynergy/
      index.ts
      theme.ts
      PaoButton.tsx
      PaoCard.tsx
      PaoHero.tsx
      PaoSectionTitle.tsx
  tokens/
    paosynergy.tokens.json
  app/
    page.tsx
tailwind.config.ts
DESIGN.md
```

