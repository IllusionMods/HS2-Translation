# HS2 Translation

English fan translation project for Honey Select 2. The translations are applied at runtime and do not require replacing or modifying any game files.

## Prerequisites

- [BepInEx 5.1](https://github.com/BepInEx/BepInEx)
- [BepisPlugins for HS2](https://github.com/bbepis/BepisPlugins/releases)
- [XUnity.AutoTranslator](https://github.com/bbepis/XUnity.AutoTranslator)
- [HS2_TextResourceRedirector](https://github.com/IllusionMods/TranslationTools#textresourceredirector) (required for most resources)
- [HS2_Subtitles](https://github.com/DeathWeasel1337/KK_Plugins#subtitles) (required to see subtitles)
- [HS2_TranslationCacheCleaner](https://github.com/GeBo1/GeBoPlugins#translationcachecleaner) (optional, but recommended)

## Installation

1. Ensure you have the prerequisites installed.
2. Go to the releases page above and download the latest release. Alternatively, advanced users can get the latest beta translations by clicking "Clone or download" button above. Read the ADV translations section below to see how to enable ADV translations if you do this.
3. Extract the zip and merge the Translation folder with the one in your BepInEx folder. It's recommended to delete your old translation folder to prevent translation collisions. If you do not be sure to run TranslationCacheCleaner.
4. Install the latest [AutoTranslatorConfig.ini](blob/master/config/AutoTranslatorConfig.ini) (or compare it to your existing one and be sure that the entries under the following sections match up: `Files`, `TextFrameworks`, `Behaviour`, `Texture`, `ResourceRedirector`)

## Contribution

Any help is appreciated. Regardless of your translation skill and Japanese knowledge you can still help with translations. Even if you have no experience you can help by proofreading or using Google translate or other translation services and then cleaning up the translation using sanity and a bit of logic. Absolutely no raw machine translations will be accepted, users can use [XUnity.AutoTranslator](https://github.com/bbepis/XUnity.AutoTranslator/releases) for that.

Translations are all inside of `Bepinex\Translation\en\` folder. They are then split into the following folders:
- `RedirectedResources` - Replacements for strings embedded in asset files. Preferred over `Text` for accuracy and performance.
- `Text` - Normal text replacements and modifications.
- `Text\Localizations` - Strings under  this folder were dumped via TextDump. Translations can be added for missing entries, but new entries should not be added or merging future dumps will become difficult.
- `Texture` - Image replacements.

Coordinate with other translators on the [Illusion Soft Discord server](https://discord.gg/illusionsoft) #translation channel. To avoid translation conflicts please ask if anyone is working on a file. If you have any questions about the quality of your translations, ask for advice on the server.

### How to add or improve translations

- If you want to make a simple edit simply open the file in question and click edit. After you are done editing, commit the changes and stall a pull request.
- If you have more translations to submit [fork the repository](https://help.github.com/articles/fork-a-repo/). Upload your changes to your fork and then [submit a pull request](https://help.github.com/articles/about-pull-requests/). Your pull request will be reviewed and accepted after a quality check. Again, no raw machine translations will be accepted. Proper capitalization, punctuation, and spelling is a must.

## Text Translations

### Known Scope Levels

| Level | Description       |
|------:|-------------------|
| -1    | (global)          |
| 0     | Dialogs           |
| 2     | Main Menu         |
| 4     | "Home" scene      |
| 6     | ADV dialog scenes |
| 7     | H scenes          |
| 8     | Lobby             |
| 9     | Fur's Room        |
| 14    | Character Search  | 

## Resource Translations

- `adv` - main game dialogs
- `etcetra/list/config` - Personalities
- `etcetra/list/parametername` - Traits, H Traits, State
- `gamedata/achievement/achivement` - achievements
- `gamedata/achievement/exchange` - unlockables/powerups,
- `gamedata/bgmname` - BGM titles
- `gamedata/eventcontent` - current activity/urge
- `map/list/mapinfo` - map names
- `list/characustom` - maker stuff
- `list/h/animationinfo` - positions (game versions)
- `list/h/sound` - h-subs are
- `studio` - studio stuff

### ADV translations

Every translation.txt file has the raw Japanese text that needs translations. Each one starts commented out (`//` at the begining) so it will not be loaded. For your text to display correctly in game, put the translation on the right side of the equal sign and remove the `//` at the start of the line. Do not edit the Japanese text or the translation will not work.

The `assets` folder inside of `Bepinex\Translation\en\RedirectedResources` can be compressed into a .zip archive to be read by the game (simply right-click on the assets folder and then compress to .zip). Uncompressed files under assets are also still loaded. The game has to be restarted in order to see updated translations.


[TextResourceRedirector](https://github.com/IllusionMods/TranslationTools#textresourceredirector) is required for these translations.

### Specialized translation lines

There are some specialized resources handled by the resource redirection that require some addititional handling.

#### Format strings

Format strings have replacements in them processed by [`String.Format`](https://docs.microsoft.com/en-us/dotnet/api/system.string.format?view=netframework-4.6#Starting).  The sections that are replaced by the game engine will look like `{0}`, `{1}`, `{2}`, etc.  Usually they are a character name or the name of some item.  The same replacements found in the original string should exist in the translated string.

Example:
```
{0}と仲がいいと思ってるわ=I think I'm good friends with {0}.
```

#### ADV Choices

Because these strings are encoded into a larger entry in the resource files they require special handling by TextResourceRedirector to ensure the text that should no be replaced remains untouched, while allowing the displayed text to be translated. These lines will start with `CHOICE:` followed by the text that needs to be translated.  On the right side of the `=` you need only include the translated text without the `CHOICE:` prefix. 

Example:
```
CHOICE:受け取る=Accept
```

#### Optional Prefixes

There are a number of assets that support the use of optional prefixing to get a more exact match. This allows for more specific translations in cases where multiple assets might match the same replacement code.  Matching for these assets will first try the prefixed match, then fall back to the standard un-prefixed match.  Given the following translation file:

```
PREFIX1:こんにちは=Hi!
こんにちは=Hello.
```

Trying to match `こんにちは` for an asset using `PREFIX1` would return `Hi!`, where an asset using `PREFIX2` would fall back to `Hello.`.

| asset location               | prefix        | Notes                                                                               |
|------------------------------|---------------|-------------------------------------------------------------------------------------|
| `etcetra/list/parametername` | `HATTRIBUTE:` |                                                                                     |
| `etcetra/list/parametername` | `MIND:`       |                                                                                     |
| `etcetra/list/parametername` | `STATE:`      |                                                                                     |
| `etcetra/list/parametername` | `TRAIT:`      |                                                                                     |


#### Personalities

| ID | Name   | Eng Name     | Dialog (`adv/scenario/`) | Subtitles (`list/h/sound/voice/*/`) |
|----|--------|--------------|--------------------------|-------------------------------------|
| 0  | クール  | Quiet        | `c00`                    | `hvoicestart_c00_*`, `hvoice_c00*`  |
| 1  | 普通   | Normal       | `c01`                    | `hvoicestart_c01_*`, `hvoice_c01_*`  |
| 2  | 苦労人 | Hardworking  | `c02`                    | `hvoicestart_c02_*`, `hvoice_c02_*`  |
| 3  | 女友達 | Girlfriend   | `c03`                    | `hvoicestart_c03_*`, `hvoice_c03_*`  |
| 4  | ギャル  | Fashionable  | `c04`                    | `hvoicestart_c04_*`, `hvoice_c04_*`  |
| 5  | 気弱   | Timid        | `c05`                    | `hvoicestart_c05_*`, `hvoice_c05_*`  |
| 6  | 母性的 | Motherly     | `c06`                    | `hvoicestart_c06_*`, `hvoice_c06_*`  |
| 7  | ドS    | Sadistic     | `c07`                    | `hvoicestart_c07_*`, `hvoice_c07_*`  |
| 8  | オープン | Open-hearted | `c08`                   | `hvoicestart_c08_*`, `hvoice_c08_*`  |
| 9  | 天然   | Natural      | `c09`                    | `hvoicestart_c09_*`, `hvoice_c09_*`  |
| -1 | フュル  | Fur          | `c-1`                    |                                      |

### Tools

- [Release Tool](https://github.com/IllusionMods/KoikatsuStoryTranslation/tree/master/tools/ReleaseTool) - Tool that cleans up the translation files to remove any unnecessary untranslated parts.
- [Yomichan](https://foosoft.net/projects/yomichan/) - This browser plugin allows you to see the definition of Japanese words by putting your mouse over them in the browser and pressing shift.
- Dictionaries:  
  - https://jisho.org/  
  - http://www.romajidesu.com/  






