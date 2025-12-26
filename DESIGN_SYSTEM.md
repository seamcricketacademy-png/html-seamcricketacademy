# Seam Cricket Academy - Design System Guidelines

## 1. Iconography
To maintain the "Weightless/Kinetic" aesthetic, all icons must strictly adhere to these standards.

### Feature/Program Icons
*   **Type**: 3D Emoji / High-Fidelity Render.
*   **Format**: Transparent PNG or SVG (No background colors).
*   **Size**: `w-16 h-16` (64px x 64px).
*   **Styling**:
    *   **NO** CSS blending modes for standard assets (ensure assets are pre-processed to transparency).
    *   **Object Fit**: `object-contain` to prevent cropping.
*   **Context**: Placed inside a `text-5xl` container for alignment with text-based emojis.

**Code Example:**
```jsx
<img 
    src="/assets/images/icon_name.png" 
    alt="Title" 
    class="w-16 h-16 object-contain"
    loading="lazy"
/>
```

## 2. Card Components (`ProgramCard`)
*   **Background**: `glass-panel` (Glassmorphism).
*   **Hover Effect**: `hover:border-neon/30` + `transition-all duration-500`.
*   **Padding**: `p-10`.
*   **Grid Layout**: `grid lg:grid-cols-2 gap-8`.

## 3. Colors & Theme
*   **Theme**: Dark / Night Mode.
*   **Accent**: `text-neon` (Fluorescent Green/Yellow).
*   **Text**: 
    *   Headings: `text-white` `font-light` `tracking-wide`.
    *   Body: `text-white/60` `leading-relaxed`.

## 4. Asset Management
*   **Location**: `/public/assets/images/`.
*   **Naming Convention**: `snake_case` (e.g., `bowling_machine_transparent.png`).
