# FLIK Merchant Dashboard: UX/UI Gap Analysis Report

**Prepared by:** Principal UX Architect & Design Systems Lead
**Focus Areas:** Information Architecture, Fintech Benchmarks, Interaction Design, Accessibility, and Data UX.

*Note: This report has been updated to reflect live product constraints and dev-environment mock data artifacts.*

---

## 🛑 CRITICAL (Fix Immediately)
*These issues cause severe user friction or block core business intelligence workflows.*

### 1. Missing Timeframe Context on Dashboard
*   **Location:** `Dashboard`
*   **The Issue:** Top-level metrics like "Total Penghasilan" and "Order Selesai" are displayed without a date picker or timeframe label (e.g., Today, This Month, All-Time).
*   **Impact:** Renders the data useless for business decision-making.
*   **Recommendation:** Add a global date-picker to the Dashboard header and ensure all cards respect that timeframe.

---

## 🟠 HIGH (Schedule for Next Sprint)
*These issues significantly degrade the user experience, violate standard fintech patterns, or cause high cognitive load.*

### 1. Left-Aligned Currency in Financial Tables
*   **Location:** `Saldo`, `Invoice`, `Customer`, `Laporan`
*   **The Issue:** All monetary values (`Rp 500.000`) are left-aligned.
*   **Impact:** Violates standard accounting/fintech UX. The human eye cannot scan or compare the magnitude of numbers easily.
*   **Recommendation:** Update the design system table component to Right-Align or Decimal-Align all currency and numerical count columns.

### 2. Missing Status Indicators (Technical Debt)
*   **Location:** `Invoice`
*   **The Issue:** Invoices currently lack a "Paid/Unpaid" status column due to technical constraints.
*   **Impact:** Forces merchants to cross-reference bank accounts or other systems to know what requires attention, slowing down operations.
*   **Recommendation:** Prioritize resolving the technical constraint on the roadmap. Once resolved, introduce semantic, color-coded status pills (e.g., Green for Lunas, Yellow for Pending).

### 3. Non-Actionable Dashboard Metrics (No Drill-downs)
*   **Location:** `Dashboard`
*   **The Issue:** Cards like "Pengiriman Bermasalah: 7" (7 Problematic Shipments) appear as static text.
*   **Impact:** Merchants see a problem but cannot immediately act on it.
*   **Recommendation:** Make summary cards clickable hyperlinks that route the user to a pre-filtered table (e.g., Shipping table filtered by "Status: Problematic").

### 4. Conflicting Information Architecture (Home vs. Dashboard)
*   **Location:** Left Navigation
*   **The Issue:** Having both "Home" (Quick Actions) and "Dashboard" (Analytics) splits the merchant's "Command Center" into two disconnected screens.
*   **Impact:** Cognitive friction upon login ("Where do I go?").
*   **Recommendation:** Merge these pages. Put top-level analytics and alerts at the top, followed by the "Akses Cepat" action grid below it.

### 5. Missing Analytical Context (Trend Deltas)
*   **Location:** `Dashboard`, `Customer`, `Laporan`
*   **The Issue:** Metrics show static numbers (e.g., "Jumlah Order: 50") without historical comparison.
*   **Impact:** Merchants cannot gauge growth or velocity.
*   **Recommendation:** Add trend indicators beneath primary metrics (e.g., `↑ 15% vs Minggu Lalu`).

### 6. Accessibility: Missing Form Labels
*   **Location:** Global Search Bars
*   **The Issue:** Search inputs rely entirely on placeholder text which disappears when typing.
*   **Impact:** Fails WCAG accessibility audits; high cognitive load for users who forget the specific search criteria.
*   **Recommendation:** Add persistent visual `<label>` tags above inputs, or implement floating labels.

---

## 🟡 MEDIUM (Add to Backlog)
*Inconsistencies and UI clutter that make the platform feel unpolished.*

### 1. Hidden Save Mechanisms (Below the Fold)
*   **Location:** `Personalisasi Checkout`, `Pengaturan Pengiriman`
*   **The Issue:** The "Simpan" (Save) button exists but requires significant vertical scrolling to reach on long pages with many options.
*   **Impact:** Users might forget to scroll down and leave the page, resulting in lost configuration data.
*   **Recommendation:** Implement a sticky footer for the Save action so it is always visible regardless of scroll depth.

### 2. Enhance Table Scrolling UX
*   **Location:** Data Tables (`FLIK Shipping`, `Laporan`, etc.)
*   **The Issue:** While horizontal scrolling exists, wide tables make it easy to lose context of *which* row is being viewed when scrolling far to the right to see statuses.
*   **Recommendation:** Make the first identifier column (e.g., Order ID, Nomor Batch) a "sticky" column that remains fixed on the left while the user scrolls horizontally.

### 3. Inconsistent Localization & Terminology
*   **The Issue:** Mixing English and Indonesian in the same view (e.g., `Appearance` accordion with `Ubah Logo` button). Interchangeable use of "Saldo" and "Kredit" for merchant funds.
*   **Recommendation:** Establish a strict localization dictionary and pick a single mental model for funds (Saldo vs Kredit).

### 4. Flat Call-to-Action (CTA) Hierarchy on Home
*   **The Issue:** All 6 buttons under "Akses Cepat" have the exact same secondary styling.
*   **Recommendation:** Give the most valuable business action (e.g., `Buat Invoice`) primary solid-blue styling to guide new users.

### 5. UI Clutter: Repetitive Icons
*   **The Issue:** Repeating the "External Link" icon 20+ times in a single table column.
*   **Recommendation:** Make table text natively clickable (blue/hover underline) instead of using icons.

### 6. Lack of Breadcrumbs & Deep Navigation
*   **The Issue:** Users navigating deep into an invoice or setting have no visual trail to go back one level.
*   **Recommendation:** Implement standard breadcrumbs (e.g., `FLIK Checkout > Invoice > #00300`) below the page title.

---

## 🔵 LOW (Quick Wins & Polish)
*Minor visual tweaks and nice-to-haves.*

1. **Missed Onboarding Opportunities:** The empty "Ringkasan penjualan" chart on the Home page looks dead. Add an encouraging CTA (e.g., "Create your first invoice to see data here!").
2. **Contextually Incorrect Placeholders:** The search bar on the `Saldo` page says "Cari data order", but it should say "Cari transaksi".
3. **Unpolished Empty States:** The missing logo state on `Personalisasi Checkout` uses a broken browser `<img>` icon. Replace with a deliberate, styled placeholder (dashed box + camera icon).
4. **Cek Red Zone Auto-Suggest:** Ensure the large input field for Address/Postal code includes a robust dropdown auto-suggest to prevent spelling errors.