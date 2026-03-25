# Design System Strategy: The Kinetic Sentinel

### 1. Overview & Creative North Star
The Creative North Star for this design system is **"The Kinetic Sentinel."** In the high-stakes world of cybersecurity, interface design must balance two extremes: the absolute precision of mission-critical data and the fluid, atmospheric nature of digital threats. 

This system breaks the "enterprise template" look by rejecting rigid, boxed-in layouts in favor of an **Editorial Tech** aesthetic. We utilize intentional asymmetry, overlapping glass surfaces, and a high-contrast typographic scale to create a sense of depth and hierarchy. Rather than a flat dashboard, the UI is treated as a tactical heads-up display (HUD)—a series of intelligent layers that prioritize human cognition over raw data dumping.

### 2. Colors & Tonal Architecture
The palette is rooted in deep charcoal to minimize eye fatigue during long shifts, punctuated by "Electric" and "Neon" accents that guide the eye toward action.

*   **Primary (#b0c6ff):** The Electric Blue. Used for primary actions and system-level focus.
*   **Secondary (#d3fbff):** The Neon Cyan. Reserved for active states, data highlights, and "current" indicators.
*   **Semantic Risks:** 
    *   High: `tertiary_container` (#ff5545)
    *   Medium: `on_tertiary_fixed_variant` (#930005)
    *   Low: `secondary_fixed_dim` (#00dbe9) (Note: Adjusted to align with the provided token palette for visual harmony).

**The "No-Line" Rule:**
Borders are a relic of print. In this system, we prohibit 1px solid borders for sectioning. Boundaries are defined solely through background color shifts. A `surface-container-low` component sits on a `surface` background to create a "soft" edge. 

**Surface Hierarchy & Nesting:**
We use a tiered stacking logic to define importance:
1.  **Base:** `surface` (#131314) – The infinite void.
2.  **Sectioning:** `surface-container-low` (#1c1b1c) – To group related modules.
3.  **Active Modules:** `surface-container-highest` (#353436) – For the most interactive elements.

**The "Glass & Gradient" Rule:**
To achieve the "premium" feel, floating elements (modals, tooltips, sidebars) must use Glassmorphism. This is achieved by combining `surface_container` tokens at 60-80% opacity with a `backdrop-blur` of 20px-40px.

### 3. Typography: Editorial Precision
The typography system uses a dual-font approach to marry technical utility with futuristic branding.

*   **Display & Headlines (Space Grotesk):** This typeface provides a geometric, slightly "glitch-tech" personality. Use `display-lg` (3.5rem) for high-level metrics and `headline-sm` (1.5rem) for section titles to create an authoritative, editorial look.
*   **Body & Labels (Inter):** The industry standard for legibility. All data tables, logs, and descriptions use Inter. 
    *   **Hierarchy Tip:** Use `label-sm` (0.6875rem) in all-caps with a 5% letter-spacing for metadata to give it a "military-spec" aesthetic.

### 4. Elevation & Depth: Tonal Layering
We move away from the "shadow-on-white" paradigm of the 2010s. Depth here is atmospheric.

*   **Layering Principle:** Place a `surface-container-lowest` card inside a `surface-container-high` section. The "recession" of the darker color creates a natural pocket for data without adding visual noise.
*   **Ambient Shadows:** For floating glass panels, use shadows with a `32px` blur and `8%` opacity, using the `primary` token color instead of black. This creates a "glow" that feels like light emitting from the screen.
*   **The "Ghost Border":** When a border is required for accessibility, use the `outline_variant` token at **15% opacity**. This creates a "suggestion" of a boundary that only appears when the user focuses on it.

### 5. Components

**Glassmorphic Cards:**
*   **Background:** `surface_container_low` at 70% opacity.
*   **Blur:** 24px backdrop filter.
*   **Border:** Top-left 1px "Ghost Border" (at 20% opacity) to simulate a light hit on a glass edge.
*   **Padding:** Scale `6` (1.3rem) for internal breathing room.

**Buttons:**
*   **Primary:** Uses a gradient from `primary` (#b0c6ff) to `primary_container` (#568dff). No border.
*   **Secondary:** Ghost-style. No background. `outline` token for the text and a subtle `0.5px` Ghost Border.
*   **States:** On hover, primary buttons should emit a soft glow using the `primary` color (12px blur, 20% opacity).

**Status Badges (Glow Items):**
*   High-priority alerts must not just be red; they must "pulse."
*   Use `error_container` (#93000a) as the base with a secondary outer glow of `error` (#ffb4ab) at 30% opacity.

**Sidebar & Navigation:**
*   **State:** Transition from collapsed (80px) to expanded (260px) using a non-linear `cubic-bezier(0.4, 0, 0.2, 1)` easing.
*   **Separation:** No vertical line. Use a `surface_bright` background for the sidebar against the `surface_dim` main content area.

**Input Fields:**
*   Avoid the "box" look. Use a `surface_container_lowest` background with a `2px` bottom-bar highlight in `secondary` (#d3fbff) only when the field is active.

### 6. Do's and Don'ts

**Do:**
*   **Use Asymmetry:** Place a large metric (`display-lg`) off-center to create visual interest.
*   **Respect the Spacing Scale:** Use `spacing-10` (2.25rem) between major modules to let the data "breathe."
*   **Layer with Purpose:** Ensure that the most critical "Action Required" item is always on the `surface-container-highest` tier.

**Don't:**
*   **Don't Use Dividers:** Never use a horizontal `<hr>` or a 1px border to separate list items. Use vertical whitespace (`spacing-3`) or subtle alternating background shades.
*   **Don't Over-Glow:** If everything glows, nothing is important. Reserve glow effects exclusively for "Critical" and "High" risk levels.
*   **Don't Use Pure White:** Never use #FFFFFF. Always use `on_surface` (#e5e2e3) for text to prevent visual "halving" against the dark background.