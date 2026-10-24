# eOcene 25 — a calm iOS-inspired web workspace

The user explicitly replaces the restored 23.16.1 visual identity with a complete iOS-inspired system, grounded in Apple Human Interface Guidelines and Apple Design Resources. This supersedes earlier visual-world decisions while preserving application data, authentication and existing product features.

## Mode and identity
Operate on dashboard pages, Read on public guides and legal pages. White grouped surfaces on a quiet neutral canvas, charcoal gray in dark mode, consistent blue emphasis, 22px card corners, a single subtle blue-gray 1px edge, no ornamental halos or decorative glass. Native system typography uses the Apple system font where present and Segoe UI/Inter elsewhere. No proprietary Apple font or symbol files are redistributed.

## Structure
The sidebar distinguishes school tasks from account items. Notifications join settings and privacy in its bottom group. Each page title and the personalized greeting sit inside a clear card. Footer stays at the bottom of the document flow through a flex workspace and never overlays content. Desktop body text grows to 17px and 18px on wide screens, supporting text to 14–15px. Layouts reflow through workspace container queries. Grade and subject descriptions are left aligned. Matching card roles share spacing, text scale and action placement. Recent grades use a two-column layout on wide workspaces.

## Explicit exceptions
The calendar page's component, controls and calendar-specific styles are preserved. Its inherited content font remains Inter. Shared app shell navigation and theme follow the new identity. Keyboard focus, semantic errors, verification and privacy controls remain visible. Swipe actions retain their tested 88px reveal with a 78px action button, leaving a 10px gap outside the unchanged calendar rows.

## Functional details
Moje eOcene remains at /ocene. The average trend is chronological by actual entry timestamp, retaining each original grade date for its record. Home tasks show at most three active items. Atomic server cooldown allows new tasks every ten seconds, without restricting completion or edits. Subject goals are selected then explicitly saved. Forecast grade buttons and suggested future combinations use grades 2–5 while existing actual grade 1 values remain included in calculations.

The timer keeps its reliable tracking and audio pause/resume logic. It removes the Pomodoro badge, completed-block counter, break-cycle text and old motivational paragraph. Small liked thoughts rotate every ten minutes on the active timer page. A three-question, in-memory planning card recommends imagery, explaining or practice according to current preferences, without classifying a fixed learning type. Rain and the former sea slot use two quieter real rain recordings with explicit credits and licenses.

## Validation
Use bounded tests for math, chronological data, cooldown boundaries, quiz behavior, subjects, task privacy and timer/audio state transitions. Local browser preview uses the managed-linux execution profile. Inspect published public and available signed-in screens; verify the page scope attribute and computed alignment as well as screenshots. No assertion of all-device screenshot parity is made.

## Responsive refinement 25.1
Shared outer radius is 20px, 18px on phones. Swipe wrappers and their child surfaces inherit the same edge. List rows use a 12px inset radius. One-column layouts take precedence at workspace widths up to 760px, with compact grade, subject and ranking rows. Sidebar glyphs use restrained category colors and a seven-pixel active dot, including the portaled mobile drawer. Ranking toolbar and headings use the same card surface in both themes. Unnecessary row and shell dividers are removed while field borders and focus indicators remain. Route motion targets content rather than the footer and respects reduced motion.

## Motion and footer 25.1.1
Motion stays enabled by default on every device and respects reduced-motion preferences. Lazy panels animate on their actual first mount rather than only animating the loading fallback. Click feedback falls back to opacity when additive transforms are unsupported. Footer is excluded from route motion and sits in a transparent flex spacer with 40px clearance after the last card, 32px on phones, while retaining bottom alignment on short pages.
