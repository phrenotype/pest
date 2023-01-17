# PEST

This is for **educational purposes** only. I bear no responsibility for what you use this for. For this reason, no specific tutorial will be given for how exactly when or where to use this tool.

This is a fire and forget way to keep a webmaster confused.

Using the build tool, you can generate three different types of bash files that will perform differently.

- Wiper : Will consistently wipe the webroot and replace the index.php/index.html with a custom message

- Cron Wiper : Same as the wiper, but will be used as a cron job

# How it works

A webmaster might get a message on the web root in an `index.php` file. No matter what he/she does, They cannot get rid of that file. It comes back after being deleted and no other file can be uploaded. Any uploaded file gets deleted immediately.

# Usage

To build the final product you need the following

- The webroot path
- A custom message (A ransom message maybe)
- Sleep time in seconds (This will be ignored for cron wiper). This servers as a delay between each run.


To build a wiper, run:

```bash
bash build wiper /home/user/public_html "Hacked" 60
```

A file named ".wiper" will be created.


To build a cron wiper, run:

```bash
bash build cronwiper /home/user/public_html "Hacked" 60
```

A file named ".cron_wiper" will be created.

## Obfuscation
It is important you obfuscate these files by changing the file names, making them dot files and adding useless comments at the top of the file to distract during manual audit.

Also note that the cron wiper is discouraged as it raises attention and is quick to spot.

## Using the generated files
To run the wiper

```bash
nohup bash .wiper & disown
```

To run the .cron_wiper, add it the the list of cron jobs.


If you find this page cryptic, or you have no idea what's going on, maybe you should not be here at all. Go build a cute website or an app.




Stay Dangerous :)
