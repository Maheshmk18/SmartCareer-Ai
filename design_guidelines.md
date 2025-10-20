# Personal Finance Management Dashboard - Design Guidelines

## Design Approach

**Selected Approach:** Design System (Modern Financial Dashboard)
**Primary References:** Linear's clean productivity aesthetic + Stripe Dashboard's data presentation + Notion's information hierarchy
**Justification:** Finance management tools require trustworthy, efficient, information-dense interfaces where clarity and usability trump visual experimentation. Users need quick access to critical financial data with minimal cognitive load.

---

## Core Design Elements

### A. Color Palette

**Light Mode:**
- Primary: 217 91% 60% (Professional blue - trust and stability)
- Background: 0 0% 100% (Pure white)
- Surface: 220 13% 97% (Soft gray for cards)
- Border: 220 13% 91% (Subtle dividers)
- Text Primary: 222 47% 11% (Near black)
- Text Secondary: 215 16% 47% (Muted gray)
- Success: 142 71% 45% (Green for income/positive)
- Danger: 0 72% 51% (Red for expenses/overspending)
- Warning: 38 92% 50% (Amber for budget alerts)

**Dark Mode:**
- Primary: 217 91% 60% (Same blue maintains consistency)
- Background: 222 47% 11% (Deep charcoal)
- Surface: 217 33% 17% (Elevated dark gray)
- Border: 217 33% 24% (Subtle dark dividers)
- Text Primary: 210 40% 98% (Off-white)
- Text Secondary: 215 20% 65% (Muted light gray)
- Success/Danger/Warning: Same hues, adjusted lightness for dark backgrounds

### B. Typography

**Font Families:**
- Primary: 'Inter' from Google Fonts (clean, highly legible for data)
- Monospace: 'JetBrains Mono' for currency values and numbers

**Type Scale:**
- Page Titles: text-3xl font-semibold (30px)
- Section Headers: text-xl font-semibold (20px)
- Card Titles: text-lg font-medium (18px)
- Body Text: text-base font-normal (16px)
- Labels/Captions: text-sm font-medium (14px)
- Currency/Numbers: text-2xl font-mono font-bold for emphasis

### C. Layout System

**Spacing Primitives:** Use Tailwind units of 2, 4, 6, 8, and 12 for consistency
- Component padding: p-6 (cards, sections)
- Component gaps: gap-4 or gap-6 (between elements)
- Section spacing: space-y-8 (vertical rhythm)
- Page margins: p-8 on desktop, p-4 on mobile

**Grid Structure:**
- Dashboard: 3-column grid (lg:grid-cols-3) for stat cards
- Analytics: 2-column grid (lg:grid-cols-2) for charts
- Transaction list: Single column with full-width table
- Sidebar: Fixed 256px width on desktop, collapsible on mobile

### D. Component Library

**Navigation:**
- Fixed sidebar with icon + text navigation items
- Dashboard, Transactions, Add Transaction, Budgets, Analytics, Settings sections
- Active state: Primary color background with white text
- Hover: Subtle background tint

**Data Display:**
- Stat Cards: Elevated with subtle shadow, rounded-lg borders, featuring large monospace numbers, percentage changes with arrow indicators, and category icons
- Charts: Clean axis labels, grid lines in muted colors, tooltips on hover, using primary color scheme with transparency
- Transaction Table: Striped rows, sortable columns, inline category badges, amount color-coded (green/red), hover row highlight
- Budget Progress Bars: Height h-2, rounded-full, with dual colors (remaining vs. spent), percentage labels above

**Forms:**
- Input Fields: Consistent border-2 styling, focus ring with primary color, proper label hierarchy, validation states (red border for errors)
- Buttons: Primary (solid primary color), Secondary (outline with border-2), Danger (solid red for delete actions)
- Dropdowns: Shadcn Select component with search for categories

**Cards & Containers:**
- All cards: bg-surface border border-border rounded-lg p-6 shadow-sm
- Hover state for interactive cards: subtle shadow increase
- No excessive depth or layering - keep hierarchy clear through spacing

**Icons:**
- Use Heroicons (outline style) via CDN
- Icon size: h-5 w-5 for inline, h-6 w-6 for standalone
- Categories get dedicated icons (shopping cart, car, home, etc.)

### E. Data Visualization

**Chart Style:**
- Line charts for trend analysis (monthly spending)
- Donut/Pie charts for category breakdowns
- Bar charts for budget vs. actual comparisons
- Color scheme: Primary blue for main data, categorical colors for multi-series
- Clean grid, subtle gridlines, responsive sizing
- Use Chart.js or Recharts with custom theme matching design system

**Dashboard Metrics:**
- Large number display (text-4xl font-mono) with smaller label below
- Positive/negative indicators with up/down arrows and green/red colors
- Percentage change from previous period in smaller text

---

## Page-Specific Layouts

**Dashboard Home:**
- Top row: 4 stat cards (Total Income, Total Expenses, Net Savings, Budget Health) in grid-cols-1 md:grid-cols-2 lg:grid-cols-4
- Second row: 2-column layout - Monthly trend line chart (left 2/3) + Category breakdown donut chart (right 1/3)
- Third row: Recent transactions list (last 5) with "View All" link

**Transactions Page:**
- Filter bar: Date range picker, category dropdown, type selector (Income/Expense)
- Full-width sortable table with columns: Date, Description, Category, Amount, Actions (edit/delete icons)
- Pagination at bottom
- Floating action button (bottom-right) for "Add Transaction"

**Add/Edit Transaction:**
- Clean form layout: single column, max-w-md centered
- Fields: Description (text), Amount (number with currency symbol), Category (searchable select), Date (date picker), Type (toggle Income/Expense)
- Large primary "Save Transaction" button at bottom

**Budgets Page:**
- Category cards grid (2-column on desktop)
- Each card shows: Category name with icon, Budget amount, Spent amount, Progress bar, Remaining amount
- Edit budget button per category
- Alert badge if over budget (red) or nearing limit (amber)

**Analytics Page:**
- Tab navigation: Monthly View, Category View, Trends
- Large charts with filters (time range selector)
- Export button (top-right) for CSV/PDF reports

---

## Interaction Patterns

**Micro-interactions:**
- Smooth transitions: transition-all duration-200 ease-in-out
- Hover states on all interactive elements
- Loading states with skeleton screens for data fetching
- Success/error toast notifications (top-right corner)

**Responsiveness:**
- Mobile: Stack all grids to single column, collapse sidebar to hamburger menu
- Tablet: 2-column grids where appropriate
- Desktop: Full 3-4 column layouts with fixed sidebar

---

## Accessibility & Quality

- All interactive elements have focus states with ring-2 ring-primary
- Color never the only indicator (use icons + text for status)
- Consistent dark mode throughout including form inputs
- Minimum touch target size: 44x44px for mobile
- ARIA labels on icon-only buttons
- Keyboard navigation support throughout

---

## Visual Hierarchy Principles

1. **Financial data is king:** Large, bold numbers with monospace fonts
2. **Status clarity:** Immediate visual feedback on budget health through color and progress indicators
3. **Scannable tables:** Clear column headers, alternating row colors, aligned numeric data
4. **Breathing room:** Generous whitespace prevents overwhelming users with dense financial information
5. **Trustworthy aesthetic:** Professional color scheme, consistent spacing, no unnecessary animations