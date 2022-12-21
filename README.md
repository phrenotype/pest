# PEST

This is a fire and forget way to keep a webmaster confused.

This is for **educational purposes** only. I bear no responsibility for what you use this for.


# How it works

A webmaster might get a message on the web root in an `index.php` file. No matter what he/she does, They cannot get rid of that file. It comes back after being deleted and no other file can be uploaded. It gets deleted immediately.

# Usage

There are two files. The first one `.pest` should be used if cronjob access is not there. The second `.pest_cron` is used as a cron job. The latter is discouraged as it raises attention and is quick to spot.


For the `.pest` file the following:

- Establish file upload access or vulnerability.
- Open the file and edit the `WEBROOT` variable to what the target's webroot is.
- Edit the `RANSOME_MESSAGE` to whatever you want your message to be.
- Rename the file to something benign but keep it as a dot file.
- Upload the file to a folder outside the webroot and feel free to add useless bash code and comments to make it look legitmate.
- Once on the target server, make it executable by running `chmod +x .whatever_you_renamed_it_to`
- Finally, run `nohup bash .whatever_name_you_gave_it & disown`.
- It will keep clearing all the contents of the webroot and writing your message to `index.php`.

Note that if the server if restarted, this will cease to work and you will have to run the script again.


For the `.pest_cron`, if it's on a shared hosting, you'll need to take over the cpanel (A tutorial for another day) and add it as a cron job. If it's a root user, use crontab.

