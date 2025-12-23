# Project Context & Memory

> [!IMPORTANT]
> **Active Directory**: `d:\html-seamcricketacademy\astro-revamp`
> **Framework**: Astro 5.0 + Tailwind CSS + React.
> **Status**: Active Development / Revamp.

## 1. Core Mandates
*   **"Value-First" Architecture**: Prioritize high-value UI/UX (Awe-Inspiring) over minor constraints.
*   **"Weightless" Aesthetic**: Premium, dark-mode, neon-accented, glassmorphism design.
*   **Plug-and-Play Standards**: All assets and components must follow documented standards to avoid regression.

## 2. Proactive Analysis Protocol
**Mandatory Checks** (Perform these BEFORE starting work):
1.  **Repository Root Verification**: Always check the root `d:\html-seamcricketacademy` for `.github/workflows` to identify CI/CD pipelines.
2.  **Legacy vs. Active**: Confirm which directory is the "Source of Truth" (currently `astro-revamp`).
3.  **Environment Scan**: Check `package.json` and `astro.config.mjs` for build targets.

## 3. Key Documentation
*   **`DESIGN_SYSTEM.md`**: (In project root) Contains strict guidelines for Iconography (Size: w-16), Card Styles, and Colors. **CONSULT THIS BEFORE MAKING UI CHANGES.**
*   **`.github/workflows/deploy.yml`**: Automated deployment pipeline configuration.

## 4. Workflow Memory
### Deployment (Automated)
*   **Trigger**: Push to `main` branch.
*   **Action**: GitHub Actions automatically builds and deploys to GitHub Pages.
*   **Command**: `git push origin main` (Do NOT manually drag-drop/upload).

### Asset Handling (Icons)
*   **Do not use raw JPGs** for icons.
*   **Do not depend on CSS blending** (`mix-blend-screen`) unless absolutely necessary.
*   **Preferred Workflow**:
    1.  Generate/Obtain 3D Emoji style asset.
    2.  Process transparency (use `node remove_bg.mjs` helper if needed).
    3.  Save as Transparent PNG.
    4.  Use `w-16 h-16 object-contain`.

### Development
*   **Command**: `npm run dev`
*   **Localhost**: http://localhost:4321/
*   **Logic Pitfalls**: When editing `.astro` files, do NOT mix HTML template code into the Frontmatter (Javascript) section. Keep them strictly separate.

## 4. Recent Changes (Dec 2024)
*   **Bowling Machine Icon**: Replaced emoji with custom 3D asset (`bowling_machine_transparent.png`).
*   **Icon Standardization**: Increased all feature icons to `w-16` (64px) for visibility.

## 5. File Structure
*   `src/components/`: UI Components (Programs.astro, etc.)
*   `public/assets/images/`: Static assets.
*   `remove_bg.mjs`: Utility script for rough transparency processing.
