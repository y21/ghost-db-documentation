# ghost-db-documentation
An unofficial markdown documentation for Chadsoft's ghost leaderboard API.

## About
Unfortunately, the <a href="http://chadsoft.co.uk/time-trials/">CTGP-R Ghost Database API</a> is undocumented, and no one has made a documentation for it yet, so I decided it would be helpful for developers in the Mario Kart Wii community to write one, so that people can use the API in their application without any problems.

## Issues
If you have questions about CTGP-R or Mario Kart Wii in general, you should not open an issue. You might want to consider contacting <a href="https://www.youtube.com/user/MrBean35000vr">MrBean</a> or Chadderz (founders of CTGP-R) if your problem/question is related to CTGP. You should **only** open issues about the documentation and the API itself.

## Contributing and Pull Requests
In case you found a typo or another mistake, feel free to submit a pull request. I will merge pull requests if they meet the following rules:
- Accurate description/title: try to describe changes as clear as possible
- Name all commits: all commit summaries should be clear enough for others to understand what has changed

---
## Return Format
The API returns data as JSON which is already part of the web standard and almost every language can parse and work with it. 

## Endpoints
Every route in the subdirectory `time-trials` of <a href="http://chadsoft.co.uk/">chadsoft.co.uk</a> can be reached through the <a href="http://tt.chadsoft.co.uk/index.json">API</a> using its route (`/directory/file.json`), so for example http://chadsoft.co.uk/time-trials/ becomes http://tt.chadsoft.co.uk/index.json.