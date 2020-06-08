# HS2 Translation
English translation project for Honey Select 2

The translations are applied at runtime and do not require replacing or modifying any game files.

## Installation
1. Install at least [BepInEx 5 build #161](https://github.com/BepInEx/BepInEx), latest [BepisPlugins for HS2](https://github.com/bbepis/BepisPlugins/releases), latest [XUnity.AutoTranslator](https://github.com/bbepis/XUnity.AutoTranslator) and [HS2_TextResourceRedirector](https://github.com/IllusionMods/TranslationTools#textresourceredirector) (withouth this many of the translations won't be loaded into the game).
2. Go to the releases page above and download the latest release. Alternatively, advanced users can get the latest beta translations by clicking "Clone or download" button above. Read the ADV translations section below to see how to enable ADV translations if you do this.
3. Extract the zip and merge the Translation folder with the one in your BepInEx folder. It's recommended to delete your old translation folder to prevent translation collisions.
4. Optionally get [HS2_Subtitles](https://github.com/DeathWeasel1337/KK_Plugins#subtitles) to see subtitles, if any.

## Contribution
Any help is appreciated. Regardless of your translation skill and Japanese knowledge you can still help with translations. Even if you have no experience you can help by proofreading or using Google translate or other translation services and then cleaning up the translation using sanity and a bit of logic. Absolutely no raw machine translations will be accepted, users can use [XUnity.AutoTranslator](https://github.com/bbepis/XUnity.AutoTranslator/releases) for that.

Translations are all inside of `Bepinex\Translation\en\` folder. They are then split into three folders:
- `Text` - Normal text replacements and modifications.
- `Text\Localizations` - Strings under  this folder were dumped via TextDump. Translations can be added for missing entries, but new entries should not be added or merging future dumps will become difficult.
- `Texture` - Image replacements.
- `RedirectedResources` - Replacements for entire text assets. Preferred over `Text` for accuracy and performance.

Coordinate with other translators on the [Illusion Soft Discord server](https://discord.gg/illusionsoft) #translation channel. To avoid translation conflicts please ask if anyone is working on a file. If you have any questions about the quality of your translations, ask for advice on the server.

### How to add or improve translations
- If you want to make a simple edit simply open the file in question and click edit. After you are done editing, commit the changes and stall a pull request.
- If you have more translations to submit [fork the repository](https://help.github.com/articles/fork-a-repo/). Upload your changes to your fork and then [submit a pull request](https://help.github.com/articles/about-pull-requests/). Your pull request will be reviewed and accepted after a quality check. Again, no raw machine translations will be accepted. Proper capitalization, punctuation, and spelling is a must.

### ADV translations
Every translation.txt file has the raw Japanese text that needs translations. Each one starts commented out (`//` at the begining) so it will not be loaded. For your text to display correctly in game, put the translation on the right side of the equal sign and remove the `//` at the start of the line. Do not edit the Japanese text or the translation will not work.

The `assets` folder inside of `Bepinex\Translation\en\RedirectedResources` can be compressed into a .zip archive to be read by the game (simply right-click on the assets folder and then compress to .zip). Uncompressed files under assets are also still loaded. The game has to be restarted in order to see updated translations.


[TextResourceRedirector](https://github.com/DeathWeasel1337/KK_Plugins#textresourceredirector) **v1.3 (or greater)** is required for these translations.


### Specialized ADV translation lines

There are some specialized resources handled by the resource redirection that require some addititional handling.

#### Format strings

Format strings have replacements in them processed by [`String.Format`](https://docs.microsoft.com/en-us/dotnet/api/system.string.format?view=netframework-4.6#Starting).  The sections that are replaced by the game engine will look like `{0}`, `{1}`, `{2}`, etc.  Usually they are a character name or the name of some item.  The same replacements found in the original string should exist in the translated string.

Example:
```
{0}‚Æ’‡‚ª‚¢‚¢‚ÆŽv‚Á‚Ä‚é‚í=I think I'm good friends with {0}.
```

#### Choices

Because these strings are encoded into a larger entry in the resource files they require special handling by TextResourceRedirector to ensure the text that should no be replaced remains untouched, while allowing the displayed text to be translated. These lines will start with `CHOICE:` followed by the text that needs to be translated.  On the right side of the `=` you need only include the translated text without the `CHOICE:` prefix. 

Example:
```
CHOICE:Žó‚¯Žæ‚é=Accept
```

### Tools
[Yomichan](https://foosoft.net/projects/yomichan/)  
This browser plugin allows you to see the definition of Japanese words by putting your mouse over them in the browser and pressing shift.  

Dictionaries:  
https://jisho.org/  
http://www.romajidesu.com/  

### ADV folders and personalities

