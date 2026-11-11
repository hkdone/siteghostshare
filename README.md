<!doctype html>
<html lang="fr" data-theme="light">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="color-scheme" content="light dark" />
  <title>PhantomLink — Préparez, verrouillez et partagez vos fichiers sans cloud</title>
  <meta name="description" content="PhantomLink (Android) : nettoyez vos photos et PDF (GPS, EXIF), masquez et filigranez vos pièces sensibles, stockez-les dans un coffre hors-ligne et transférez-les en direct sans compte ni cloud. Réception sur tout navigateur." />
  <style>
    @layer reset, base, components, utilities;

    @layer reset {
      html {
        line-height: 1.55;
        -webkit-text-size-adjust: 100%;
        scroll-behavior: smooth;
      }

      @media (prefers-reduced-motion: reduce) {
        html {
          scroll-behavior: auto;
        }
      }

      body, h1, h2, h3, h4, p, ul, ol, dl, dd, figure, blockquote, pre, table {
        margin: 0;
      }

      html, body, header, nav, main, section, article, aside, footer,
      div, span, button, a, table, thead, tbody, tr, th, td, details, summary {
        box-sizing: border-box;
      }

      button {
        font: inherit;
        color: inherit;
      }

      img, svg {
        display: block;
        max-inline-size: 100%;
      }
    }

    @layer base {
      :root {
        color-scheme: light dark;

        /* Tokens de marque PhantomLink */
        --brand: #0F766E;
        --brand-bright: #0D9488;
        --brand-accent: #14B8A6;

        /* Valeurs par défaut (Thème Clair) */
        --canvas: #F4F6F8;
        --surface: #FFFFFF;
        --surface-alt: #F8FAFC;
        --surface-soft: #ECFDF5;
        --brand-soft: #CCFBF1;
        --brand-tint: rgba(15, 118, 110, 0.08);
        --ink: #0F172A;
        --ink-muted: #334155;
        --ink-subtle: #475569;
        --line: #E2E8F0;
        --line-strong: #CBD5E1;

        --success-bg: #DCFCE7;
        --success-ink: #166534;
        --success-border: #86EFAC;

        --warn-bg: #FFFBEB;
        --warn-ink: #92400E;
        --warn-border: #FCD34D;

        --danger-bg: #FEE2E2;
        --danger-ink: #991B1B;
        --danger-border: #FCA5A5;

        --vault-bg: #0F172A;
        --vault-surface: #1E293B;
        --vault-ink: #F8FAFC;
        --vault-muted: #CBD5E1;

        --header-bg: rgba(244, 246, 248, 0.88);
        --shadow-sm: 0 1px 3px rgba(15, 23, 42, 0.06);
        --shadow-md: 0 10px 30px -10px rgba(15, 23, 42, 0.10);
        --shadow-lg: 0 22px 45px -15px rgba(15, 23, 42, 0.14);
        --focus-ring: #0D9488;

        --r-sm: 8px;
        --r-md: 12px;
        --r-lg: 16px;
        --r-xl: 24px;
      }

      /* Thème Sombre automatique via prefers-color-scheme */
      @media (prefers-color-scheme: dark) {
        :root:not([data-theme="light"]) {
          --brand: #2DD4BF;
          --brand-bright: #14B8A6;
          --brand-accent: #5EEAD4;
          --canvas: #0B1120;
          --surface: #111827;
          --surface-alt: #1E293B;
          --surface-soft: rgba(20, 184, 166, 0.12);
          --brand-soft: rgba(45, 212, 191, 0.16);
          --brand-tint: rgba(45, 212, 191, 0.12);
          --ink: #F8FAFC;
          --ink-muted: #CBD5E1;
          --ink-subtle: #94A3B8;
          --line: #1F2937;
          --line-strong: #334155;

          --success-bg: rgba(22, 101, 52, 0.28);
          --success-ink: #86EFAC;
          --success-border: rgba(134, 239, 172, 0.35);

          --warn-bg: rgba(146, 64, 14, 0.28);
          --warn-ink: #FDE68A;
          --warn-border: rgba(252, 211, 77, 0.35);

          --danger-bg: rgba(153, 27, 27, 0.28);
          --danger-ink: #FCA5A5;
          --danger-border: rgba(252, 165, 165, 0.35);

          --header-bg: rgba(11, 17, 32, 0.88);
          --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.35);
          --shadow-md: 0 12px 32px -12px rgba(0, 0, 0, 0.5);
          --shadow-lg: 0 24px 50px -15px rgba(0, 0, 0, 0.65);
          --focus-ring: #5EEAD4;
        }
      }

      /* Support progressif light-dark() + forçage manuel via data-theme */
      :root[data-theme="dark"] {
        color-scheme: dark;
        --brand: #2DD4BF;
        --brand-bright: #14B8A6;
        --brand-accent: #5EEAD4;
        --canvas: #0B1120;
        --surface: #111827;
        --surface-alt: #1E293B;
        --surface-soft: rgba(20, 184, 166, 0.12);
        --brand-soft: rgba(45, 212, 191, 0.16);
        --brand-tint: rgba(45, 212, 191, 0.12);
        --ink: #F8FAFC;
        --ink-muted: #CBD5E1;
        --ink-subtle: #94A3B8;
        --line: #1F2937;
        --line-strong: #334155;
        --success-bg: rgba(22, 101, 52, 0.28);
        --success-ink: #86EFAC;
        --success-border: rgba(134, 239, 172, 0.35);
        --warn-bg: rgba(146, 64, 14, 0.28);
        --warn-ink: #FDE68A;
        --warn-border: rgba(252, 211, 77, 0.35);
        --danger-bg: rgba(153, 27, 27, 0.28);
        --danger-ink: #FCA5A5;
        --danger-border: rgba(252, 165, 165, 0.35);
        --header-bg: rgba(11, 17, 32, 0.88);
        --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.35);
        --shadow-md: 0 12px 32px -12px rgba(0, 0, 0, 0.5);
        --shadow-lg: 0 24px 50px -15px rgba(0, 0, 0, 0.65);
        --focus-ring: #5EEAD4;
      }

      :root[data-theme="light"] {
        color-scheme: light;
      }

      @supports (color: light-dark(white, black)) {
        :root:not([data-theme]) {
          --canvas: light-dark(#F4F6F8, #0B1120);
          --surface: light-dark(#FFFFFF, #111827);
          --surface-alt: light-dark(#F8FAFC, #1E293B);
          --ink: light-dark(#0F172A, #F8FAFC);
          --ink-muted: light-dark(#334155, #CBD5E1);
          --ink-subtle: light-dark(#475569, #94A3B8);
          --line: light-dark(#E2E8F0, #1F2937);
          --line-strong: light-dark(#CBD5E1, #334155);
        }
      }

      body {
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Inter, "Helvetica Neue", Arial, sans-serif;
        background: var(--canvas);
        color: var(--ink);
        line-height: 1.65;
        font-size: 1rem;
        overflow-x: clip;
      }

      a {
        color: var(--brand);
        text-underline-offset: 3px;
      }

      a:hover {
        color: var(--brand-bright);
      }

      :focus-visible {
        outline: 3px solid var(--focus-ring);
        outline-offset: 2px;
        border-radius: 4px;
      }

      code {
        font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
        font-size: 0.9em;
        background: var(--surface-alt);
        border: 1px solid var(--line);
        padding: 0.1em 0.35em;
        border-radius: 5px;
      }

      h1, h2, h3, h4 {
        color: var(--ink);
        letter-spacing: -0.02em;
        line-height: 1.2;
      }
    }

    @layer components {
      /* Lien d'évitement accessibilité */
      .skip-link {
        position: absolute;
        inset-inline-start: 16px;
        inset-block-start: -120px;
        z-index: 1000;
        background: var(--brand);
        color: #FFFFFF;
        padding: 10px 18px;
        border-radius: var(--r-sm);
        font-weight: 700;
        text-decoration: none;
        box-shadow: var(--shadow-md);
      }

      .skip-link:focus-visible {
        inset-block-start: 16px;
        color: #FFFFFF;
      }

      .container {
        max-inline-size: 1120px;
        margin-inline: auto;
        padding-inline: 20px;
      }

      /* Barre de navigation sticky + onglets principaux */
      .site-header {
        position: sticky;
        inset-block-start: 0;
        z-index: 100;
        background: var(--header-bg);
        backdrop-filter: blur(12px);
        -webkit-backdrop-filter: blur(12px);
        border-block-end: 1px solid var(--line);
      }

      .header-inner {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-between;
        gap: 12px 20px;
        padding-block: 10px;
      }

      .brand-lockup {
        display: inline-flex;
        align-items: center;
        gap: 10px;
        text-decoration: none;
        color: var(--ink);
        font-weight: 800;
        font-size: 1.125rem;
        letter-spacing: -0.02em;
        min-block-size: 44px;
      }

      .brand-mark {
        inline-size: 36px;
        block-size: 36px;
        border-radius: 10px;
        background: linear-gradient(135deg, #0F766E 0%, #14B8A6 100%);
        display: grid;
        place-items: center;
        color: #FFFFFF;
        flex-shrink: 0;
        box-shadow: 0 4px 12px rgba(15, 118, 110, 0.28);
      }

      .brand-sub {
        font-size: 0.72rem;
        font-weight: 700;
        text-transform: uppercase;
        letter-spacing: 0.06em;
        padding: 3px 8px;
        border-radius: 999px;
        background: var(--brand-soft);
        color: var(--brand);
        border: 1px solid var(--brand-tint);
      }

      .header-actions {
        display: flex;
        align-items: center;
        flex-wrap: wrap;
        gap: 10px;
      }

      /* Onglets principaux (WCAG 1.4.1 : bordure ::after en plus de la couleur) */
      .primary-tabs {
        display: inline-flex;
        align-items: stretch;
        gap: 4px;
        background: var(--surface);
        padding: 4px;
        border-radius: var(--r-md);
        border: 1px solid var(--line);
        box-shadow: var(--shadow-sm);
      }

      .tab-btn {
        position: relative;
        appearance: none;
        border: none;
        background: transparent;
        color: var(--ink-muted);
        font-weight: 600;
        font-size: 0.92rem;
        padding: 8px 14px;
        min-block-size: 40px;
        border-radius: var(--r-sm);
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        gap: 7px;
        transition: color 0.15s ease, background-color 0.15s ease;
      }

      @media (pointer: coarse) {
        .tab-btn,
        .btn,
        .theme-btn,
        .scenario-tab,
        .proof-toggle-btn {
          min-block-size: 44px;
        }
      }

      .tab-btn:hover:not(:disabled) {
        color: var(--ink);
        background: var(--surface-alt);
      }

      .tab-btn[aria-selected="true"] {
        color: var(--brand);
        background: var(--brand-tint);
        font-weight: 700;
      }

      /* Indicateur non uniquement chromatique (bordure CSS conservée en forced-colors) */
      .tab-btn[aria-selected="true"]::after {
        content: "";
        position: absolute;
        inset-inline: 10px;
        inset-block-end: 2px;
        border-block-end: 2.5px solid currentColor;
      }

      .theme-btn {
        appearance: none;
        background: var(--surface);
        border: 1px solid var(--line);
        color: var(--ink-muted);
        border-radius: var(--r-md);
        padding: 8px 12px;
        min-block-size: 40px;
        font-size: 0.85rem;
        font-weight: 600;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        gap: 6px;
        box-shadow: var(--shadow-sm);
      }

      .theme-btn:hover:not(:disabled) {
        border-color: var(--line-strong);
        color: var(--ink);
      }

      /* IMPORTANT (règle guide tabs) : aucun padding/margin/bg sur role="tabpanel" */
      [role="tabpanel"] {
        display: block;
      }

      [role="tabpanel"][hidden] {
        display: none;
      }

      [role="tabpanel"][hidden="until-found"] {
        content-visibility: hidden;
      }

      .panel-inner {
        padding-block-end: 56px;
      }

      /* Section Hero */
      .hero {
        padding-block: 44px 36px;
      }

      .hero-grid {
        display: grid;
        grid-template-columns: 1.15fr 0.85fr;
        gap: 32px;
        align-items: center;
      }

      @media (max-width: 900px) {
        .hero-grid {
          grid-template-columns: 1fr;
        }
      }

      .availability-banner {
        display: inline-flex;
        flex-wrap: wrap;
        align-items: center;
        gap: 8px;
        padding: 7px 14px;
        border-radius: 999px;
        background: var(--surface);
        border: 1px solid var(--line-strong);
        box-shadow: var(--shadow-sm);
        font-size: 0.86rem;
        font-weight: 600;
        color: var(--ink);
        margin-block-end: 18px;
      }

      .android-dot {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        color: var(--success-ink);
        background: var(--success-bg);
        border: 1px solid var(--success-border);
        padding: 2px 9px;
        border-radius: 999px;
        font-weight: 700;
        font-size: 0.78rem;
      }

      .hero h1 {
        font-size: clamp(1.9rem, 3.6vw, 2.85rem);
        font-weight: 850;
        line-height: 1.14;
        margin-block-end: 18px;
      }

      .hero h1 .highlight {
        color: var(--brand);
      }

      .hero-lead {
        font-size: 1.1rem;
        color: var(--ink-muted);
        margin-block-end: 24px;
        max-inline-size: 62ch;
      }

      .hero-ctas {
        display: flex;
        flex-wrap: wrap;
        gap: 12px;
        margin-block-end: 22px;
      }

      .btn {
        display: inline-flex;
        align-items: center;
        justify-content: center;
        gap: 8px;
        min-block-size: 44px;
        padding: 10px 20px;
        border-radius: var(--r-md);
        font-weight: 700;
        font-size: 0.95rem;
        text-decoration: none;
        cursor: pointer;
        border: 1px solid transparent;
        transition: transform 0.14s ease, box-shadow 0.14s ease, background-color 0.14s ease;
      }

      .btn-primary {
        background: #0F766E;
        color: #FFFFFF;
        box-shadow: 0 6px 18px rgba(15, 118, 110, 0.28);
      }

      .btn-primary:hover:not(:disabled) {
        background: #0D9488;
        color: #FFFFFF;
        transform: translateY(-1px);
      }

      .btn-secondary {
        background: var(--surface);
        color: var(--ink);
        border-color: var(--line-strong);
        box-shadow: var(--shadow-sm);
      }

      .btn-secondary:hover:not(:disabled) {
        border-color: var(--brand);
        color: var(--brand);
      }

      .hero-trust-strip {
        display: flex;
        flex-wrap: wrap;
        gap: 10px 18px;
        font-size: 0.88rem;
        color: var(--ink-muted);
        list-style: none;
        padding: 0;
      }

      .hero-trust-strip li {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        font-weight: 600;
      }

      /* Widget interactif Avant / Après du Hero */
      .demo-card {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-xl);
        padding: 20px;
        box-shadow: var(--shadow-lg);
      }

      .demo-header {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
        margin-block-end: 16px;
        padding-block-end: 12px;
        border-block-end: 1px solid var(--line);
      }

      .demo-title {
        font-size: 0.92rem;
        font-weight: 800;
        color: var(--ink);
      }

      .proof-toggle {
        display: inline-flex;
        background: var(--surface-alt);
        border: 1px solid var(--line);
        border-radius: 999px;
        padding: 3px;
        gap: 2px;
      }

      .proof-toggle-btn {
        position: relative;
        appearance: none;
        border: none;
        background: transparent;
        color: var(--ink-muted);
        font-size: 0.8rem;
        font-weight: 700;
        padding: 6px 12px;
        border-radius: 999px;
        cursor: pointer;
      }

      .proof-toggle-btn[aria-pressed="true"] {
        background: #0F766E;
        color: #FFFFFF;
      }

      .demo-preview {
        background: var(--surface-alt);
        border: 1px dashed var(--line-strong);
        border-radius: var(--r-lg);
        padding: 16px;
        margin-block-end: 14px;
      }

      .demo-doc {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-md);
        padding: 14px;
        position: relative;
        overflow: hidden;
      }

      .demo-doc-top {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 8px;
        margin-block-end: 10px;
      }

      .demo-filename {
        font-family: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;
        font-size: 0.78rem;
        font-weight: 700;
        color: var(--ink);
        word-break: break-all;
      }

      .demo-badge {
        font-size: 0.72rem;
        font-weight: 800;
        padding: 2px 8px;
        border-radius: 999px;
        white-space: nowrap;
      }

      .demo-badge-risk {
        background: var(--danger-bg);
        color: var(--danger-ink);
        border: 1px solid var(--danger-border);
      }

      .demo-badge-safe {
        background: var(--success-bg);
        color: var(--success-ink);
        border: 1px solid var(--success-border);
      }

      .demo-lines {
        display: grid;
        gap: 8px;
        font-size: 0.84rem;
      }

      .demo-row {
        display: flex;
        justify-content: space-between;
        gap: 10px;
        padding: 6px 9px;
        border-radius: var(--r-sm);
        background: var(--surface-alt);
      }

      .demo-row-label {
        color: var(--ink-subtle);
        font-weight: 600;
      }

      .demo-row-val {
        font-weight: 700;
        text-align: end;
      }

      .demo-val-exposed {
        color: var(--danger-ink);
      }

      .demo-val-clean {
        color: var(--success-ink);
      }

      .demo-watermark {
        margin-block-start: 10px;
        padding: 7px 10px;
        border-radius: var(--r-sm);
        border: 1px solid var(--brand-tint);
        background: var(--brand-soft);
        color: var(--brand);
        font-size: 0.78rem;
        font-weight: 800;
        text-align: center;
        letter-spacing: 0.04em;
      }

      .demo-caption {
        font-size: 0.84rem;
        color: var(--ink-muted);
      }

      /* Bandeau Disponibilité Android vs Réception Universelle */
      .platform-strip {
        margin-block: 10px 44px;
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-lg);
        padding: 18px 22px;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 18px;
        box-shadow: var(--shadow-sm);
      }

      .platform-item {
        display: flex;
        align-items: flex-start;
        gap: 12px;
      }

      .platform-icon {
        inline-size: 40px;
        block-size: 40px;
        border-radius: var(--r-md);
        display: grid;
        place-items: center;
        flex-shrink: 0;
        background: var(--brand-soft);
        color: var(--brand);
      }

      .platform-item h2 {
        font-size: 0.96rem;
        font-weight: 800;
        margin-block-end: 3px;
      }

      .platform-item p {
        font-size: 0.88rem;
        color: var(--ink-muted);
      }

      /* Sections génériques */
      .section {
        padding-block: 30px;
      }

      .section-head {
        margin-block-end: 20px;
        max-inline-size: 64ch;
      }

      .section-eyebrow {
        display: inline-block;
        font-size: 0.75rem;
        font-weight: 800;
        text-transform: uppercase;
        letter-spacing: 0.07em;
        color: var(--brand);
        margin-block-end: 6px;
      }

      .section-head h2 {
        font-size: clamp(1.4rem, 2.5vw, 1.85rem);
        font-weight: 850;
        margin-block-end: 6px;
      }

      .section-head p {
        color: var(--ink-muted);
        font-size: 0.96rem;
      }

      /* Grille des 4 Pouvoirs */
      .pillars-grid {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
        gap: 16px;
        align-items: start;
      }

      @media (max-width: 780px) {
        .pillars-grid {
          grid-template-columns: 1fr;
        }
      }

      .pillar-card {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-xl);
        padding: 22px;
        box-shadow: var(--shadow-sm);
        display: flex;
        flex-direction: column;
        gap: 12px;
        transition: border-color 0.16s ease, box-shadow 0.16s ease;
      }

      .pillar-card:hover {
        border-color: var(--line-strong);
        box-shadow: var(--shadow-md);
      }

      .pillar-card-vault {
        border-color: rgba(15, 118, 110, 0.35);
      }

      .pillar-top {
        display: flex;
        align-items: center;
        gap: 14px;
      }

      .pillar-icon {
        inline-size: 46px;
        block-size: 46px;
        border-radius: 13px;
        display: grid;
        place-items: center;
        flex-shrink: 0;
        background: var(--brand-soft);
        color: var(--brand);
      }

      .pillar-num {
        font-size: 0.72rem;
        font-weight: 800;
        text-transform: uppercase;
        letter-spacing: 0.06em;
        color: var(--brand);
      }

      .pillar-card h3 {
        font-size: 1.15rem;
        font-weight: 800;
      }

      .pillar-summary {
        font-size: 0.95rem;
        color: var(--ink-muted);
        line-height: 1.5;
      }

      .pillar-list {
        padding-inline-start: 18px;
        display: grid;
        gap: 8px;
        font-size: 0.91rem;
        color: var(--ink-muted);
      }

      /* Blocs dépliables progressifs ("En savoir plus") */
      .more-box {
        margin-block-start: auto;
      }

      .more-box > summary {
        list-style: none;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        gap: 7px;
        min-block-size: 38px;
        padding: 6px 13px;
        border-radius: 999px;
        background: var(--surface-alt);
        border: 1px solid var(--line);
        color: var(--brand);
        font-size: 0.84rem;
        font-weight: 700;
        transition: background-color 0.14s ease, border-color 0.14s ease;
      }

      .more-box > summary::-webkit-details-marker {
        display: none;
      }

      .more-box > summary:hover {
        border-color: var(--brand);
        background: var(--brand-tint);
      }

      .more-box > summary .chev {
        display: inline-block;
        transition: transform 0.16s ease;
        font-style: normal;
      }

      .more-box[open] > summary .chev {
        transform: rotate(90deg);
      }

      .more-box > summary .label-open {
        display: none;
      }

      .more-box[open] > summary .label-closed {
        display: none;
      }

      .more-box[open] > summary .label-open {
        display: inline;
      }

      .more-box-body {
        margin-block-start: 14px;
        padding-block-start: 14px;
        border-block-start: 1px dashed var(--line-strong);
      }

      .more-box-section {
        margin-block-start: 18px;
      }

      .more-box-section > summary {
        background: var(--surface);
        box-shadow: var(--shadow-sm);
      }

      /* Cartes synthétiques Gratuit vs Pro & Comparatif */
      .plans-summary-grid {
        display: grid;
        grid-template-columns: repeat(2, minmax(0, 1fr));
        gap: 18px;
      }

      @media (max-width: 720px) {
        .plans-summary-grid {
          grid-template-columns: 1fr;
        }
      }

      .plan-card {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-xl);
        padding: 22px;
        box-shadow: var(--shadow-sm);
        display: grid;
        gap: 10px;
      }

      .plan-card-pro {
        border-color: var(--brand);
        background: linear-gradient(180deg, var(--brand-tint) 0%, var(--surface) 45%);
      }

      .plan-card h3 {
        font-size: 1.15rem;
        font-weight: 850;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 10px;
      }

      .plan-card p {
        font-size: 0.94rem;
        color: var(--ink-muted);
      }

      .plan-highlights {
        list-style: none;
        padding: 0;
        display: grid;
        gap: 6px;
        font-size: 0.9rem;
        color: var(--ink);
      }

      .plan-highlights li::before {
        content: "✓ ";
        color: var(--brand);
        font-weight: 800;
      }

      .compare-summary-grid {
        display: grid;
        grid-template-columns: repeat(3, minmax(0, 1fr));
        gap: 14px;
      }

      @media (max-width: 780px) {
        .compare-summary-grid {
          grid-template-columns: 1fr;
        }
      }

      .compare-mini-card {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-lg);
        padding: 16px 18px;
        box-shadow: var(--shadow-sm);
      }

      .compare-mini-card h3 {
        font-size: 0.96rem;
        font-weight: 800;
        color: var(--brand);
        margin-block-end: 6px;
      }

      .compare-mini-card p {
        font-size: 0.9rem;
        color: var(--ink-muted);
      }

      .chip {
        font-size: 0.78rem;
        font-weight: 700;
        padding: 4px 10px;
        border-radius: 999px;
        background: var(--surface-alt);
        border: 1px solid var(--line);
        color: var(--ink-muted);
      }

      /* Scénarios interactifs du quotidien */
      .scenario-shell {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-xl);
        padding: 22px;
        box-shadow: var(--shadow-md);
      }

      .scenario-tablist {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        padding-block-end: 16px;
        border-block-end: 1px solid var(--line);
        margin-block-end: 20px;
      }

      .scenario-tab {
        position: relative;
        appearance: none;
        border: 1px solid var(--line);
        background: var(--surface-alt);
        color: var(--ink-muted);
        border-radius: var(--r-md);
        padding: 10px 14px;
        min-block-size: 42px;
        font-weight: 700;
        font-size: 0.9rem;
        cursor: pointer;
        display: inline-flex;
        align-items: center;
        gap: 8px;
      }

      .scenario-tab:hover:not(:disabled) {
        border-color: var(--brand);
        color: var(--ink);
      }

      .scenario-tab[aria-selected="true"] {
        background: var(--brand-tint);
        border-color: var(--brand);
        color: var(--brand);
      }

      .scenario-tab[aria-selected="true"]::after {
        content: "";
        position: absolute;
        inset-inline: 10px;
        inset-block-end: 3px;
        border-block-end: 2.5px solid currentColor;
      }

      .scenario-panel-body {
        display: grid;
        grid-template-columns: 1.15fr 0.85fr;
        gap: 24px;
        align-items: center;
      }

      @media (max-width: 780px) {
        .scenario-panel-body {
          grid-template-columns: 1fr;
        }
      }

      .scenario-steps {
        list-style: none;
        padding: 0;
        display: grid;
        gap: 12px;
        margin-block-start: 14px;
      }

      .scenario-steps li {
        display: flex;
        gap: 12px;
        align-items: flex-start;
        background: var(--surface-alt);
        border: 1px solid var(--line);
        border-radius: var(--r-md);
        padding: 12px 14px;
        font-size: 0.94rem;
      }

      .step-num {
        inline-size: 26px;
        block-size: 26px;
        border-radius: 999px;
        background: #0F766E;
        color: #FFFFFF;
        font-size: 0.8rem;
        font-weight: 800;
        display: grid;
        place-items: center;
        flex-shrink: 0;
        margin-block-start: 2px;
      }

      .scenario-benefit-box {
        background: var(--surface-soft);
        border: 1px solid var(--brand-tint);
        border-radius: var(--r-lg);
        padding: 20px;
      }

      .scenario-benefit-box h4 {
        font-size: 1rem;
        font-weight: 800;
        color: var(--brand);
        margin-block-end: 10px;
      }

      .scenario-benefit-box p {
        font-size: 0.94rem;
        color: var(--ink-muted);
        margin-block-end: 10px;
      }

      /* Tableaux responsives avec container queries (guide responsive-table) */
      .table-wrap {
        container-type: inline-size;
        overflow: auto;
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-lg);
        box-shadow: var(--shadow-sm);
      }

      table.data-table {
        width: 100%;
        border-collapse: collapse;
        font-size: 0.92rem;
        text-align: start;
      }

      table.data-table caption {
        padding: 14px 16px;
        font-weight: 800;
        font-size: 0.98rem;
        color: var(--ink);
        text-align: start;
        background: var(--surface-alt);
        border-block-end: 1px solid var(--line);
      }

      table.data-table thead {
        position: sticky;
        inset-block-start: 0;
        z-index: 2;
      }

      table.data-table th,
      table.data-table td {
        padding: 12px 14px;
        border-block-end: 1px solid var(--line);
        vertical-align: top;
      }

      table.data-table thead th {
        background: var(--surface-alt);
        color: var(--ink);
        font-weight: 800;
        font-size: 0.84rem;
        text-transform: uppercase;
        letter-spacing: 0.04em;
        white-space: nowrap;
      }

      table.data-table tbody th[scope="row"] {
        background: var(--surface);
        color: var(--ink);
        font-weight: 700;
        text-align: start;
      }

      @container (width >= 640px) {
        table.data-table tbody th[scope="row"] {
          position: sticky;
          inset-inline-start: 0;
          z-index: 1;
        }
      }

      /* Mode empilé lisible sous 640px via container query */
      @container (width < 640px) {
        table.data-table thead {
          display: none;
        }

        table.data-table tbody {
          display: grid;
          gap: 12px;
          padding: 12px;
          background: var(--surface-alt);
        }

        table.data-table tr {
          display: grid;
          background: var(--surface);
          border: 1px solid var(--line);
          border-radius: var(--r-md);
          overflow: hidden;
        }

        table.data-table tbody th[scope="row"] {
          background: var(--brand-tint);
          color: var(--brand);
          border-block-end: 1px solid var(--line);
          padding: 10px 14px;
          font-size: 0.95rem;
        }

        table.data-table td {
          display: grid;
          grid-template-columns: 1fr;
          gap: 3px;
          padding: 10px 14px;
        }

        table.data-table td:last-child {
          border-block-end: none;
        }

        table.data-table td::before {
          font-size: 0.76rem;
          font-weight: 800;
          text-transform: uppercase;
          letter-spacing: 0.04em;
          color: var(--ink-subtle);
        }

        .table-plans td:nth-child(2)::before { content: var(--p-col2) " :"; }
        .table-plans td:nth-child(3)::before { content: var(--p-col3) " :"; }

        .table-compare td:nth-child(2)::before { content: var(--c-col2) " :"; }
        .table-compare td:nth-child(3)::before { content: var(--c-col3) " :"; }
        .table-compare td:nth-child(4)::before { content: var(--c-col4) " :"; }
        .table-compare td:nth-child(5)::before { content: var(--c-col5) " :"; }
        .table-compare td:nth-child(6)::before { content: var(--c-col6) " :"; }

        .table-thirdparty td:nth-child(2)::before { content: var(--t-col2) " :"; }
        .table-thirdparty td:nth-child(3)::before { content: var(--t-col3) " :"; }
        .table-thirdparty td:nth-child(4)::before { content: var(--t-col4) " :"; }
      }

      .table-plans {
        --p-col2: "Gratuit (0 €)";
        --p-col3: "PhantomLink Pro";
      }

      .table-compare {
        --c-col2: "PhantomLink";
        --c-col3: "Signal";
        --c-col4: "WhatsApp";
        --c-col5: "WeTransfer / SwissTransfer";
        --c-col6: "LocalSend";
      }

      .table-thirdparty {
        --t-col2: "Rôle Technique";
        --t-col3: "Nature des Données";
        --t-col4: "Confidentialité & Conservation";
      }

      .tag-yes {
        display: inline-block;
        padding: 2px 8px;
        border-radius: 6px;
        font-weight: 700;
        font-size: 0.82rem;
        background: var(--success-bg);
        color: var(--success-ink);
      }

      .tag-no {
        display: inline-block;
        padding: 2px 8px;
        border-radius: 6px;
        font-weight: 700;
        font-size: 0.82rem;
        background: var(--surface-alt);
        color: var(--ink-subtle);
      }

      .tag-warn {
        display: inline-block;
        padding: 2px 8px;
        border-radius: 6px;
        font-weight: 700;
        font-size: 0.82rem;
        background: var(--warn-bg);
        color: var(--warn-ink);
      }

      .table-note {
        margin-block-start: 12px;
        font-size: 0.88rem;
        color: var(--ink-subtle);
      }

      /* Badges de vérifications publiques */
      .audit-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 14px;
        margin-block-end: 20px;
      }

      .audit-card {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-lg);
        padding: 18px;
        text-decoration: none;
        color: inherit;
        box-shadow: var(--shadow-sm);
        display: flex;
        flex-direction: column;
        gap: 6px;
        transition: border-color 0.15s ease, transform 0.15s ease;
      }

      .audit-card:hover {
        border-color: var(--brand);
        transform: translateY(-2px);
      }

      .audit-score {
        font-size: 1.55rem;
        font-weight: 900;
        color: var(--brand);
        line-height: 1.1;
      }

      .audit-name {
        font-weight: 800;
        font-size: 0.96rem;
        color: var(--ink);
      }

      .audit-desc {
        font-size: 0.84rem;
        color: var(--ink-muted);
      }

      .audit-link-label {
        margin-block-start: auto;
        padding-block-start: 6px;
        font-size: 0.82rem;
        font-weight: 700;
        color: var(--brand);
      }

      /* Encadrés de transparence et cartes légales */
      .honesty-card {
        background: var(--warn-bg);
        border: 1px solid var(--warn-border);
        border-inline-start: 5px solid #D97706;
        border-radius: var(--r-lg);
        padding: 20px 22px;
        color: var(--ink);
      }

      .honesty-card h3 {
        font-size: 1.08rem;
        font-weight: 800;
        color: var(--warn-ink);
        margin-block-end: 10px;
      }

      .honesty-card ul {
        padding-inline-start: 18px;
        display: grid;
        gap: 8px;
        font-size: 0.94rem;
        color: var(--ink-muted);
      }

      /* Cartes FAQ */
      .faq-list {
        display: grid;
        gap: 10px;
      }

      .faq-item {
        background: var(--surface);
        border: 1px solid var(--line);
        border-radius: var(--r-md);
        padding: 4px 18px;
      }

      .faq-item summary {
        list-style: none;
        cursor: pointer;
        font-weight: 700;
        padding-block: 14px;
        min-block-size: 44px;
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 12px;
      }

      .faq-item summary::-webkit-details-marker {
        display: none;
      }

      .faq-item summary::after {
        content: "+";
        font-size: 1.25rem;
        font-weight: 800;
        color: var(--brand);
        flex-shrink: 0;
      }

      .faq-item[open] summary::after {
        content: "−";
      }

      .faq-item p {
        padding-block-end: 14px;
        color: var(--ink-muted);
        font-size: 0.94rem;
      }

      /* Onglet 2 : Politique de Confidentialité */
      .legal-shell {
        max-inline-size: 860px;
        margin-inline: auto;
        padding-block-start: 34px;
      }

      .legal-header {
        border-block-end: 2px solid var(--brand);
        padding-block-end: 18px;
        margin-block-end: 26px;
      }

      .legal-header h1 {
        font-size: clamp(1.55rem, 2.8vw, 2rem);
        margin-block-end: 8px;
      }

      .legal-meta {
        font-size: 0.92rem;
        color: var(--ink-muted);
      }

      .legal-card {
        background: var(--surface);
        border: 1px solid var(--line);
        border-inline-start: 4px solid var(--brand);
        border-radius: var(--r-md);
        padding: 18px 20px;
        margin-block-end: 22px;
        box-shadow: var(--shadow-sm);
      }

      .legal-warning {
        background: var(--warn-bg);
        border: 1px solid var(--warn-border);
        border-inline-start: 4px solid #D97706;
        border-radius: var(--r-md);
        padding: 16px 20px;
        margin-block: 16px 22px;
      }

      .legal-body h2 {
        font-size: 1.22rem;
        margin-block: 28px 10px;
        padding-block-start: 14px;
        border-block-start: 1px solid var(--line);
      }

      .legal-body p {
        margin-block-end: 12px;
        color: var(--ink-muted);
      }

      .legal-body ul {
        padding-inline-start: 20px;
        margin-block-end: 16px;
        display: grid;
        gap: 8px;
        color: var(--ink-muted);
      }

      .legal-body li strong {
        color: var(--ink);
      }

      /* Pied de page */
      .site-footer {
        border-block-start: 1px solid var(--line);
        background: var(--surface);
        padding-block: 26px;
        font-size: 0.88rem;
        color: var(--ink-subtle);
      }

      .footer-inner {
        display: flex;
        flex-wrap: wrap;
        align-items: center;
        justify-content: space-between;
        gap: 14px 24px;
      }

      .footer-links {
        display: flex;
        flex-wrap: wrap;
        gap: 16px;
        align-items: center;
      }

      .footer-link-btn {
        appearance: none;
        border: none;
        background: transparent;
        padding: 4px 0;
        color: var(--brand);
        font-weight: 700;
        text-decoration: underline;
        cursor: pointer;
        font-size: 0.88rem;
      }

      /* Animation progressive au scroll (guide scroll-entry-exit-effects) */
      @keyframes sectionReveal {
        from {
          opacity: 0.35;
          transform: translateY(18px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      @media (prefers-reduced-motion: no-preference) {
        @supports ((animation-timeline: view()) and (animation-range: entry)) {
          .reveal {
            animation: sectionReveal linear both;
            animation-timeline: view();
            animation-range: entry 0% entry 24%;
          }
        }
      }
    }

    @layer utilities {
      .badge-row-inline {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        align-items: center;
      }

      .mt-16 {
        margin-block-start: 16px;
      }
    }
  </style>
</head>
<body>
  <a class="skip-link" href="#main-content">Aller au contenu principal</a>

  <header class="site-header">
    <div class="container header-inner">
      <a class="brand-lockup" href="#top" id="brand-home">
        <span class="brand-mark" aria-hidden="true">
          <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round">
            <path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/>
            <path d="M9 12l2 2 4-4"/>
          </svg>
        </span>
        <span>PhantomLink</span>
        <span class="brand-sub">Android · Zéro Cloud</span>
      </a>

      <div class="header-actions">
        <div class="primary-tabs" role="tablist" aria-label="Navigation principale" focusgroup="tablist nomemory">
          <button
            type="button"
            role="tab"
            class="tab-btn"
            id="tab-showcase"
            aria-selected="true"
            aria-controls="panel-showcase"
            focusgroupstart
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
              <rect x="3" y="3" width="7" height="7" rx="1.5"/>
              <rect x="14" y="3" width="7" height="7" rx="1.5"/>
              <rect x="3" y="14" width="7" height="7" rx="1.5"/>
              <rect x="14" y="14" width="7" height="7" rx="1.5"/>
            </svg>
            Découvrir l'application
          </button>
          <button
            type="button"
            role="tab"
            class="tab-btn"
            id="tab-privacy"
            aria-selected="false"
            aria-controls="panel-privacy"
          >
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
              <path d="M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z"/>
              <polyline points="14 2 14 8 20 8"/>
              <line x1="16" y1="13" x2="8" y2="13"/>
              <line x1="16" y1="17" x2="8" y2="17"/>
            </svg>
            Confidentialité &amp; Mentions légales
          </button>
        </div>

        <button type="button" class="theme-btn" id="theme-toggle" aria-label="Basculer entre le thème clair et le thème sombre">
          <span aria-hidden="true" id="theme-icon">☀</span>
          <span id="theme-label">Thème : Clair</span>
        </button>
      </div>
    </div>
  </header>

  <main id="main-content">
    <!-- =========================================================
         ONGLET 1 : VITRINE PRODUIT DYNAMIQUE & GRAND PUBLIC
         ========================================================= -->
    <section id="panel-showcase" role="tabpanel" aria-labelledby="tab-showcase">
      <div class="panel-inner">
        <div class="container">
          <!-- HERO -->
          <section class="hero" id="top" aria-labelledby="hero-title">
            <div class="hero-grid">
              <div>
                <div class="availability-banner">
                  <span class="android-dot">
                    <svg width="13" height="13" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
                      <path d="M17.6 9.48l1.84-3.18c.16-.31.04-.69-.26-.85-.29-.15-.65-.06-.83.22l-1.88 3.24a11.46 11.46 0 0 0-8.94 0L5.65 5.67a.61.61 0 0 0-.83-.22c-.3.16-.42.54-.26.85l1.84 3.18C3.58 11.01 1.66 13.84 1.38 17.2h21.24c-.28-3.36-2.2-6.19-5.02-7.72zM8.5 14.5a1 1 0 1 1 0-2 1 1 0 0 1 0 2zm7 0a1 1 0 1 1 0-2 1 1 0 0 1 0 2z"/>
                    </svg>
                    Disponible sur Android
                  </span>
                  <span>Version iOS en préparation · Reçu sur tout navigateur</span>
                </div>

                <h1 id="hero-title">
                  Préparez, verrouillez et partagez vos fichiers
                  <span class="highlight">en direct, sans jamais passer par un cloud.</span>
                </h1>

                <p class="hero-lead">
                  Effacez les traces de vos photos et PDF, mettez vos papiers à l'abri hors-ligne et partagez-les directement d'un appareil à l'autre, sans compte.
                </p>

                <div class="hero-ctas">
                  <a class="btn btn-primary" href="#piliers">Découvrir les 4 pouvoirs</a>
                  <a class="btn btn-secondary" href="#quotas">Voir Gratuit &amp; Pro</a>
                  <button type="button" class="btn btn-secondary" data-open-tab="privacy">Confidentialité</button>
                </div>

                <ul class="hero-trust-strip" aria-label="Garanties clés">
                  <li>
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" aria-hidden="true"><polyline points="20 6 9 17 4 12"/></svg>
                    Sans compte
                  </li>
                  <li>
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" aria-hidden="true"><polyline points="20 6 9 17 4 12"/></svg>
                    Zéro serveur cloud
                  </li>
                  <li>
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" aria-hidden="true"><polyline points="20 6 9 17 4 12"/></svg>
                    Marche même hors-ligne
                  </li>
                </ul>
              </div>

              <!-- Démonstration interactive Avant / Après -->
              <aside class="demo-card" aria-label="Simulation interactive Avant / Après">
                <div class="demo-header">
                  <span class="demo-title">Exemple : pièce d'identité</span>
                  <div class="proof-toggle" role="group" aria-label="Comparer l'état du fichier">
                    <button type="button" class="proof-toggle-btn" id="btn-demo-before" aria-pressed="false">Avant</button>
                    <button type="button" class="proof-toggle-btn" id="btn-demo-after" aria-pressed="true">Après</button>
                  </div>
                </div>

                <div class="demo-preview">
                  <div class="demo-doc">
                    <div class="demo-doc-top">
                      <span class="demo-filename" id="demo-filename">doc_clean_watermarked.jpg</span>
                      <span class="demo-badge demo-badge-safe" id="demo-badge">Prêt à partager</span>
                    </div>

                    <div class="demo-lines">
                      <div class="demo-row">
                        <span class="demo-row-label">Position GPS cachée</span>
                        <span class="demo-row-val demo-val-clean" id="demo-gps">Supprimée (0 donnée)</span>
                      </div>
                      <div class="demo-row">
                        <span class="demo-row-label">Appareil &amp; date exacte</span>
                        <span class="demo-row-val demo-val-clean" id="demo-exif">Effacés localement</span>
                      </div>
                      <div class="demo-row">
                        <span class="demo-row-label">Numéro sensible caché</span>
                        <span class="demo-row-val demo-val-clean" id="demo-redact">Flouté irréversiblement</span>
                      </div>
                      <div class="demo-row">
                        <span class="demo-row-label">Orientation photo</span>
                        <span class="demo-row-val demo-val-clean" id="demo-orient">Droite &amp; verrouillée</span>
                      </div>
                    </div>

                    <div class="demo-watermark" id="demo-watermark">
                      FILIGRANE : « POUR DOSSIER LOCATIF UNIQUEMENT — NOV. 2026 »
                    </div>
                  </div>
                </div>

                <p class="demo-caption" id="demo-caption">
                  Nettoyé localement sur Android, prêt pour PhantomLink, WhatsApp, Gmail ou Leboncoin.
                </p>
              </aside>
            </div>
          </section>

          <!-- BANDEAU DISPONIBILITÉ -->
          <section class="platform-strip reveal" aria-label="Compatibilité actuelle">
            <div class="platform-item">
              <div class="platform-icon" aria-hidden="true">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="6" y="2" width="12" height="20" rx="2"/><line x1="12" y1="18" x2="12.01" y2="18"/></svg>
              </div>
              <div>
                <h2>Android aujourd'hui (iOS en préparation)</h2>
                <p>L'application tourne sur Android ; la version iPhone / iPad est en préparation.</p>
              </div>
            </div>
            <div class="platform-item">
              <div class="platform-icon" aria-hidden="true">
                <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><line x1="2" y1="12" x2="22" y2="12"/><path d="M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
              </div>
              <div>
                <h2>Rien à installer pour recevoir</h2>
                <p>Un simple navigateur suffit sur iPhone, Mac, Windows ou Linux.</p>
              </div>
            </div>
          </section>

          <!-- LES 4 POUVOIRS -->
          <section class="section reveal" id="piliers" aria-labelledby="piliers-title">
            <div class="section-head">
              <span class="section-eyebrow">4 pouvoirs en 1 appli</span>
              <h2 id="piliers-title">L'essentiel en 10 secondes</h2>
            </div>

            <div class="pillars-grid">
              <!-- Pilier 1 -->
              <article class="pillar-card">
                <div class="pillar-top">
                  <div class="pillar-icon" aria-hidden="true">
                    <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/><path d="m9 12 2 2 4-4"/></svg>
                  </div>
                  <div>
                    <div class="pillar-num">1 · Avant d'envoyer</div>
                    <h3>Nettoyer, flouter &amp; filigraner</h3>
                  </div>
                </div>
                <p class="pillar-summary">
                  Retirez l'adresse GPS de vos photos, masquez un numéro et ajoutez un filigrane anti-fraude sur vos PDF.
                </p>
                <details class="more-box">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">En savoir plus</span><span class="label-open">Réduire</span></summary>
                  <div class="more-box-body">
                    <ul class="pillar-list">
                      <li><strong>Suppression des traces :</strong> GPS, modèle de téléphone, heure et auteur PDF retirés, photos toujours droites, preuve Avant / Après.</li>
                      <li><strong>Masquage irréversible :</strong> pinceau, flou, mosaïque ou émoji ; PDF aplatis sans texte récupérable dessous.</li>
                      <li><strong>Filigrane &amp; dossier virtuel 24 h :</strong> texte répété (libre en Pro) et accès direct depuis WhatsApp, Gmail ou Leboncoin.</li>
                    </ul>
                  </div>
                </details>
              </article>

              <!-- Pilier 2 -->
              <article class="pillar-card pillar-card-vault">
                <div class="pillar-top">
                  <div class="pillar-icon" aria-hidden="true">
                    <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><rect x="3" y="11" width="18" height="11" rx="2"/><path d="M7 11V7a5 5 0 0 1 10 0v4"/><circle cx="12" cy="16" r="1"/></svg>
                  </div>
                  <div>
                    <div class="pillar-num">2 · Hors-ligne chez vous</div>
                    <h3>Coffre-fort PhantomLock</h3>
                  </div>
                </div>
                <p class="pillar-summary">
                  Gardez vos papiers vitaux chiffrés hors-ligne sous code PIN ou empreinte, avec sauvegarde <code>.plbak</code>.
                </p>
                <details class="more-box">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">En savoir plus</span><span class="label-open">Réduire</span></summary>
                  <div class="more-box-body">
                    <ul class="pillar-list">
                      <li><strong>100 % hors-ligne :</strong> passeport, carte vitale et codes restent sur votre téléphone.</li>
                      <li><strong>Lien direct avec le Sas :</strong> nettoyez et filigranez une pièce coffrée juste avant envoi sans toucher à l'original.</li>
                      <li><strong>Anti-curieux &amp; export <code>.plbak</code> :</strong> blocage temporaire après 3 mauvais codes sans perte, transfert facile vers un nouveau mobile.</li>
                    </ul>
                  </div>
                </details>
              </article>

              <!-- Pilier 3 -->
              <article class="pillar-card">
                <div class="pillar-top">
                  <div class="pillar-icon" aria-hidden="true">
                    <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M22 2 11 13"/><path d="m22 2-7 20-4-9-9-4Z"/></svg>
                  </div>
                  <div>
                    <div class="pillar-num">3 · Transferts directs</div>
                    <h3>Envoyer &amp; recevoir sans cloud</h3>
                  </div>
                </div>
                <p class="pillar-summary">
                  Transférez d'un appareil à l'autre par Wi-Fi, sans box ni Internet, ou à distance — sans créer de compte.
                </p>
                <details class="more-box">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">En savoir plus</span><span class="label-open">Réduire</span></summary>
                  <div class="more-box-body">
                    <ul class="pillar-list">
                      <li><strong>3 modes réseau :</strong> Wi-Fi local, Wi-Fi autonome créé par le mobile (sans box) ou Internet P2P jusqu'à 100 Go (PC/App en Pro).</li>
                      <li><strong>Sécurisé &amp; pratique :</strong> lien ou QR code + PIN à 4 chiffres, partage depuis la galerie, aperçu photo et refus fichier par fichier.</li>
                      <li><strong>Diffusion &amp; Demandes (Pro) :</strong> jusqu'à 100 téléchargements ou lien de dépôt pour recevoir des pièces chez vous.</li>
                    </ul>
                  </div>
                </details>
              </article>

              <!-- Pilier 4 -->
              <article class="pillar-card">
                <div class="pillar-top">
                  <div class="pillar-icon" aria-hidden="true">
                    <svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"/><path d="M8 10h.01"/><path d="M12 10h.01"/><path d="M16 10h.01"/></svg>
                  </div>
                  <div>
                    <div class="pillar-num">4 · En direct</div>
                    <h3>Chat, Vocal &amp; Contacts Favoris</h3>
                  </div>
                </div>
                <p class="pillar-summary">
                  Discutez sans historique, parlez en talkie-walkie et joignez vos proches à distance par simple QR code.
                </p>
                <details class="more-box">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">En savoir plus</span><span class="label-open">Réduire</span></summary>
                  <div class="more-box-body">
                    <ul class="pillar-list">
                      <li><strong>Chat éphémère :</strong> aucune trace gardée ; le bouton « Brûler le fil » efface tout immédiatement des deux écrans.</li>
                      <li><strong>Talkie-walkie vocal :</strong> échangez en direct à la voix pendant votre transfert.</li>
                      <li><strong>Contacts Favoris sans annuaire :</strong> scannez un QR code face à face pour réveiller et joindre votre proche plus tard sans numéro ni e-mail.</li>
                      <li><strong>Bonus pratiques :</strong> presse-papiers temps réel, point de rendez-vous, salle d'attente (Pro) et carte de visite vCard.</li>
                    </ul>
                  </div>
                </details>
              </article>
            </div>
          </section>

          <!-- SCÉNARIOS CONCRETS DU QUOTIDIEN -->
          <section class="section reveal" id="usages" aria-labelledby="usages-title">
            <div class="section-head">
              <span class="section-eyebrow">En pratique</span>
              <h2 id="usages-title">À quoi ça sert dans la vraie vie ?</h2>
            </div>

            <div class="scenario-shell">
              <div class="scenario-tablist" role="tablist" aria-label="Exemples d'utilisation" focusgroup="tablist nomemory">
                <button type="button" role="tab" class="scenario-tab" id="sc-tab-1" aria-selected="true" aria-controls="sc-panel-1" focusgroupstart>
                  🏠 Dossier locatif
                </button>
                <button type="button" role="tab" class="scenario-tab" id="sc-tab-2" aria-selected="false" aria-controls="sc-panel-2">
                  🛒 Leboncoin / Vinted
                </button>
                <button type="button" role="tab" class="scenario-tab" id="sc-tab-3" aria-selected="false" aria-controls="sc-panel-3">
                  📦 Gros dossier
                </button>
                <button type="button" role="tab" class="scenario-tab" id="sc-tab-4" aria-selected="false" aria-controls="sc-panel-4">
                  🧳 Voyage &amp; mobile
                </button>
              </div>

              <div id="sc-panel-1" role="tabpanel" aria-labelledby="sc-tab-1">
                <p class="pillar-summary"><strong>Dossier location protégé :</strong> floutez les numéros inutiles, ajoutez un filigrane « Dossier locatif » et envoyez sans laisser de copie sur un cloud.</p>
                <details class="more-box more-box-section">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">Voir les 3 étapes</span><span class="label-open">Masquer</span></summary>
                  <div class="more-box-body">
                    <ol class="scenario-steps">
                      <li><span class="step-num">1</span><span>Importez CNI et justificatifs dans le Sas PhantomLink.</span></li>
                      <li><span class="step-num">2</span><span>Masquez au doigt, filigranez et aplatissez le PDF.</span></li>
                      <li><span class="step-num">3</span><span>Envoyez par lien avec PIN 4 chiffres (ou directement dans Gmail).</span></li>
                    </ol>
                  </div>
                </details>
              </div>

              <div id="sc-panel-2" role="tabpanel" aria-labelledby="sc-tab-2" hidden="until-found">
                <p class="pillar-summary"><strong>Annonces sans fuite d'adresse :</strong> la position GPS de votre maison et le modèle de votre mobile sont retirés avant publication.</p>
                <details class="more-box more-box-section">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">Voir les 3 étapes</span><span class="label-open">Masquer</span></summary>
                  <div class="more-box-body">
                    <ol class="scenario-steps">
                      <li><span class="step-num">1</span><span>Ouvrez la photo de l'objet dans PhantomLink.</span></li>
                      <li><span class="step-num">2</span><span>GPS et métadonnées disparaissent ; floutez une plaque ou un reflet si besoin.</span></li>
                      <li><span class="step-num">3</span><span>Piochez l'image propre depuis Leboncoin ou Vinted (purgée auto en 24 h).</span></li>
                    </ol>
                  </div>
                </details>
              </div>

              <div id="sc-panel-3" role="tabpanel" aria-labelledby="sc-tab-3" hidden="until-found">
                <p class="pillar-summary"><strong>Vidéos et gros dossiers :</strong> envoyez en qualité originale jusqu'à 100 Go (PC/App en Pro) directement vers un navigateur sans rien installer.</p>
                <details class="more-box more-box-section">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">Voir les 3 étapes</span><span class="label-open">Masquer</span></summary>
                  <div class="more-box-body">
                    <ol class="scenario-steps">
                      <li><span class="step-num">1</span><span>Partagez vos fichiers vers PhantomLink depuis votre galerie.</span></li>
                      <li><span class="step-num">2</span><span>Choisissez Wi-Fi local (500 Mo gratuit), Wi-Fi autonome ou Internet P2P (Pro).</span></li>
                      <li><span class="step-num">3</span><span>Votre contact scanne le QR code ou ouvre le lien dans son navigateur.</span></li>
                    </ol>
                  </div>
                </details>
              </div>

              <div id="sc-panel-4" role="tabpanel" aria-labelledby="sc-tab-4" hidden="until-found">
                <p class="pillar-summary"><strong>Papiers vitaux &amp; changement de téléphone :</strong> gardez passeport et codes hors-ligne dans votre coffre et exportez tout en un fichier <code>.plbak</code>.</p>
                <details class="more-box more-box-section">
                  <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">Voir les 3 étapes</span><span class="label-open">Masquer</span></summary>
                  <div class="more-box-body">
                    <ol class="scenario-steps">
                      <li><span class="step-num">1</span><span>Rangez vos pièces importantes dans le Coffre PhantomLock.</span></li>
                      <li><span class="step-num">2</span><span>Sortez-en une copie vers le Sas pour la filigraner si un hôtel vous la demande.</span></li>
                      <li><span class="step-num">3</span><span>Exportez votre sauvegarde chiffrée <code>.plbak</code> pour restaurer sur un autre Android.</span></li>
                    </ol>
                  </div>
                </details>
              </div>
            </div>
          </section>

          <!-- GRATUIT VS PRO (Résumé visuel + Tableau dépliable) -->
          <section class="section reveal" id="quotas" aria-labelledby="quotas-title">
            <div class="section-head">
              <span class="section-eyebrow">Formules claires</span>
              <h2 id="quotas-title">Gratuit ou Pro</h2>
            </div>

            <div class="plans-summary-grid">
              <article class="plan-card">
                <h3><span>Gratuit</span><span class="chip">0 € · Sans compte</span></h3>
                <ul class="plan-highlights">
                  <li>3 fichiers / jour au Sas + dossier 24 h</li>
                  <li>Wi-Fi local &amp; autonome jusqu'à 500 Mo</li>
                  <li>1 coffre (3 fichiers) + export <code>.plbak</code></li>
                  <li>Réception gratuite de tout contact Pro</li>
                </ul>
              </article>

              <article class="plan-card plan-card-pro">
                <h3><span>PhantomLink Pro</span><span class="chip">Via Google Play</span></h3>
                <ul class="plan-highlights">
                  <li>Sas &amp; filigrane libre illimités</li>
                  <li>Transferts Internet P2P jusqu'à 100 Go*</li>
                  <li>Coffre 200 fichiers / 4 Go + Demandes de dépôt</li>
                  <li>Appels Favoris, Diffusion 100x &amp; Salle d'attente</li>
                </ul>
              </article>
            </div>

            <details class="more-box more-box-section">
              <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">Voir le tableau complet des quotas</span><span class="label-open">Masquer le tableau</span></summary>
              <div class="more-box-body">
                <div class="table-wrap" tabindex="0" role="region" aria-labelledby="caption-plans">
                  <table class="data-table table-plans">
                    <caption id="caption-plans">Comparatif détaillé entre PhantomLink Gratuit et PhantomLink Pro</caption>
                    <thead>
                      <tr>
                        <th scope="col">Usage</th>
                        <th scope="col">Gratuit (0 €)</th>
                        <th scope="col">PhantomLink Pro</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <th scope="row">Sas de nettoyage, floutage &amp; filigrane</th>
                        <td><strong>3 fichiers / jour</strong> (filigrane avec signature PhantomLink) + disque virtuel 24 h</td>
                        <td><span class="tag-yes">Illimité</span> · Filigrane 100 % personnalisé sans mention (texte, opacité, densité)</td>
                      </tr>
                      <tr>
                        <th scope="row">Transferts en Wi-Fi local &amp; Wi-Fi autonome</th>
                        <td>Jusqu'à <strong>500 Mo / fichier</strong> · 1 téléchargement · 20 min max · PIN 4 chiffres</td>
                        <td><span class="tag-yes">Illimité</span> · Durée prolongée · Diffusion multi-destinataires (jusqu'à 100 téléchargements)</td>
                      </tr>
                      <tr>
                        <th scope="row">Transferts à distance par Internet (P2P)</th>
                        <td><span class="tag-no">Non inclus</span> (réception d'un contact Pro gratuite)</td>
                        <td><span class="tag-yes">Jusqu'à 100 Go</span> vers PC/Mac ou entre applis Android*</td>
                      </tr>
                      <tr>
                        <th scope="row">Coffre-fort hors-ligne &amp; sauvegarde .plbak</th>
                        <td>1 coffre · <strong>3 fichiers / 80 Mo max</strong> · Export/import <code>.plbak</code> inclus</td>
                        <td><span class="tag-yes">Jusqu'à 200 fichiers / 4 Go</span> · Export/import <code>.plbak</code> inclus</td>
                      </tr>
                      <tr>
                        <th scope="row">Demande de fichiers / secrets &amp; Salle d'attente</th>
                        <td><span class="tag-no">Pro uniquement</span></td>
                        <td><span class="tag-yes">Inclus</span> · Lien de dépôt vers votre mobile + validation manuelle des arrivants</td>
                      </tr>
                      <tr>
                        <th scope="row">Chat éphémère &amp; Talkie-walkie vocal</th>
                        <td>Chat texte · Audio <strong>5 min en local</strong> · 1 carte vCard / jour</td>
                        <td><span class="tag-yes">Toute la session en local &amp; sur Internet</span> · Pièces jointes chat 25 Mo · vCard illimitées</td>
                      </tr>
                      <tr>
                        <th scope="row">Contacts Favoris (réveil à distance)</th>
                        <td>Réception &amp; réponse <span class="tag-yes">Gratuit</span> (ajout QR inclus)</td>
                        <td><span class="tag-yes">Appels &amp; envois sortants illimités</span> vers vos contacts appairés</td>
                      </tr>
                    </tbody>
                  </table>
                </div>
                <p class="table-note">
                  * Limite technique du navigateur mobile : vers Chrome/Safari sur smartphone, le plafond est de <strong>512 Mo</strong> pour préserver la mémoire du navigateur. Vers un PC/Mac ou entre applis Android, la limite atteint <strong>100 Go</strong>.
                </p>
              </div>
            </details>
          </section>

          <!-- COMPARATIF CONCURRENCE (3 cartes synthétiques + Tableau dépliable) -->
          <section class="section reveal" id="comparatif" aria-labelledby="compare-title">
            <div class="section-head">
              <span class="section-eyebrow">En un coup d'œil</span>
              <h2 id="compare-title">Pourquoi pas juste WhatsApp ou WeTransfer ?</h2>
            </div>

            <div class="compare-summary-grid">
              <article class="compare-mini-card">
                <h3>Vs WeTransfer / Cloud</h3>
                <p>Zéro serveur de stockage et vos fichiers partent déjà nettoyés et filigranés.</p>
              </article>
              <article class="compare-mini-card">
                <h3>Vs WhatsApp / Signal</h3>
                <p>Sans numéro de téléphone, zéro compression vidéo et coffre hors-ligne intégré.</p>
              </article>
              <article class="compare-mini-card">
                <h3>Vs LocalSend</h3>
                <p>Marche même sans box Wi-Fi, à distance sur Internet, avec protection des PDF.</p>
              </article>
            </div>

            <details class="more-box more-box-section">
              <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">Comparer ligne par ligne</span><span class="label-open">Masquer le comparatif</span></summary>
              <div class="more-box-body">
                <div class="table-wrap" tabindex="0" role="region" aria-labelledby="caption-compare">
                  <table class="data-table table-compare">
                    <caption id="caption-compare">Comparaison grand public des usages et garanties</caption>
                    <thead>
                      <tr>
                        <th scope="col">Besoin au quotidien</th>
                        <th scope="col">PhantomLink</th>
                        <th scope="col">Signal</th>
                        <th scope="col">WhatsApp</th>
                        <th scope="col">WeTransfer / SwissTransfer</th>
                        <th scope="col">LocalSend</th>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <th scope="row">Nettoie GPS, floute &amp; filigrane avant partage</th>
                        <td><span class="tag-yes">Oui complet</span> (+ PDF aplati)</td>
                        <td>Floutage simple</td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                      </tr>
                      <tr>
                        <th scope="row">Aucun compte, e-mail ou numéro requis</th>
                        <td><span class="tag-yes">Oui (0 donnée)</span></td>
                        <td><span class="tag-no">Numéro requis</span></td>
                        <td><span class="tag-no">Numéro + compte</span></td>
                        <td>E-mail souvent requis</td>
                        <td><span class="tag-yes">Oui</span></td>
                      </tr>
                      <tr>
                        <th scope="row">Transfert direct sans serveur cloud</th>
                        <td><span class="tag-yes">Oui (Wi-Fi &amp; P2P)</span></td>
                        <td><span class="tag-no">Relais serveur</span></td>
                        <td><span class="tag-no">Serveurs Meta</span></td>
                        <td><span class="tag-no">Stocké en ligne</span></td>
                        <td><span class="tag-yes">Wi-Fi local</span></td>
                      </tr>
                      <tr>
                        <th scope="row">Marche sans box ni réseau Internet</th>
                        <td><span class="tag-yes">Oui (Wi-Fi autonome)</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Routeur requis</span></td>
                      </tr>
                      <tr>
                        <th scope="row">Coffre-fort hors-ligne + sauvegarde .plbak</th>
                        <td><span class="tag-yes">Oui (.plbak)</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                        <td><span class="tag-no">Non</span></td>
                      </tr>
                      <tr>
                        <th scope="row">Disponibilité mobile</th>
                        <td><span class="tag-warn">Android (iOS en préparation)</span></td>
                        <td>Android &amp; iOS</td>
                        <td>Android &amp; iOS</td>
                        <td>Web &amp; applis</td>
                        <td>Android, iOS &amp; PC</td>
                      </tr>
                    </tbody>
                  </table>
                </div>
              </div>
            </details>
          </section>

          <!-- VÉRIFICATIONS PUBLIQUES & LIMITES ASSUMÉES -->
          <section class="section reveal" id="confiance" aria-labelledby="trust-title">
            <div class="section-head">
              <span class="section-eyebrow">Confiance &amp; franchise</span>
              <h2 id="trust-title">Vérifications publiques</h2>
            </div>

            <div class="audit-grid">
              <a class="audit-card" href="https://observatory.mozilla.org/analyze/ghostshare-signal.dkstudiodev86.workers.dev" target="_blank" rel="noopener noreferrer">
                <span class="audit-score">A+ · 155/100</span>
                <span class="audit-name">Mozilla HTTP Observatory</span>
                <span class="audit-link-label">Vérifier ↗</span>
              </a>

              <a class="audit-card" href="https://securityheaders.com/?q=https%3A%2F%2Fghostshare-signal.dkstudiodev86.workers.dev%2F&amp;followRedirects=on" target="_blank" rel="noopener noreferrer">
                <span class="audit-score">Note A+</span>
                <span class="audit-name">SecurityHeaders.com</span>
                <span class="audit-link-label">Vérifier ↗</span>
              </a>

              <a class="audit-card" href="https://www.immuniweb.com/websec/ghostshare-signal.dkstudiodev86.workers.dev/" target="_blank" rel="noopener noreferrer">
                <span class="audit-score">Grade A</span>
                <span class="audit-name">ImmuniWeb SSL / WebSec</span>
                <span class="audit-link-label">Vérifier ↗</span>
              </a>

              <a class="audit-card" href="https://internet.nl/site/ghostshare-signal.dkstudiodev86.workers.dev/4359100/" target="_blank" rel="noopener noreferrer">
                <span class="audit-score">75 % · Code 0</span>
                <span class="audit-name">Internet.nl &amp; Scans code</span>
                <span class="audit-link-label">Vérifier ↗</span>
              </a>
            </div>

            <div class="honesty-card">
              <h3>Limites assumées</h3>
              <p class="pillar-summary">Android aujourd'hui (iOS en préparation), aucun audit payant de cabinet privé sur le code mobile, et adresses IP visibles entre les deux appareils lors d'un transfert direct.</p>
              <details class="more-box more-box-section">
                <summary><i class="chev" aria-hidden="true">▸</i><span class="label-closed">En savoir plus</span><span class="label-open">Réduire</span></summary>
                <div class="more-box-body">
                  <ul>
                    <li><strong>Android aujourd'hui, iOS en préparation :</strong> iPhone/iPad reçoivent déjà vos fichiers dans leur navigateur.</li>
                    <li><strong>Pas d'audit payant de cabinet privé sur le code mobile :</strong> les scores ci-dessus portent sur notre portail web et nos scans automatisés ; le code mobile n'a pas passé d'audit payant ANSSI/Quarkslab/Cure53.</li>
                    <li><strong>Direct P2P = IP visible par votre correspondant :</strong> utilisez un VPN si vous devez masquer votre adresse réseau.</li>
                    <li><strong>Après téléchargement :</strong> votre contact contrôle son fichier (d'où l'utilité du filigrane). Sur Wi-Fi public ouvert, préférez le Point d'accès autonome ou Internet P2P.</li>
                  </ul>
                </div>
              </details>
            </div>
          </section>

          <!-- QUESTIONS FRÉQUENTES -->
          <section class="section reveal" id="faq" aria-labelledby="faq-title">
            <div class="section-head">
              <h2 id="faq-title">Questions rapides</h2>
            </div>

            <div class="faq-list">
              <details class="faq-item">
                <summary>Mon correspondant doit-il installer quelque chose sur iPhone ou PC ?</summary>
                <p>Non : il clique simplement sur votre lien (ou scanne le QR code) dans Safari, Chrome, Edge ou Firefox.</p>
              </details>
              <details class="faq-item">
                <summary>Mes fichiers passent-ils par vos serveurs ?</summary>
                <p>Non : le nettoyage, le coffre et vos sauvegardes restent 100 % sur votre téléphone, et les transferts circulent directement entre appareils.</p>
              </details>
              <details class="faq-item">
                <summary>Que faire si j'oublie le code PIN de mon coffre ?</summary>
                <p>Par conception, personne (pas même l'éditeur) ne peut le réinitialiser : gardez précieusement votre mot de passe.</p>
              </details>
            </div>
          </section>
        </div>
      </div>
    </section>

    <!-- =========================================================
         ONGLET 2 : POLITIQUE DE CONFIDENTIALITÉ & MENTIONS LÉGALES
         ========================================================= -->
    <section id="panel-privacy" role="tabpanel" aria-labelledby="tab-privacy" hidden="until-found">
      <div class="panel-inner">
        <div class="container legal-shell">
          <div class="legal-header">
            <h1>Politique de Confidentialité &amp; Mentions Légales</h1>
            <p class="legal-meta">
              Application : <strong>PhantomLink (GhostMesh)</strong> · Éditeur : Jean Virassa (DK Studio)<br />
              Contact : <a href="mailto:contact@dkstudio.dev">contact@dkstudio.dev</a> · Dernière mise à jour : 11 novembre 2026
            </p>
          </div>

          <div class="legal-card">
            <strong>Synthèse en langage clair.</strong>
            PhantomLink est un outil logiciel technique décentralisé combinant le partage pair-à-pair (P2P direct), des coffres locaux chiffrés et un Sas de protection de la vie privée (purification des métadonnées, masquage et filigrane sans cloud).
            <strong>Aucun fichier, document, secret, message ou flux audio ne transite par, ni n'est hébergé sur un serveur de stockage cloud appartenant à l'éditeur.</strong>
            L'éditeur n'a aucun accès à vos données et ne tient aucun registre ou historique de vos échanges. Vous demeurez l'unique responsable du contenu que vous traitez, transférez ou recevez.
          </div>

          <div class="legal-body">
            <h2>1. Statut Juridique d'Éditeur Logiciel (Pure Tool Provider)</h2>
            <p>L'application PhantomLink est fournie en tant qu'outil logiciel technique neutre et décentralisé (disponible sur Android, avec réception compatible navigateur web).</p>
            <ul>
              <li><strong>Absence totale d'hébergement :</strong> L'éditeur n'exploite aucun serveur d'hébergement, de stockage de fichiers ou de base de données de contenu. L'éditeur <strong>n'est pas un hébergeur de données</strong> au sens de l'article 6 de la Loi pour la Confiance dans l'Économie Numérique (LCEN) ni de la Directive e-Commerce européenne.</li>
              <li><strong>Zéro contrôle éditorial :</strong> L'éditeur n'exerce aucun contrôle technique, a priori ou a posteriori, sur les données échangées entre pairs ou scellées dans les coffres de l'application.</li>
            </ul>

            <h2>2. Clause de Non-Responsabilité &amp; Exonération de Garantie</h2>
            <p>L'utilisateur final est le seul et unique responsable des contenus émis, demandés, reçus ou stockés via l'application :</p>
            <ul>
              <li><strong>Licéité des contenus :</strong> L'utilisateur s'engage à respecter scrupuleusement les lois et réglementations en vigueur dans sa juridiction (droits de propriété intellectuelle, secret des affaires, respect de la vie privée, interdiction des contenus illicites).</li>
              <li><strong>Innocuité &amp; Sécurité :</strong> L'éditeur décline toute responsabilité quant à l'exactitude, la légalité ou la dangerosité (virus, logiciels malveillants, malwares, rançongiciels) des fichiers reçus d'un tiers. L'utilisateur a la responsabilité exclusive de vérifier l'identité de son correspondant avant tout téléchargement ou exécution.</li>
              <li><strong>Fourniture « En l'état » (Clause AS IS) :</strong> Le logiciel est fourni sans garantie d'aucune sorte, expresse ou implicite, quant à sa continuité de service, son adéquation à un besoin spécifique ou son invulnérabilité face à des compromissions matérielles du terminal récepteur. En aucun cas l'auteur ne pourra être tenu responsable de préjudices directs ou indirects, pertes de données ou litiges consécutifs à l'utilisation du logiciel.</li>
            </ul>

            <div class="legal-warning">
              <strong>Transparence sur l'absence d'audit de sécurité indépendant certifié :</strong><br />
              Le logiciel mobile PhantomLink <strong>n'a pas fait l'objet d'un audit de sécurité payant ni d'une certification formelle par un organisme d'État (type ANSSI) ou un cabinet d'audit spécialisé (type Quarkslab, Cure53, Synacktiv)</strong>. Les garanties énoncées reposent sur la conception interne de l'éditeur, l'application de primitives cryptographiques reconnues (AES-256-GCM, WebRTC DTLS) et les vérifications publiques automatisées du portail de signalisation. Les utilisateurs traitant des données hautement sensibles ou classifiées sont invités à conduire leur propre évaluation de risque avant usage.
            </div>

            <h2>3. Absence Totale de Journalisation (No-Logs Policy)</h2>
            <p>L'éditeur applique une politique stricte de zéro donnée personnelle :</p>
            <ul>
              <li><strong>Zéro collecte d'identité :</strong> Aucun nom, aucune adresse e-mail ni aucun numéro de téléphone n'est exigé pour faire fonctionner l'application.</li>
              <li><strong>Zéro historique :</strong> L'éditeur ne conserve, ne vend et ne monétise aucun log de transfert, aucun journal de session et aucun historique de messages.</li>
              <li><strong>Purge volatile :</strong> Les tampons de mémoire vive (RAM) sont libérés et réécriturés dès la clôture de la session sur l'appareil.</li>
            </ul>

            <h2>4. Rôle des Services Tiers d'Infrastructure</h2>
            <p>Pour permettre l'interconnexion P2P directe et les notifications sans créer de compte central, l'application s'appuie sur des composants tiers strictement limités :</p>

            <div class="table-wrap" tabindex="0" role="region" aria-labelledby="caption-thirdparty">
              <table class="data-table table-thirdparty">
                <caption id="caption-thirdparty">Services tiers strictement limités utilisés pour l'infrastructure technique</caption>
                <thead>
                  <tr>
                    <th scope="col">Service Tiers</th>
                    <th scope="col">Rôle Technique</th>
                    <th scope="col">Nature des Données</th>
                    <th scope="col">Confidentialité &amp; Conservation</th>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <th scope="row">Cloudflare Workers</th>
                    <td>Courtier de signalisation WebRTC éphémère (rendez-vous initial pour négocier SDP/ICE).</td>
                    <td>Adresses IP de transit, horodatages et identifiants de session temporaires.</td>
                    <td><strong>100 % volatile en mémoire vive (RAM)</strong>. Aucun stockage de contenu. Journaux techniques réseau régis par la politique de Cloudflare Inc.</td>
                  </tr>
                  <tr>
                    <th scope="row">Google Firebase (FCM)</th>
                    <td>Relais de réveil push asynchrone (fonctionnalité Phantom Wake).</td>
                    <td>Enveloppe binaire opaque chiffrée AES-256-GCM via clé symétrique locale (PSK).</td>
                    <td><strong>Relais aveugle (Zero-Knowledge)</strong> : Google transporte des octets chiffrés sans détenir la clé de déchiffrement stockée dans le Keystore matériel du smartphone.</td>
                  </tr>
                  <tr>
                    <th scope="row">Google Play Billing</th>
                    <td>Gestion des abonnements et achats de la version Pro.</td>
                    <td>Traitement financier de la transaction.</td>
                    <td>L'éditeur n'a accès à <strong>aucune coordonnée bancaire</strong>, gérée exclusivement par Google LLC.</td>
                  </tr>
                </tbody>
              </table>
            </div>

            <h2>5. Fonctionnalités Réelles &amp; Périmètre Technique</h2>
            <p>L'application propose exclusivement les fonctions suivantes :</p>
            <ul>
              <li><strong>Sas de Confidentialité &amp; Purification de Métadonnées (PrivacyShield) :</strong> Inspection et élimination intégrale des métadonnées identifiantes (coordonnées GPS, modèle d'appareil photo, horodatages, profil logiciel, auteur/créateur de document PDF) opérée 100 % localement en mémoire vive sur votre appareil, avec preuve interactive Avant / Après, renommage anonyme et cuisson automatique de l'orientation portrait des photos sans transit réseau ni cloud.</li>
              <li><strong>Studio de Masquage Tactile &amp; Aplatissement PDF (Zero-Recovery) :</strong> Caviardage destructif au doigt (pinceau, flou gaussien, mosaïque de pixels, émojis protecteurs) avec écrasement physique irréversible des données de pixels en mémoire vive, et génération de documents PDF 100 % aplatis matriciels (0 calque amovible, 0 texte sélectionnable, 0 métadonnée résiduelle).</li>
              <li><strong>Filigrane Anti-Usurpation Documentaire :</strong> Incrustation indélébile de trames répétées sur photos et documents PDF multi-pages à contraste calibré pour neutraliser les risques d'usurpation d'identité (CNI, avis d'imposition, fiches de paie, dossiers locatifs).</li>
              <li><strong>Disque Virtuel SAF &amp; Purge Zéro-Résidu 24h :</strong> Exposition temporaire des documents purifiés via le Storage Access Framework Android (« Ouvrir à partir de ») avec purge automatique programmée après 24 heures et purge manuelle immédiate.</li>
              <li><strong>Partage de fichiers (mono et multi-fichiers) :</strong> Transfert direct en local (LAN/SoftAP) ou par Internet P2P WebRTC sans hébergement intermédiaire, avec sélection unitaire par le destinataire, mode Diffusion et partage express Android.</li>
              <li><strong>Partage de secrets &amp; mots de passe :</strong> Transmission volatile autodestructible après consultation.</li>
              <li><strong>Demande de fichiers / secrets (Option Pro) :</strong> Génération d'un lien de dépôt sécurisé pour recevoir des éléments directement sur son appareil.</li>
              <li><strong>Chat éphémère &amp; presse-papiers / vCard / point de rendez-vous :</strong> Échanges directs en mémoire vive (RAM-only), sans historique ni serveur de messages.</li>
              <li><strong>Conférence vocale Push-To-Talk (PTT) :</strong> Flux audio direct chiffré de bout en bout (DTLS-SRTP) en mode talkie-walkie.</li>
              <li><strong>Coffres PhantomLock &amp; sauvegardes portables <code>.plbak</code> :</strong> Stockage local chiffré au repos (AES-256-GCM, PBKDF2 120 000 itérations) sous protection exclusive du PIN / mot de passe de l'utilisateur, avec synergie bidirectionnelle de scellement et d'anonymisation dans le Sas et export portable chiffré.</li>
              <li><strong>Contacts Favoris (Phantom Wake) :</strong> Réveil push sécurisé entre terminaux appairés via clé symétrique (PSK 256 bits).</li>
            </ul>

            <h2>6. Modèle de Menace &amp; Recommandations de Sécurité</h2>
            <ul>
              <li><strong>Mode Local (LAN HTTP pour fichiers) :</strong> Le contenu est chiffré applicativement de bout en bout (clé dans l'ancre <code>#key</code>), protégeant contre l'<strong>écoute passive</strong> (sniffing Wi-Fi). Sur un réseau public hostile (café, gare) où un attaquant actif pourrait modifier le trafic HTTP (ARP spoofing), l'utilisateur est invité à activer le <strong>mode Point d'accès direct (SoftAP)</strong> ou le <strong>mode P2P Internet</strong>.</li>
              <li><strong>Mode P2P Internet :</strong> Le tunnel est sécurisé par DTLS. Pour les échanges hautement sensibles, les correspondants sont invités à valider visuellement la concordance de leur code de sécurité (SAS) affiché à l'écran.</li>
              <li><strong>Coffres PhantomLock &amp; sauvegardes <code>.plbak</code> :</strong> En cas d'oubli définitif du secret ou PIN de déchiffrement, <strong>aucune procédure de réinitialisation ou de récupération n'est possible</strong> par l'éditeur.</li>
            </ul>

            <h2>7. Permissions Requises par l'Appareil</h2>
            <p>L'application sollicite uniquement les permissions strictement nécessaires à son fonctionnement :</p>
            <ul>
              <li><strong>Caméra :</strong> Scan du QR code pour rejoindre instantanément une session ou appairer un contact (aucun enregistrement ni diffusion vidéo).</li>
              <li><strong>Microphone :</strong> Transmission audio lors de la conférence vocale Push-To-Talk uniquement.</li>
              <li><strong>Accès réseau / Wi-Fi :</strong> Établissement du serveur local éphémère ou du point d'accès SoftAP.</li>
              <li><strong>Stockage / Fichiers :</strong> Sélection des fichiers à traiter ou émettre, ou enregistrement des fichiers reçus sur le terminal.</li>
            </ul>

            <h2>8. Vos Droits (RGPD) &amp; Contact</h2>
            <p>Étant donné que l'éditeur ne détient aucune base de données d'utilisateurs, aucun compte et aucun fichier, il ne dispose d'aucun moyen technique de consulter, restituer ou supprimer vos contenus locaux ou vos échanges P2P.</p>
            <p>
              Pour toute question légale, technique ou relative au support :<br />
              <strong>DK Studio (Jean Virassa)</strong> — <a href="mailto:contact@dkstudio.dev">contact@dkstudio.dev</a>
            </p>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer class="site-footer">
    <div class="container footer-inner">
      <div>
        <strong>PhantomLink (GhostMesh)</strong> · DK Studio — Application Android sans cloud, sans compte et sans traceur publicitaire.
      </div>
      <div class="footer-links">
        <button type="button" class="footer-link-btn" data-open-tab="showcase">Présentation</button>
        <button type="button" class="footer-link-btn" data-open-tab="privacy">Confidentialité &amp; Mentions légales</button>
        <a href="mailto:contact@dkstudio.dev">contact@dkstudio.dev</a>
      </div>
    </div>
  </footer>

  <script>
    (() => {
      // 1. Gestion des groupes d'onglets accessibles (clavier + ARIA + until-found / beforematch)
      function initTabGroup(tabs, panels, onSwitch) {
        function activate(nextTab, focusTab) {
          tabs.forEach((tab, idx) => {
            const selected = tab === nextTab;
            tab.setAttribute("aria-selected", selected ? "true" : "false");
            tab.tabIndex = selected ? 0 : -1;
            const panel = panels[idx];
            if (!panel) return;
            if (selected) {
              panel.removeAttribute("hidden");
            } else {
              panel.setAttribute("hidden", "until-found");
            }
          });
          if (focusTab) nextTab.focus();
          if (onSwitch) onSwitch(nextTab);
        }

        tabs.forEach((tab, index) => {
          tab.tabIndex = tab.getAttribute("aria-selected") === "true" ? 0 : -1;
          tab.addEventListener("click", () => activate(tab, false));
          tab.addEventListener("keydown", (event) => {
            let nextIndex = null;
            if (event.key === "ArrowRight") nextIndex = (index + 1) % tabs.length;
            else if (event.key === "ArrowLeft") nextIndex = (index - 1 + tabs.length) % tabs.length;
            else if (event.key === "Home") nextIndex = 0;
            else if (event.key === "End") nextIndex = tabs.length - 1;
            if (nextIndex !== null) {
              event.preventDefault();
              activate(tabs[nextIndex], true);
            }
          });
        });

        panels.forEach((panel, index) => {
          panel.addEventListener("beforematch", () => {
            if (tabs[index]) activate(tabs[index], false);
          });
        });

        return activate;
      }

      // Onglets principaux (Présentation vs Confidentialité)
      const mainTabs = [
        document.getElementById("tab-showcase"),
        document.getElementById("tab-privacy")
      ];
      const mainPanels = [
        document.getElementById("panel-showcase"),
        document.getElementById("panel-privacy")
      ];

      const activateMainTab = initTabGroup(mainTabs, mainPanels, (selectedTab) => {
        const isPrivacy = selectedTab.id === "tab-privacy";
        if (window.history && window.history.replaceState) {
          const targetHash = isPrivacy ? "#privacy" : "#presentation";
          if (window.location.hash !== targetHash) {
            window.history.replaceState(null, "", targetHash);
          }
        }
      });

      function openMainTabByKey(key, scrollTop) {
        const target = key === "privacy" ? mainTabs[1] : mainTabs[0];
        activateMainTab(target, false);
        if (scrollTop) window.scrollTo({ top: 0, behavior: "auto" });
      }

      // Support liens profonds (?tab=privacy, #privacy, #confidentialite, #mentions-legales)
      function syncTabFromLocation() {
        const hash = window.location.hash.toLowerCase();
        const params = new URLSearchParams(window.location.search);
        const tabParam = (params.get("tab") || "").toLowerCase();
        if (
          tabParam === "privacy" ||
          tabParam === "confidentialite" ||
          hash === "#privacy" ||
          hash === "#confidentialite" ||
          hash === "#mentions-legales"
        ) {
          openMainTabByKey("privacy", false);
        }
      }
      syncTabFromLocation();
      window.addEventListener("hashchange", syncTabFromLocation);

      // Boutons & liens internes ouvrant un onglet principal
      document.querySelectorAll("[data-open-tab]").forEach((el) => {
        el.addEventListener("click", () => {
          openMainTabByKey(el.getAttribute("data-open-tab"), true);
        });
      });

      document.getElementById("brand-home").addEventListener("click", () => {
        openMainTabByKey("showcase", true);
      });

      // Onglets secondaires (Scénarios concrets)
      const scenarioTabs = [
        document.getElementById("sc-tab-1"),
        document.getElementById("sc-tab-2"),
        document.getElementById("sc-tab-3"),
        document.getElementById("sc-tab-4")
      ];
      const scenarioPanels = [
        document.getElementById("sc-panel-1"),
        document.getElementById("sc-panel-2"),
        document.getElementById("sc-panel-3"),
        document.getElementById("sc-panel-4")
      ];
      initTabGroup(scenarioTabs, scenarioPanels);

      // 2. Simulation interactive Avant / Après du Hero
      const btnBefore = document.getElementById("btn-demo-before");
      const btnAfter = document.getElementById("btn-demo-after");
      const demoFilename = document.getElementById("demo-filename");
      const demoBadge = document.getElementById("demo-badge");
      const demoGps = document.getElementById("demo-gps");
      const demoExif = document.getElementById("demo-exif");
      const demoRedact = document.getElementById("demo-redact");
      const demoOrient = document.getElementById("demo-orient");
      const demoWatermark = document.getElementById("demo-watermark");
      const demoCaption = document.getElementById("demo-caption");

      function setDemoState(afterMode) {
        btnAfter.setAttribute("aria-pressed", afterMode ? "true" : "false");
        btnBefore.setAttribute("aria-pressed", afterMode ? "false" : "true");

        if (afterMode) {
          demoFilename.textContent = "doc_clean_watermarked.jpg";
          demoBadge.textContent = "Prêt à partager";
          demoBadge.className = "demo-badge demo-badge-safe";
          demoGps.textContent = "Supprimée (0 donnée)";
          demoExif.textContent = "Effacés localement";
          demoRedact.textContent = "Flouté irréversiblement";
          demoOrient.textContent = "Droite & verrouillée";
          [demoGps, demoExif, demoRedact, demoOrient].forEach((n) => {
            n.className = "demo-row-val demo-val-clean";
          });
          demoWatermark.hidden = false;
          demoCaption.textContent =
            "Tout est préparé directement dans votre téléphone Android. Vous pouvez ensuite envoyer le fichier par PhantomLink, ou même dans WhatsApp, Gmail ou Leboncoin sans fuite cachée.";
        } else {
          demoFilename.textContent = "IMG_20261110_CNI_Salon.jpg";
          demoBadge.textContent = "Traces exposées";
          demoBadge.className = "demo-badge demo-badge-risk";
          demoGps.textContent = "48.8566° N, 2.3522° E (visible !)";
          demoExif.textContent = "Samsung S24 · 10/11/2026 09:42";
          demoRedact.textContent = "N° CNI & adresse lisibles";
          demoOrient.textContent = "Rotation par balise EXIF";
          [demoGps, demoExif, demoRedact, demoOrient].forEach((n) => {
            n.className = "demo-row-val demo-val-exposed";
          });
          demoWatermark.hidden = true;
          demoCaption.textContent =
            "Sans nettoyage, une simple photo ou un PDF contient souvent votre adresse GPS exacte, le modèle de votre téléphone et reste facile à réutiliser pour usurper votre identité.";
        }
      }

      btnBefore.addEventListener("click", () => setDemoState(false));
      btnAfter.addEventListener("click", () => setDemoState(true));

      // 3. Sélecteur de thème (Clair par défaut -> Sombre au clic)
      const themeBtn = document.getElementById("theme-toggle");
      const themeLabel = document.getElementById("theme-label");
      const themeIcon = document.getElementById("theme-icon");
      const root = document.documentElement;
      const modes = ["light", "dark"];
      let modeIndex = 0;

      function applyTheme(mode) {
        if (mode === "dark") {
          root.setAttribute("data-theme", "dark");
          themeLabel.textContent = "Thème : Sombre";
          themeIcon.textContent = "☾";
        } else {
          root.setAttribute("data-theme", "light");
          themeLabel.textContent = "Thème : Clair";
          themeIcon.textContent = "☀";
        }
      }

      applyTheme("light");

      themeBtn.addEventListener("click", () => {
        modeIndex = (modeIndex + 1) % modes.length;
        applyTheme(modes[modeIndex]);
      });
    })();
  </script>
</body>
</html>
