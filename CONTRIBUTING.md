# Contributing to Seam Cricket Academy Website

Thank you for your interest in contributing to the Seam Cricket Academy website!

## Development Workflow

1. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** in the `astro-revamp/` directory

3. **Test locally**
   ```bash
   cd astro-revamp
   npm run dev
   ```

4. **Build and verify**
   ```bash
   npm run build
   ```

5. **Submit a pull request**

## Code Style Guidelines

### Astro Components

- Use `.astro` extension for all components
- Keep logic in the frontmatter (`---` section)
- Use Tailwind CSS for styling (no inline styles)
- Follow existing naming conventions

### CSS

- Use Tailwind utility classes
- Custom utilities go in `src/styles/base.css`
- Use CSS variables for theme colors

### JavaScript

- Keep scripts minimal and at the bottom of components
- Use TypeScript annotations where helpful
- Prefer vanilla JS over frameworks

## Component Structure

```astro
---
// 1. Imports
import Component from './Component.astro';

// 2. Props/Data
const { prop } = Astro.props;

// 3. Logic
const computedValue = doSomething();
---

<!-- 4. Template -->
<div class="container">
    <Component />
</div>

<!-- 5. Client-side script (if needed) -->
<script>
    // Interactive logic
</script>
```

## Questions?

Contact the development team or open an issue.
