# Recover Data From Dedicated on Argon
If you have recently deleted any files in the `/Dedicated/schnieders/` directory. They are easy to recover from snapshots.

## Step-by-step guide
1. To find where these snapshots are stored: `cd /Dedicated/schnieders/.zfs/snapshot/`
2. Listing the contents will show each snapshot labeled by their date on which they were taken: `ls -ltr`
   ![image](https://github.com/SchniedersLab/lab-info/assets/109233531/148dc948-67f9-49fc-9f2d-b27b51d5a1f4)
3. Changing directory into one of these snapshots will reveal `/Dedicated/schnieders` as it was at that specific time.
4. Copy the data from the appropriate location in that snapshot and you are done.
