# FLIK Merchant Dashboard: UX/UI Gap Analysis Report

**Prepared by:** Principal UX Architect & Design Systems Lead
**Focus Areas:** Information Architecture, Fintech Benchmarks, Interaction Design, Accessibility, and Data UX.

*Note: This report has been updated to reflect live product constraints, technical realities, and specific business requirements.*

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

### 1. Missing Status Indicators (Technical Debt)
*   **Location:** `Invoice`
*   **The Issue:** Invoices currently lack a "Paid/Unpaid" status column due to technical constraints.
*   **Impact:** Forces merchants to cross-reference bank accounts or other systems to know what requires attention, slowing down operations.
*   **Recommendation:** Prioritize resolving the technical constraint on the roadmap. Once resolved, introduce semantic, color-coded status pills (e.g., Green for Lunas, Yellow for Pending).

### 2. Missing Analytical Context (Trend Deltas)
*   **Location:** `Dashboard`, `Customer`, `Laporan`
*   **The Issue:** Metrics show static numbers (e.g., "Jumlah Order: 50") without historical comparison.
*   **Impact:** Merchants cannot gauge growth or velocity.
*   **Recommendation:** Add trend indicators beneath primary metrics (e.g., `↑ 15% vs Minggu Lalu`).

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

### 4. UI Clutter: Repetitive Icons
*   **The Issue:** Repeating the "External Link" icon 20+ times in a single table column.
*   **Recommendation:** Make table text natively clickable (blue/hover underline) instead of using icons.

---

## 🔵 LOW (Quick Wins & Polish)
*Minor visual tweaks and nice-to-haves.*

1. **Missed Onboarding Opportunities:** The empty "Ringkasan penjualan" chart on the Home page looks dead. Add an encouraging CTA (e.g., "Create your first invoice to see data here!").
2. **Contextually Incorrect Placeholders:** The search bar on the `Saldo` page says "Cari data order", but it should say "Cari transaksi".