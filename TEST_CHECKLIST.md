# 🧪 Manual Testing Checklist

Use this checklist to verify all features work correctly after deployment.

---

## 📝 Pre-Testing Setup

- [ ] Open browser (Chrome recommended)
- [ ] Clear browser cache (Ctrl+Shift+Delete)
- [ ] Open DevTools Console (F12)
- [ ] Keep console open to catch any errors

---

## 1️⃣ Survey Testing (`/`)

### Basic Survey Flow
- [ ] Navigate to `https://devsurvey.vercel.app/`
- [ ] Survey loads without errors
- [ ] Claude AI logo/branding visible
- [ ] Chat interface appears

### Question Flow
- [ ] First question appears
- [ ] Type answer and press Enter/Send
- [ ] Next question appears
- [ ] Van Westendorp pricing questions appear (4 prices)
- [ ] JTBD priority ranking appears
- [ ] Pain point questions appear (incident + 5 scores)
- [ ] Interest rating question appears
- [ ] Commitment level question appears
- [ ] Contact info collected (email, name, phone)

### Referral System
- [ ] Test with referral link: `/?ref=TEST123`
- [ ] Referral code displays at end
- [ ] Copy referral link button works
- [ ] "Refer 2 friends" messaging appears

### Data Submission
- [ ] "Submit" button works
- [ ] No console errors appear
- [ ] Thank you message displays
- [ ] Data should appear in admin dashboard

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 2️⃣ Admin Dashboard Testing (`/admin`)

### Page Load
- [ ] Navigate to `https://devsurvey.vercel.app/admin`
- [ ] Dashboard loads without errors
- [ ] Stats cards display at top
- [ ] Response table loads

### Stats Display
- [ ] Total Responses shows correct number
- [ ] Avg Interest shows decimal (e.g., 7.5)
- [ ] Completion Rate shows percentage
- [ ] Total Referrals shows number

### Table Display
- [ ] Table shows all responses
- [ ] Columns: Date, Tools, Role, Interest, Commitment
- [ ] Checkboxes visible in first column
- [ ] "Select All" checkbox in header
- [ ] "View Full" buttons visible
- [ ] "Delete" buttons visible (red)

### Selection System
- [ ] Click individual checkbox - row is selected
- [ ] Selected row count updates
- [ ] Click "Select All" - all rows selected
- [ ] Click "Select All" again - all rows deselected
- [ ] "Delete Selected" button appears when rows selected

### Delete Functionality
**Single Delete:**
- [ ] Click "Delete" button on one row
- [ ] Confirmation dialog appears: "Are you sure...?"
- [ ] Click "Cancel" - nothing happens
- [ ] Click "Delete" again, then "OK" - row deletes
- [ ] Success alert: "Response deleted successfully"
- [ ] Table refreshes without deleted row

**Bulk Delete:**
- [ ] Select 2-3 rows with checkboxes
- [ ] Click "Delete Selected" button
- [ ] Confirmation dialog: "Are you sure you want to delete X response(s)?"
- [ ] Click "Cancel" - nothing happens
- [ ] Select rows again, click "Delete Selected", then "OK"
- [ ] Success alert: "Successfully deleted X response(s)"
- [ ] Table refreshes without deleted rows

### View Full Response
- [ ] Click "View Full" button on any row
- [ ] Modal window appears (large, centered)
- [ ] Modal title: "Survey Response Details"

**Check all sections display:**
- [ ] 📋 Basic Information (date, tools, frequency, spending, role)
- [ ] 😤 Pain Points (incident story, 5 pain scores, workarounds)
- [ ] 🎯 Priorities & Interest (JTBD rankings, why answers, interest)
- [ ] 💰 Van Westendorp Pricing (4 price points)
- [ ] ✅ Commitment & Deal Breakers
- [ ] 📧 Contact Information (email, name, phone, friend emails)
- [ ] 🔗 Referral Information (code, referred_by, count, reward)
- [ ] 💬 Full Conversation Transcript (all Q&A)

**Modal functionality:**
- [ ] Close button (X) works
- [ ] Click outside modal - closes
- [ ] Scroll inside modal works if content is long

### CSV Export
- [ ] Click "Export CSV" button
- [ ] File downloads: `survey-responses-YYYY-MM-DD.csv`
- [ ] Open CSV in Excel/Sheets
- [ ] All 30+ columns present
- [ ] Data matches what's in dashboard
- [ ] Special characters handled correctly (quotes, commas)

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 3️⃣ Analytics Dashboard Testing (`/analytics`)

### Page Load
- [ ] Navigate to `https://devsurvey.vercel.app/analytics`
- [ ] Dashboard loads without errors
- [ ] Title: "Survey Analytics Dashboard"
- [ ] 7 tab buttons visible at top
- [ ] "Overview" tab is active by default

### Tab 1: Overview
**Stats Cards:**
- [ ] Total Responses shows number
- [ ] Completion Rate shows percentage
- [ ] Avg Interest shows decimal
- [ ] Median Price shows dollar amount

**Charts:**
- [ ] Interest Score Distribution chart renders
- [ ] Bar chart with scores 1-10 on X-axis
- [ ] Heights show count per score
- [ ] Hover shows exact count
- [ ] Commitment Levels chart renders (pie/doughnut)
- [ ] Shows early access, waitlist, etc.
- [ ] Hover shows count and percentage

### Tab 2: Van Westendorp
- [ ] Click "Van Westendorp" tab
- [ ] Tab becomes active
- [ ] Content switches to Van Westendorp

**Van Westendorp Chart:**
- [ ] Line chart with 4 curves renders
- [ ] X-axis: Price ($)
- [ ] Y-axis: Cumulative % (0-100)
- [ ] Red line: "Too Cheap"
- [ ] Green line: "Bargain"
- [ ] Yellow line: "Expensive"
- [ ] Red dashed line: "Too Expensive"
- [ ] Hover shows exact values
- [ ] Chart is responsive

**Pricing Insights:**
- [ ] Optimal Price Range displayed
- [ ] Median Bargain Price displayed
- [ ] Median Expensive Price displayed
- [ ] Values make sense (not $0)

**Statistics Table:**
- [ ] Table shows 4 rows (one per price point)
- [ ] Columns: Min, 25th, Median, 75th, Max
- [ ] Values are numbers (not "undefined")

### Tab 3: Pain Analysis
- [ ] Click "Pain Analysis" tab
- [ ] Content switches

**Pain Score Chart:**
- [ ] Bar chart with 5 bars renders
- [ ] Bars: Cost, Quality, Privacy, Speed, Reliability
- [ ] Y-axis: 0-10 scale
- [ ] Heights show average pain scores
- [ ] Hover shows exact average
- [ ] Different colors for each bar

**Key Pain Points:**
- [ ] List of pain points ranked
- [ ] Highest pain score first
- [ ] Shows dimension name + average score

### Tab 4: JTBD Priorities
- [ ] Click "JTBD Priorities" tab
- [ ] Content switches

**Priority Rankings:**
- [ ] Chart renders (bar or horizontal bar)
- [ ] Shows weighted priority scores
- [ ] Clear labels for each priority

**Top Priority Reasons:**
- [ ] List of qualitative "why" answers
- [ ] Shows what users said for their #1 priority

### Tab 5: Tools & Demographics
- [ ] Click "Tools & Demographics" tab
- [ ] Content switches

**Charts (3 total):**
- [ ] AI Tools Usage chart renders
- [ ] Shows Cursor, Copilot, Claude, ChatGPT, etc.
- [ ] User Roles chart renders (pie or bar)
- [ ] Shows Developer, Manager, Founder, Student
- [ ] Current Spending chart renders
- [ ] Shows $0, $10-20, $20-50, $50+ distribution

### Tab 6: Referrals
- [ ] Click "Referrals" tab
- [ ] Content switches

**Referral Metrics (4 stats):**
- [ ] Total Referrals shows number
- [ ] Rewards Earned shows number
- [ ] Viral Coefficient shows decimal (e.g., 0.8)
- [ ] Referral Rate shows percentage

**Referral Funnel Chart:**
- [ ] Chart renders showing 0, 1, 2+ referrals
- [ ] Shows distribution of referral counts

**Top Referrers Table:**
- [ ] Table shows top 10 referrers
- [ ] Columns: Email/Name, Referral Code, Count, Reward
- [ ] Sorted by count (highest first)

### Tab 7: Export Data
- [ ] Click "Export Data" tab
- [ ] Content switches

**Export Options (3 buttons):**
- [ ] "Export CSV" button visible
- [ ] "Export JSON" button visible
- [ ] "Export for Python/R (Analysis-Ready)" button visible

**Export CSV:**
- [ ] Click "Export CSV"
- [ ] File downloads: `survey-data-YYYY-MM-DD.csv`
- [ ] Open in Excel
- [ ] All 30+ columns present
- [ ] Data matches dashboard

**Export JSON:**
- [ ] Click "Export JSON"
- [ ] File downloads: `survey-data-YYYY-MM-DD.json`
- [ ] Open in text editor
- [ ] Valid JSON (proper brackets, commas)
- [ ] Array of objects
- [ ] All fields present

**Export Analysis-Ready:**
- [ ] Click "Export for Python/R"
- [ ] File downloads: `survey-analysis-ready-YYYY-MM-DD.json`
- [ ] Open in text editor
- [ ] Valid JSON
- [ ] Contains encoded fields:
  - [ ] `tools_cursor`, `tools_copilot` (0 or 1)
  - [ ] `frequency_encoded` (1-5)
  - [ ] `spending_encoded` (numbers like 0, 15, 35, 75)
  - [ ] `role_encoded` (1-5)
  - [ ] `pain_avg` (calculated average)
  - [ ] `interested` (0 or 1)
  - [ ] `committed` (0 or 1)
  - [ ] `was_referred` (0 or 1)
  - [ ] `has_email` (0 or 1)
  - [ ] `price_midpoint` (calculated)

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 4️⃣ Cross-Browser Testing

### Chrome
- [ ] Survey works
- [ ] Admin works
- [ ] Analytics works
- [ ] Charts render correctly
- [ ] No console errors

### Firefox
- [ ] Survey works
- [ ] Admin works
- [ ] Analytics works
- [ ] Charts render correctly

### Safari (if available)
- [ ] Survey works
- [ ] Admin works
- [ ] Analytics works
- [ ] Charts render correctly

### Edge
- [ ] Survey works
- [ ] Admin works
- [ ] Analytics works

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 5️⃣ Mobile Testing

### Mobile Chrome
- [ ] Survey responsive
- [ ] Admin table scrollable/readable
- [ ] Analytics charts resize properly
- [ ] Buttons tap-friendly

### Mobile Safari (if available)
- [ ] Survey responsive
- [ ] Admin works
- [ ] Analytics works

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 6️⃣ Data Flow Testing

### End-to-End Test
1. [ ] Complete full survey with unique test data
2. [ ] Note your email/identifier
3. [ ] Visit /admin - find your response
4. [ ] Verify all data matches what you entered
5. [ ] Click "View Full" - verify ALL fields present
6. [ ] Check conversation transcript is complete
7. [ ] Visit /analytics - verify your response in stats
8. [ ] Export CSV - verify your response in file
9. [ ] Export JSON - verify your response in file
10. [ ] Export Analysis-Ready - verify encoded correctly
11. [ ] Return to /admin - delete your test response
12. [ ] Verify deleted from table
13. [ ] Refresh page - confirm still gone
14. [ ] Visit /analytics - verify count decreased by 1

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 7️⃣ Referral System Testing

### Referral Flow
1. [ ] Complete survey, get referral code (e.g., REF123)
2. [ ] Copy referral link
3. [ ] Open incognito/private window
4. [ ] Paste referral link
5. [ ] Complete survey
6. [ ] Visit /admin - find first response
7. [ ] Verify `referral_count` incremented by 1
8. [ ] Repeat with 2nd referral
9. [ ] Verify `referral_count` now = 2
10. [ ] Verify `reward_earned` = true
11. [ ] Visit /analytics - Referrals tab
12. [ ] Verify metrics updated correctly

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 8️⃣ Error Handling Testing

### Test Error Scenarios
- [ ] Disconnect internet, try to load /admin - error handled gracefully
- [ ] Try to delete with no selections - nothing happens (or shows message)
- [ ] Try to export with 0 responses - downloads empty/minimal file
- [ ] Submit survey with missing fields - handles gracefully
- [ ] Check console for any red errors during normal use

**Test Result:** ✅ PASS / ❌ FAIL
**Notes:**

---

## 📊 Overall Test Results

| Component | Status | Notes |
|-----------|--------|-------|
| Survey | ⬜ PASS / ⬜ FAIL | |
| Admin Dashboard | ⬜ PASS / ⬜ FAIL | |
| Analytics Dashboard | ⬜ PASS / ⬜ FAIL | |
| Cross-Browser | ⬜ PASS / ⬜ FAIL | |
| Mobile | ⬜ PASS / ⬜ FAIL | |
| Data Flow | ⬜ PASS / ⬜ FAIL | |
| Referral System | ⬜ PASS / ⬜ FAIL | |
| Error Handling | ⬜ PASS / ⬜ FAIL | |

**Overall Status:** ⬜ READY FOR PRODUCTION / ⬜ NEEDS FIXES

---

## 🐛 Issues Found

### Issue 1
**Description:**
**Severity:** 🔴 Critical / 🟡 Medium / 🟢 Minor
**Steps to Reproduce:**
**Expected:**
**Actual:**

### Issue 2
(Add more as needed)

---

## ✅ Sign-Off

**Tester Name:**
**Date:**
**Browser/OS:**
**Test Duration:**

**Final Status:** ⬜ APPROVED FOR PRODUCTION / ⬜ FIXES REQUIRED

---

**Notes:**
- Test with real data when possible
- Pay attention to console errors
- Test all export formats actually open correctly
- Verify referral system increments correctly
- Check mobile responsiveness thoroughly
