# ghost-db-documentation
An unofficial markdown documentation for Chadsoft's ghost leaderboard API.

## Table of Contents
| Section | Reading time|
|---------|-------------|
| Introduction parts |
| <a href="#about">About</a>  | 1 minute |
| <a href="#issues">Issues</a> | 1 minute |
| <a href="#contributing-and-pull-requests">Contributing and Pull Requests</a>| 2 minutes
| Documentation |
| <a href="#return-format">Return Format | 1 minute
| <a href="#endpoints">Endpoints</a> | 3 minutes |
| `global` properties |
| <a href="#global_links">global._links</a> | 3 minutes
| <a href="#global_uniquePlayers">global.uniquePlayers</a> | 1 minute
| <a href="#global_leaderboardCount">global.leaderboardCount</a> | 1 minute
| <a href="#global_ghostCount">global.ghostCount</a> | 1 minute
| <a href="#global_recentRecords">global.recentRecords</a> | 7 minutes


## About
Unfortunately, the <a href="http://chadsoft.co.uk/time-trials/">CTGP-R Ghost Database API</a> is undocumented, and no one has made a documentation for it yet, so I decided it would be helpful for developers in the Mario Kart Wii community to write one, so that people can use the API in their application without any problems. <br/>
**Note:** `global` is meant to be the main object of returned data, example:
<img src="https://i.imgur.com/kvsOhxE.png" />

## Issues
If you have questions about CTGP-R or Mario Kart Wii in general, you should not open an issue. You might want to consider contacting <a href="https://www.youtube.com/user/MrBean35000vr">MrBean</a> or Chadderz (founders of CTGP-R) if your problem/question is related to CTGP. You should **only** open issues about the documentation and the API itself.

## Contributing and Pull Requests
In case you found a typo or another mistake, feel free to submit a pull request. I will merge pull requests if they meet the following rules:
- Accurate description/title: try to describe changes as clear as possible
- Name all commits: all commit summaries should be clear enough for others to understand what has changed

---
## Return Format
The API returns data as JSON which is already part of the web standard and almost every language can parse and work with it. <br />
**Warning**: The first character of returned data is a BOM (Byte order mark). If your language/library does not exclude it automatically when parsing, __you__ should do it.

## Endpoints
Every route in the subdirectory `time-trials` of <a href="http://chadsoft.co.uk/">chadsoft.co.uk</a> can be accessed through the <a href="http://tt.chadsoft.co.uk/index.json">API</a> using its route (`/directory/file.json`), so for example `http://chadsoft.co.uk/time-trials/` becomes `http://tt.chadsoft.co.uk/index.json`. <br/>
**Note**: Keep in mind that you have to change the file extension `.html` to `.json`
>The data will not be "pretty-printed" (linebreaks, spaces and easy-to-read code in general), so if you want to try out an endpoint, you might want to download an extension that formats JSON for you. <br />
>I recommend <a href="https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa?hl=en">JSON Formatter</a> for Google Chrome or <a href="https://addons.mozilla.org/en-US/firefox/addon/jsonview/">JSONView</a> for Firefox.
---
## global._links
**Type:** object&lt;object&gt; <br/>
**Available in:** any<br/>
**Static length:** no<br/>
**Description:** The `_links` is an object with all links that are shown (file extension is `.json`) in `div._1c1 side-navigation` (link box): <br/>
<img src="https://i.imgur.com/Yjb8WOT.png" /> <br/>
`_links.self` is the **current** page, so if you're requesting `/index.json` it should say `/index.json`.

## global.uniquePlayers
**Type:** integer <br />
**Available in:** `/index.json` <br/>
**Static length:** no<br/>
**Description:** The amount of racers who have submitted at least one ghost to the database.

## global.leaderboardCount
**Type:** integer <br />
**Available in:** `/index.json` <br />
**Static length:** no<br/>
**Description:** The amount of existing leaderboards (every track has its own leaderboard, including custom tracks that are not in CTGP-R)

## global.ghostCount
**Type:** integer <br />
**Available in:** `/index.json` <br/>
**Static length:** no<br/>
**Description:** The amount of ghosts that exist in the database in **all** categories and on **all** leaderboards.

## global.recentRecords
**Type:** array&lt;object&lt;object&gt;&gt; <br/>
**Available in:** `/index.json` <br/>
**Static length:** 10 <br/>
**Description:** An array of ghosts (typeof object) with several properties that represent information about the ghost: <br />

| Property | Description |
|----------|-------------|
| _links   | An object with links that refers to the `item` (ghost), `player` and `leaderboard`. |
| href | The link to the ghost, equivalent to `_links.item` |
| country | <a href="https://wiibrew.org/wiki/Country_Codes">Country code</a> of where the ghost was created (`undefined` if user has location disabled)
| region | Region code (`undefined` if user has location disabled)
| continent | Continent code (`undefined` if user has location disabled)
| player | The name of racers' mii |
| trackId | The track ID |
| trackName | The name of the track |
| trackVersion | The version of the track |
| defaultTrack | Whether the track is a nintendo track (`true`) or a custom track (`false`) |
| finishTime | The exact time when the ghost finished the time trial. (Format: `mm:ss:msmsmsmsmsmsmsmsmsmsmsms`, m = minute, s = second, ms = millisecond) |
| finishTimeSimple | Same as `finishTime` but kept simple, this will be displayed in the CTGP-R channel, ceiled to 3 digits. (Format: `mm:ss:msmsms`) |
| bestSplit | Time of best round of ghost (Format: see `finishTime`) |
| bestSplitSimple | Same as `bestSplit` but kept simple (Format/ceiling: see `finishTimeSimple`) |
| hash | The SHA1 hash of ghost |
| vehicleId | The vehicle id |
| driverId | The driver id |
| dataSet | The ISO 8601 timestamp of when the ghost was created |
| isTie | Whether it's a tie or not |
| controller | [The controller code](https://github.com/y21/wiiset-bot/blob/master/controllerCodes.json)
