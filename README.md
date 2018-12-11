Encode Sans Fonts
=================

![](sample.png)

Forked from Pablo Impallari's original repo, in order to upgrade the family to a variable font, as well as to add in some small refinements.The description from the original is:

> The Encode Sans family is a versatile workhorse. Featuring a huge range of weights and > widths, it's ready for all kind of typographic challenges. It also includes Tabular and > Old Style figres, as well as full set of Small Caps and other Open Type features.
> 
> Designed by Pablo Impallari and Andres Torresi.
> 
> Released under the SIL Open Font License.
> 
> #### Encode Sans covers all 104 Latin Languages:
> 
> Afar, Afrikaans, Albanian, Azerbaijani, Basque, Belarusian, Bislama, Bosnian, Breton, > Catalan, Chamorro, Chichewa, Comorian, Croatian, Czech, Danish, Dutch, English, Esperanto, > Estonian, Faroese, Fijian, Filipino/Tagalog, Finnish, Flemish, French, Gaelic (Irish / > Manx / Scottish), Gagauz, German, Gikuyu, Gilbertese/Kiribati, Greenlandic, Guarani, > Haitian_Creole, Hawaiian, Hungarian, Icelandic, Igo/Igbo, Indonesian, Irish, Italian, > Javanese, Kashubian, Kinyarwanda, Kirundi, Latin, Latvian, Lithuanian, Luba/Ciluba/Kasai, > Luxembourgish, Malagasy, Malay, Maltese, Maori, Marquesan, Marshallese, > Moldovan/Moldovian/Romanian, Montenegrin, Nauruan, Ndebele, Norwegian, Oromo, > Palauan/Belauan, Polish, Portuguese, Quechua, Romanian, Romansh, Sami, Samoan, Sango, > Serbian, Sesotho, Setswana/Sitswana/Tswana, Seychellois_Creole, SiSwati/Swati/Swazi, > Silesian, Slovak, Slovenian, Somali, Sorbian, Sotho, Spanish, Swahili, Swedish, Tahitian, > Tetum, Tok_Pisin, Tongan, Tsonga, Tswana, Tuareg/Berber, Turkish, Turkmen, Tuvaluan, > Uzbek/Usbek, Wallisian, Walloon, Welsh, Xhosa, Yoruba, Zulu.
 
# Build Process

The sources can be built with FontMake, but I've put together some build scripts to pass the fonts through some steps that fix metadata issues.

## Step 1: Install Requirements

To operate the scripts within this repo, install requirements with:

```
pip install -r sources/scripts/requirements.txt
```

(Caveat: this installs all Python 3 dependencies I've installed for Google Fonts work. I know this is messy – next time, I'll set up a virtual environment for each project. I hope to circle back in the future and make this requirements file cleaner.)

## Step 2: Give permissions to build scripts

The first time you run the build, you will need to give run permissions to the build scripts.

On the command line, navigate to the project folder (`cd Encode-Sans`), and then give permissions to the shell scripts with:

```
chmod -R +x sources/scripts
```

The `-R` applies your permission to each of the shell scripts in the directory, and the `+x` adds execute permissions. Before you do this for shell scripts, you should probably take a look through their contents, to be sure they aren't doing anything bad. The ones in this repo simply build from the Encode Sans GlyphsApp sources.

## Step 3: Run the build scripts!

You can then build sources by running shell scripts in `sources/scripts/`.

```
sources/scripts/build.sh [OPTIONS]
```

Add one of the are the following flags to build the fonts:

`--statics` or `-s` to build the static TTF instances (there are 45, so it takes awhile)

`--linked` or `-l` to build the split variable fonts (split into 5 width families, each with a variable weight axis)

`--full` or `-f` to build the one full variable font, with weight & width axes

`--all` or `-a` to build all of the fonts and take a coffee break.

(Thanks to [@mjlagattuta](https://github.com/mjlagattuta)) for coming up with the way to add flags, and to [@jonalmeida](https://github.com/jonalmeida) for writing [such a good blog post about it](https://jonalmeida.com/posts/2013/05/26/different-ways-to-implement-flags-in-bash/)).



# Variable font upgrade project documentation

Notes were taken throughout the variable font upgrade project and added to the [docs](/docs) directory. I tend to take notes while working anyway, in order to think through problems and record solutions for later reference. In this project, I have included these in the repo so that others might find references to solve similar problems, especially because variable font-making processes are relatively new, and there is a general scarcity of online knowledge on font mastering. Because they were often made alongside work, the notes can at times be a bit disjointed. Hopefully they are still helpful to others! 

If you have any questions about the project or the notes, feel free to [file an issue](/issues) or to reach out to Stephen Nixon via Twitter ([@thundernixon](https://twitter.com/thundernixon)) or other social media (typically also @thundernixon).

# Further work-in-progress in `wip` branch

There are a few details currently still being cleared up and improved. While this is happening, this work will take place in the `wip` branch, and the latest font outputs will be moved into the `master` branch as they are created.