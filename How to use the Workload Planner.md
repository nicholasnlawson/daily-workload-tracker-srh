# Pharmacy Workload Planner – How to Use

The Workload Planner builds the daily directorate workload table from the Pharmacy **Ward List** and **Review List** reports. Everything runs inside your web browser on your own PC. Nothing is uploaded or sent anywhere.

## What must be in the folder

Keep these together in the same folder on the shared drive:

| Item                    | Purpose                                                 |
| ----------------------- | ------------------------------------------------------- |
| `Workload Planner.html` | The tool – open this                                    |
| `lib` folder            | PDF reader used by the tool – **do not delete or move** |
| `ward_directory.csv`    | List of wards with their specialty and directorate      |
| `Critical_meds.json`    | Critical medicines (and their aliases) to flag          |

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

> Anything typed into the page is **not saved**. Copy the table into your email before closing or refreshing the page.

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

Expand **Patient details** at the bottom to see each patient's status, last review date, hours since admission (Hx patients) and number of unreviewed items. This section is **not** included in the email copy.

- **Print** next to a ward prints that ward's list.
- **Print all ward lists** prints every ward in the selected directorate, one per page (A4 landscape).

Unreviewed items are matched to patients by hospital number. Any items that can't be matched are listed in red under that ward's table, for example if the patient has moved or been discharged.

For patients who need a history (Hx), any of their unreviewed items that appear on the critical medicines list are shown in the **Comment** column as **CRITICAL MEDS:** followed by the medicine names in red. If the patient already has a comment, the critical medicines go on an extra row underneath. Hover over the names to see the matching review list items.

## Updating the critical medicines list

`Critical_meds.json` lists the critical medicines. Edit it in Notepad (or any text editor) and keep the file name the same. Each medicine has a `name` (shown on the list) and optional `aliases` (other names, such as brand names, that also count as that medicine):

```json
{
  "medications": [
    { "name": "Tacrolimus", "aliases": ["Adoport", "Prograf"] },
    { "name": "Insulin", "aliases": [] }
  ]
}
```

- Names and aliases are matched as whole words, in any case, anywhere in the review list medication text. For example, `Insulin` matches "Insulin Aspart" but not "Insulinx".
- Every name and alias needs double quotes, and every item except the last in a list needs a comma after it. If the file has a mistake, the status box says so and no critical medicines are flagged.
- Each browser remembers the last list it loaded. After editing the file, load the folder again.

## Updating the ward directory

`ward_directory.csv` controls which wards belong to each directorate. Open it in **Excel**, edit it, and save it in **CSV** format, keeping the file name the same. Columns:

| Column       | Example                                                                               |
| ------------ | ------------------------------------------------------------------------------------- |
| Ward         | `DGC31` – must match the ward code exactly as printed on the reports (e.g. `EAU:1-3`) |
| Display Name | `C31 (ESAU)` – name shown in the table                                                |
| Specialty    | `General Surgery (Emerg)`                                                             |
| Directorate  | `Surgery`                                                                             |

The table follows the row order of this file. Each browser remembers the last directory it loaded, so after editing the file, load it again (**Load ward directory (CSV)…** or Choose folder).

## Troubleshooting

| Problem                                   | What to do                                                                                                                                           |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| A ward is missing from the table          | Check the ward is in `ward_directory.csv` with the right directorate. Wards not in the directory appear under **Not in directory** in the drop-down. |
| Specialty is blank                        | The ward code in the CSV doesn't match the report – check spelling and punctuation                                                                   |
| No CRITICAL MEDS shown                    | Check the status box says the critical medicines list is loaded. Only Hx patients with unreviewed items are checked.                                 |
| "Cannot read … the lib folder is missing" | The `lib` folder must sit next to `Workload Planner.html`                                                                                            |
| A ward is reported twice                  | If several copies of the same ward's report are loaded, the most recent is used and a note is shown. Clear out old reports to avoid this.            |
| Old figures showing                       | Click **Clear reports** and load the folder again                                                                                                    |
| Paste into email loses formatting         | Paste with Ctrl+V into a new Outlook message (HTML format), not plain text                                                                           |
