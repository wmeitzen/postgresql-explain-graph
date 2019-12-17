Advanced Features
When Verbose is Off, Row Counts Are Approximate 
If worker information is not available, PEG will approximate them. It does so by multiplying the number of workers launched, plus the parallel leader, by the number of actual rows emitted by the operator. The product will often be close to the actual number of rows had worker info been returned. However, this is considered an estimate, so PEG shows the number of rows (and data mass) with normal font (estimated values) instead of bold font (actual values).

VERBOSE OFF: ROW COUNTS ARE CLOSE



VERBOSE ON: ROWS COUNTS ARE EXACT



In the upper screenshot, you can see how the Parallel Hash Join approximates 86k rows. In the lower screenshot, it actually returns 90k rows.

PEG Can Show DML Plan Graphs 
You can wrap DML commands with begin / rollback transaction commands. This way, you can focus on your DML command performance without persisting your changes. In the “before” and “after” fields, be sure to separate commands with a semicolon.






Actual Vs. Estimated Ratios Have Minimums 
If Actual Rows, Estimated Rows, Actual Mass, and Estimated Mass is low, PEG will show only thin lines. Currently, PEG will scale the line thickness under these conditions:

If Actual Rows + Estimated Rows > 10000 rows
If Actual Mass + Estimated Mass > 50k

The ratio will be either Actual:Estimated or Estimated:Actual, whichever is larger.

PEG Uses SQLite 
You’re welcome to download sqlite and look at the sqlite database that PostgreSQL Explain Plan creates. The database file will be stored in the same directory as the .JAR file.
