Backup-Wordpress
================

Scripts to backup WordPress via server cron (cPanel, Plesk, etc)
----------------------------------------------------------------

There are plenty of plugins available to take backups within WordPress. However, the scripts mentioned here work outside WordPress making them much more effective and efficient!

## Features

- No plugin to install. So, no plugin conflicts!
- Single script to take backups of multiple sites.
- Separate script to take (nightly) files backup without uploads directory!
- Local and offline backups are supported.
- Automatic deletion of local backups.
- Support for sub-directory installation of WordPress!

## Roadmap

- Ability to choose the compression method.
- take only local backups or only remote backups or both.
- ability to remove local backups when taking only remote backups.
- single script to take all sorts of backups.
- close integration with wp-cli (probably as a plugin).
- alert when local storage reaches a limit.

## Requirements in the server

- wp-cli
- aws-cli and/or gsutil (to take offline backups)
- SSH access
- mysqldump
- zip, tar, or bzip
- enough disk space to hold local backups

## What does each backup script do?

- [db-backup.sh](https://github.com/pothi/backup-wordpress/blob/master/db-backup.sh) can take database backup with --add-drop-table option.
- [files-no-uploads-backup.sh](https://github.com/pothi/backup-wordpress/blob/master/files-no-uploads-backup.sh) can take files backups without uploads folder to reduce the overall size of the backup. Ideal for nightly backups!
- [full-backup.sh](https://github.com/pothi/backup-wordpress/blob/master/full-backup.sh) can take full backup including database (that is named db.sql and is available at the WordPress core directory). Ideal for a weekly routine!

## Where are the backups stored?

- local backups are stored in the directory named `~/backups/`. If it doesn't exist, the script/s would attempt to create it before execution.
- offline backups can be stored in AWS (for now). Support for other storage engines (especially for GCP) is coming soon!

## How to take backups?

- firstly, go through each script and fill-in the variables to fit your particular environment. Currently, it is assumed that the WordPress core is available at `~/sites/example.com/public`.
- most importantly, adjust the number of days to keep the backup, depending on the remaining hard disk space in your server!
- test the scripts using SSH before implementing it in system cron.
- note: you may take backups of multiple domains like the following...

```
/path/to/db-backup.sh example1.com
/path/to/db-backup.sh example2.com
/path/to/db-backup.sh example3.com
```

The above is applicable to all the scripts!

### Can you implement it on my server?

Yes, of course. But, for a small fee of USD 5 per server per site. [Reach out to me now!](https://www.tinywp.in/contact/).

### I have a unique situation. Can you customize it to suit my particular environment?

Possibly, yes. My hourly rate is USD 50 per hour, though.

### Have questions or just wanted to say hi?

Please ping me on [Twitter](https://twitter.com/pothi]) or [send me a message](https://www.tinywp.in/contact/).

Suggestions, bug reports, issues, forks are always welcome!
