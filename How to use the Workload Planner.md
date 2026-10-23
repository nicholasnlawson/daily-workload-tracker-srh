# Pharmacy Workload Planner – How to Use

The Workload Planner builds the daily directorate workload table from the Pharmacy **Ward List** and **Review List** reports. Everything runs inside your web browser on your own PC. Nothing is uploaded or sent anywhere.

## What must be in the folder

Keep these together in the same folder on the shared drive:

| Item                    | Purpose                                                 |
| ----------------------- | ------------------------------------------------------- |
| `Workload Planner.html` | The tool – open this                                    |
| `lib` folder            | PDF reader used by the tool – **do not delete or move** |
| `ward_directory.js`     | List of wards with their specialty and directorate      |
| `critical_meds.js`      | Critical medicines (and their aliases) to flag          |

The ward directory and critical medicines list load automatically when the page opens. There's no need to select them. Edit them on the **Ward directory** and **Critical medicines** pages of the tool (see below).

Save each day's reports into this folder, or into a subfolder inside it (e.g. `Ward Reports`).

## Daily use

1. **Save the reports.** Run the Ward List and Review List reports and save them into the folder. Either can be **PDF or text**, and a report can cover one ward or several.
2. **Open `Workload Planner.html`**, in Microsoft Edge.
3. **Load the files.** Click **Choose folder…** and select the Workload Planner folder; subfolders are included. You can also drag the files, or the whole folder, onto the page. Your browser may ask you to confirm that you want to share the folder's files with the page; this is normal.
4. **Check the status box.** It lists the reports it found. Read any **Check:** warnings, such as patient totals that don't match the report or wards missing from the directory.
5. **Choose your directorate** from the drop-down.
6. **Fill in the manual fields:**
   - **Boarders** for each ward (Surgery only, unless switched on under **Columns…**).
   - Optionally tick **Include staffing & pharmacist allocation**. This adds the Co-ordinator and Meds Rec section and the AM/PM pharmacist and Comment columns. Each pharmacist name is coloured automatically.
7. **Copy and paste.** Click **Copy table for email**, then paste into Outlook with Ctrl+V.

### Closed wards

A closed ward's Ward List report prints a page that says only **No records found.** Any ward in the ward directory that has no ward list data appears in the table as **Closed** (in red, across the count columns). Its pharmacist and comment boxes can still be filled in, e.g. "Open – 15 patients" or "Email to follow". Closed wards are not included in the totals or the Patient details.

The status box shows how many "No records found" pages each report contains. If the number of wards shown as Closed doesn't match the number of "No records found" pages, a **Check:** warning lists the closed wards. This usually means a ward's report was not run or not saved.

> Anything typed into the page is **not saved**. Copy the table into your email before closing or refreshing the page.

## Ward list for EMR reports

Click **Ward list for EMR reports** at the top of the page to see every ward in the ward directory, in order. Use it to enter ward codes into the EMR report generator quickly:

- **Click a ward code** to copy it, then paste into the EMR with Ctrl+V. Only the code itself copies; the other columns don't.
- **Copy next** copies the wards one at a time in order. The button shows which ward is next.
- The next ward to copy is highlighted **blue**. Copied wards turn **green**.
- A long list scrolls inside its own box, which follows the blue ward, so the buttons stay at the top of the screen.
- **Undo** un-marks the last ward copied. **Reset** clears all the marks.

The list comes from the **Ward directory** page. Copied marks are not saved; refreshing the page clears them.

## What the columns mean

| Column                                         | Meaning                                                                                                                                                |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Pts.**                                       | Patients on the ward list                                                                                                                              |
| **Hx. Total**                                  | Patients with no status code (history needed). Unrecognised codes are also counted here.                                                               |
| **Hx. 18–24 / 24–48 / >48 hrs**                | Hx patients by time since admission, measured to when the report was run. Total also includes patients admitted <18 hrs ago.                           |
| **UQ, Q, PRI, TMR, PRC**                       | Patients by status code. UQs are shown in red.                                                                                                         |
| **PRI >24 hrs**                                | PRI not updated for more than 24 hrs                                                                                                                   |
| **Not r/v >1 week**                            | Patients with a status whose last review was more than 7 days ago                                                                                      |
| **Unreviewed items Total / >48 hrs / >7 days** | Items on the Review List and how long ago they were prescribed. >48 hrs includes the >7 days items. "–" means no review list was loaded for that ward. |

Click **Columns…** to choose which columns appear in the table and the email copy. Surgery and the other directorates (including All loaded wards) each keep their own choices, which are remembered on that computer. By default every column is shown, except **Boarders**, which only appears for Surgery. **Reset to defaults** in the same window restores this.

## Patient details and printing

**Patient details** at the bottom lists every ward in the selected directorate. Click a ward to expand it and see each patient's status, last review date, hours since admission (Hx patients) and number of unreviewed items. This section is **not** included in the email copy.

- **Print** next to a ward prints that ward's list.
- **Print all ward lists** prints every ward in the selected directorate, one per page (A4 landscape).
- **Expand all** / **Collapse all** opens or closes every ward's list at once.
- The **Show** tickboxes filter patients by status (UQ, Q, PRI, TMR, PRC, **Hx required** for no status, and **Other** for unrecognised statuses). When filtered, each ward heading shows e.g. "5 of 24 patients". Printing uses the same filter, so you can print, say, only the Hx required patients.
- Tick **Space for written notes** to add blank space under each patient's **Comments** so notes can be handwritten on the printout.

Unreviewed items are matched to patients by hospital number. Any items that can't be matched are listed in red under that ward's table, for example if the patient has moved or been discharged.

For patients who need a history (Hx), any of their unreviewed items that appear on the critical medicines list are shown in the **Comments** column as **CRITICAL MEDS:** followed by the medicine names in red. If the patient already has a comment, the critical medicines go on an extra row underneath. Hover over the names to see the matching review list items. Medicines that matched but were skipped by an exception (see below) are not listed, but they appear in the hover text with the exception that applied. If a patient only has skipped medicines, a small grey **ⓘ** is shown instead; hover over it to see them.

Patients with no status on the ward list show **Hx required** in bold red across the Status, Last r/v and Days ago columns.

## Updating the ward directory and critical medicines

The **Ward directory** and **Critical medicines** pages (buttons at the top of the tool) let anyone edit the lists:

- **Ward directory** – each ward's **Ward code** (must match the code printed on the reports exactly, e.g. `EAU:1-3`), **Display name** (shown in the table), **Specialty** and **Directorate**. The workload table and the ward list for EMR reports follow this order; use the ↑ ↓ arrows to change it. **Add ward** adds a row at the bottom. The Directorate box suggests the directorates already in use. Keep the spelling the same so wards are grouped together.
  - **Part of (combined ward)** – for a ward that is split across several reports, e.g. EAU-SR, EAU:1-3 and EAU:4-6. Type the same name (e.g. `EAU`) in each part's box; capitals and extra spaces don't matter, and the box suggests names already in use. The parts are then shown as one ward with that name in the workload table and Patient details, at the position of the first part, using its directorate. Its specialty is the parts' specialties separated by commas, each listed once (e.g. all three EAU parts are "EAU", so it shows just "EAU"). In Patient details, beds show their number only, and the note under the heading lists the parts, marking any with no ward list loaded. The combined ward only shows as **Closed** if none of its parts has a ward list. Leave the box blank for wards that stand alone. The name can't be the same as a ward code. The ward list for EMR reports still lists each part separately, as the reports are run per part.
- **Critical medicines** – each medicine's **name** (shown as CRITICAL MEDS) and its **aliases** (other names, such as brand names), separated by commas. Use the search box to find a medicine or alias. **Add medicine** adds a row at the top. The list is sorted A–Z when saved. Names and aliases are matched as whole words, in any case, anywhere in the review list drug name. For example, `Insulin` matches "Insulin Aspart" but not "Insulinx". Medicines can also have **exceptions** (see below).
- **×** deletes a row. Rows with problems (a missing name or code, or a duplicate) turn red when you save, and nothing is saved until they're fixed.
- A dot next to the page button means there are unsaved changes. **Discard changes** goes back to the saved list.

### Critical medicine exceptions

An exception stops a prescription being flagged even though it matches the medicine's name or an alias. For example, Enoxaparin with **Dose is at or below** `40 MG` flags treatment doses but not prophylactic ones. Click **+ Add exception** under a medicine, choose the rule from the drop-down and type the value. A medicine can have several exceptions; if **any** of them applies, that prescription isn't flagged. Tick **Only medicines with exceptions** to list just those.

Each review list item has a **drug name** (the drug name column, e.g. "Enoxaparin 40 MG/0.4 ML Syringe"), a **dose** (e.g. "40 MG"), **directions** (e.g. "ONCE A DAY AT 6pm") and a **type** (SCH, PRN, ONCE). The **full prescription** is all four together.

| Rule                               | Not flagged when…                                | Example value                |
| ---------------------------------- | ------------------------------------------------ | ---------------------------- |
| Drug name contains                 | the drug name contains any of the words          | `cream, ointment, eye drops` |
| Drug name does not contain         | the drug name contains none of the words         | `glargine, detemir`          |
| Full prescription contains         | the full prescription contains any of the words  | `STAT`                       |
| Full prescription does not contain | the full prescription contains none of the words | `EVERY 6 HR`                 |
| Dose is at or below                | the prescribed dose is at or below the amount    | `40 MG`                      |
| Dose is at or above                | the prescribed dose is at or above the amount    | `10000 UNITS`                |
| Prescription type is               | the type is one of those listed                  | `PRN`                        |

- Words are matched as whole words or phrases, in any case. Separate several with commas; any one of them counts. A number only matches a whole number, so `4` doesn't match "40" or "0.4".
- **Dose rules** use the dose column, not the strength in the drug name. A 300 mg/3 ml vial prescribed at 40 mg counts as 40 mg. Doses in mg, g and micrograms are converted to compare, as are ml and litres. A range (e.g. `20-60 MG`) only counts as "at or below" if all of it is. If there's no dose, or its unit can't be compared (e.g. ml against mg), the prescription **is** flagged, to be safe. Leave the unit off (e.g. `40`) to compare the number whatever the unit.
- Text (.txt) review lists cut the drug name off at 35 characters (e.g. "…M/R Ca" for "M/R Capsule"); PDF review lists show it in full. Check that drug name words still match when text reports are used.

**Saving:** click **Save ward_directory.js…** or **Save critical_meds.js…**. In Edge (or Chrome), the first time you save, a folder window opens: choose the **Workload Planner folder** (the one `Workload Planner.html` is in) and click **Select**, then **Save changes** / **Allow** when Edge asks to let the site edit files. The planner checks it's the right folder (it must contain this page and have the same name as the folder the page was opened from) and refuses any other. After that, saving writes straight into that folder, replacing the old file; Edge may ask once per session to allow editing again. To use a different folder (e.g. if the planner has been moved), click **Change save folder…**. The folder is remembered per person, per computer and browser. In other browsers, the file is downloaded instead; move it from Downloads into the Workload Planner folder, replacing the old file.

The changes apply straight away on your screen, and for everyone else the next time they open the planner. Consider keeping a copy of the old file before making big changes.

The files can also be edited by hand in Notepad. They hold one entry per line, in JSON format (double quotes, and a comma after every entry except the last). If a file has a mistake, the status box says so and that list isn't used until it's fixed.

## Troubleshooting

| Problem                                              | What to do                                                                                                                                                  |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| A ward is missing from the table                     | Check the ward is on the **Ward directory** page with the right directorate. Wards not in the directory appear under **Not in directory** in the drop-down. |
| Specialty is blank                                   | The ward code on the **Ward directory** page doesn't match the report – check spelling and punctuation                                                      |
| No CRITICAL MEDS shown                               | Check the status box says the critical medicines list is loaded. Only Hx patients with unreviewed items are checked.                                        |
| "ward_directory.js is missing" (or critical_meds.js) | The file must sit next to `Workload Planner.html` with exactly that name                                                                                    |
| "… has a mistake in it"                              | The file was edited by hand and has a missing comma or quote. Fix it, or put back an earlier copy                                                           |
| Saved changes don't appear for others                | Check the file was saved into the Workload Planner folder with exactly the right name, replacing the old file                                               |
| "Cannot read … the lib folder is missing"            | The `lib` folder must sit next to `Workload Planner.html`                                                                                                   |
| A ward is reported twice                             | If several copies of the same ward's report are loaded, the most recent is used and a note is shown. Clear out old reports to avoid this.                   |
| Old figures showing                                  | Click **Clear reports** and load the folder again                                                                                                           |
| Paste into email loses formatting                    | Paste with Ctrl+V into a new Outlook message (HTML format), not plain text                                                                                  |
