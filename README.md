# Girls' Frontline Discord Search
[Click to invite to your server](https://discordapp.com/oauth2/authorize?client_id=351447700064960522&scope=bot&permissions=26688)

If you invite the above bot, the prefix is $gf! Use $gfhelp to get started.

Reason for permissions:
- Send Messages: It's obvious.
- Embed Links: search results are rich embeds. If you turn this off, you can use $gfsearch2 for text based information.
- Add Reactions: The bot adds 'buttons' to its own messages to switch between results. If you turn this off... You can react to the message yourself, I guess.
- Manage Messages: Wipe other people's reactions from the bot's own messages. If you turn this off, you can unclick a reaction and click again to switch between results.

### Feature Overview:

- Type, Base Stats, Max Stats, How To Obtain, Production Requirement, Ability, Ability Cooldown, Tile Bonus, Tile Bonus information.
- placebo recipies and estimated drop rates for rare dolls.
- Links to the corresponding doll page on https://en.gfwiki.com
- Flavor text, or adjudant quotes if there is no flavor text.
- Images for almost every doll... Assuming you ripped the images from the game files. Costumes too!
- Fire react on a doll's image to show their damage art.
- Aliases. Ex. HKM4 -> HK416
- Experience calculation from lv1 to lv120. Also shows number of combat reports required.
- Fuzzy search that will return the closest result and suggest other results. Has fuzzy results for search, equipment, costumes.
- Shorthand commands

Coming eventually:
- $gffilter for finding the best doll in a type.
- $gfsearch flags for only showing the relevant part of an embed.

## Commands and what they do
This information is copypasted from $gfhelp. Please refer to that for the most up to date help.
Assuming that that the default prefix $gf is still being used:
### $gfsearch: Search T-Dolls
Search a T-Doll. Returns various information about the doll if it finds it. Returns the closest result if it doesn't find an exact match.

This command supports MOD 3 dolls (among other little easter eggs).
### $gfequip: Search equipment and fairies
Search for equipment or fairies. If you search a doll's name, it will return the exclusive equipment for that doll.

### $gfimage: Display the images and costumes of a T-Doll
Supports listing all the costumes of a T-Doll with --list or -l.

### $gftimer: Check which dolls or equipment correspond to which production timer.
### $gfhelp: List commands, version, how to contact me, etc.
### $gfquote: Show quotes from the dolls if you have CharacterVoice.json from the game files
### $gfstatus: Number of servers this bot is in.
### $gfexp: Calculate experience required to level up.

You can get more up to date command information by asking the discord bot or opening main.py and scrolling down to the help command. This is just a short summary.

## Prerequesites
Python3 and pip. Game files need to be extracted if you want images and quotes.

To extract files: https://github.com/36base/girlsfrontline-resources-extract

This will help (replace adb pull with the region you play in and $PWD with the folder of extractor):
```bash
#!/bin/bash
#adb pull /sdcard/Android/data/kr.txwy.and.snqx/files/Android/New/ $PWD
#skin.json is in asset_textes

rm log.txt
a=(New/*)
# get length of an array
arraylength=${#a[@]}

for (( i=1; i<${arraylength}+1; i++ ));
do
  echo $i " / " ${arraylength}
  python3 main.py -o out target ${a[$i-1]}
done

find out/wav/ -name '*.wav' -execdir oggenc {} \; -execdir rm {} \;
```

## Setup
1. `git clone https://github.com/RhythmLunatic/Girls-Frontline-Discord-Search.git`
2. Set the GFBOT_TOKEN environment variable in your terminal with the token for the bot
3. Open main.py, change COMMAND_PREFIX to whatever you want, the default is $gf
4. If you have your own http server containing the dumped girls frontline images change PIC_DOMAIN, otherwise you can keep using mine. (Please only use my CDN for unmodified versions of the bot. Bandwidth isn't free.)
5. `pip3 install -r requirements.txt` (Windows users, the command might be 'pip' instead of pip3)
6. `chmod +x run_forever.sh` (Windows users, you're on your own)
7. `./run_forever.sh` if linux, otherwise `python3 main.py`.

## Screenshot
![GFSearch Command](https://i.imgur.com/QAkHNF5.png)

## Legal stuff
main.py is AGPLv3, read LICENCE for more information. If you run a public modified version of this bot, you MUST release the source code.

THIS PROGRAM IS NOT ENDORSED BY https://en.gfwiki.com. ALL DATA CONTAINED WITHIN girlsfrontline.json IS Ⓒ https://en.gfwiki.com AND LICENCED UNDER CC BY-SA 3.0. For more information, please read gf_json_LICENCE.

## Usage information
You could probably tell by reading the source code, but nothing is logged except for commands that start with $gf. No, your username is not recorded. Neither is your user ID.

## Plz donate
I'm a broke college student who needs to pay for my college loans: https://www.ko-fi.com/rhythmlunatic
