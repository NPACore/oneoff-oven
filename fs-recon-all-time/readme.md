# Freesurfer recon-all duration
## Question
* How long until all sessions are processed?
  * How long does it take to run one session through freesurfer (7.4.1, single core on rhea). Logs will say!
  * Running 40 at a time for 157 sessions

## Extra context

Freesurf's recon-all writes to `$SUBJECT_DIR/$subject/scripts/recon-all.log`.

Start time is always on second line of log file. End time (when finished) is on last line. This looks like

```
cat -n sub-11014_ses-1_recon-all.log
```
>          1  
>          2  Wed Jun 18 16:24:13 EDT 2025
>          ⁞ 
>      15149  recon-all -s sub-11014_ses-1 finished without error at Thu Jun 19 04:22:00 EDT 2025

### Date Notes
 * For python `datetime.datetime.strptime(datestr, format)`, format would be `"%a %b %d %H:%M:%S %Z %Y"`. 
 * `/bin/date` can read the date without specifying format. `date -d "Thu Jun 19 04:22:00 EDT 2025" +%s` yields seconds since epoch of input date (`1750321320`). Useful for date math.
