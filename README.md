# Customized waka-readme-stats

## Prep Work

1. Add a comment to your the markdown file you want to update (presumably `README.md`):

```md
<!--START_SECTION:waka-->
<!--END_SECTION:waka-->
```
2. Add your [Wakatime API key](https://wakatime.com/settings/api-key) as a secret and name it `WAKATIME_API_KEY`.
3. Add a [GitHub personal access token](https://github.com/settings/tokens) with `repo` and `user` scopes as a secret and name it `GH_TOKEN`.
4. Copy the sample workflow file to `.github/workflows/` in the desired repository.
```yml
name: Waka Readme

on:
  schedule:
    - cron: '15 */12 * * *'
  workflow_dispatch:
  
jobs:
  update-readme:
    name: Update Readme with Metrics
    runs-on: ubuntu-latest
    steps:
      - uses: miermontoto/waka-readme-stats@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          GH_TOKEN: ${{ secrets.GH_TOKEN }}
```

5. You can enable and disable feature flags based on requirements.

Your markdown file should now update at 00:15 and 12:15 UTC every day. You can change this by editing the crontab timing in the workflow file. Also, you can manually trigger an update in the 'Actions' tab.

## Customization
If you want to change what info is displayed, you can add multiple `FLAGS` in your workflow file. By default all flags are enabled.

```yml
- uses: miermontoto/waka-readme-stats@master
        with:
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
          GH_TOKEN: ${{ secrets.GH_TOKEN }}
          SHOW_OS: "False"
          SHOW_PROJECTS: "False"
```

### Flags Available

---

`LOCALE`  This flag can be used to show stats in your language. The default is english. Uses Locale [Short Hand](https://saimana.com/list-of-country-locale-code/) to be passed.

`COMMIT_BY_ME`        can be set to `True` to commit the code using your username and email.

`COMMIT_MESSAGE`        can be to set message commit, the default is "Updated with Dev Metrics".

`SHOW_UPDATED_DATE`        can be set to `True` to show updated date in end of paragraph.

`SHOW_LINES_OF_CODE`       can be set to `True` to show the lines of code writen till date.

![Lines of code](https://img.shields.io/badge/From%20Hello%20World%20I've%20written-1.3%20million%20Lines%20of%20code-blue)

`SHOW_PROFILE_VIEWS`       can be set to `False` to hide the profile views.

![Profile Views](http://img.shields.io/badge/Profile%20Views-2189-blue)


`SHOW_COMMIT`       can be set to `False` to hide the graph showing at what time of the day you commit.

**I'm an early 🐤** 
```text
🌞 Morning    95 commits     ███████░░░░░░░░░░░░░░░░░░   30.55% 
🌆 Daytime    78 commits     ██████░░░░░░░░░░░░░░░░░░░   25.08% 
🌃 Evening    112 commits    █████████░░░░░░░░░░░░░░░░   36.01% 
🌙 Night      26 commits     ██░░░░░░░░░░░░░░░░░░░░░░░   8.36%

```

`SHOW_DAYS_OF_WEEK`       can be set to `False` to hide the graph showing on what days of the week you commit.

📅 **I'm Most Productive on Sundays** 

```text
Monday       50 commits     ███░░░░░░░░░░░░░░░░░░░░░░   13.19% 
Tuesday      85 commits     █████░░░░░░░░░░░░░░░░░░░░   22.43% 
Wednesday    56 commits     ███░░░░░░░░░░░░░░░░░░░░░░   14.78% 
Thursday     44 commits     ███░░░░░░░░░░░░░░░░░░░░░░   11.61% 
Friday       28 commits     █░░░░░░░░░░░░░░░░░░░░░░░░   7.39% 
Saturday     30 commits     ██░░░░░░░░░░░░░░░░░░░░░░░   7.92% 
Sunday       86 commits     █████░░░░░░░░░░░░░░░░░░░░   22.69%

```

`SHOW_LANGUAGE`       can be set to `False` to hide the graph showing what languages your commits are in.

```text
💬 Languages:
JavaScript               5 hrs 26 mins       ███████████████░░░░░░░░░░   61.97%
PHP                      1 hr 35 mins        ████░░░░░░░░░░░░░░░░░░░░░   18.07%
Markdown                 1 hr 9 mins         ███░░░░░░░░░░░░░░░░░░░░░░   13.3%
Python                   22 mins             █░░░░░░░░░░░░░░░░░░░░░░░░   4.32%
XML                      8 mins              ░░░░░░░░░░░░░░░░░░░░░░░░░   1.62%
```


`SHOW_OS`       can be set to `False` to hide the graph showing the OS you commit from.

```text
💻 Operating systems:
Windows                  8 hrs 46 mins       █████████████████████████   100.0%
```

`SHOW_PROJECTS` can be set to `False` to hide the graph showing what repositories you commit to.

```text
📚 Repositories:
ctx_connector            4 hrs 3 mins        ███████████░░░░░░░░░░░░░░   46.33%
NetSuite-Connector       1 hr 31 mins        ████░░░░░░░░░░░░░░░░░░░░░   17.29%
mango-web-master         1 hr 12 mins        ███░░░░░░░░░░░░░░░░░░░░░░   13.77%
cable                    54 mins             ██░░░░░░░░░░░░░░░░░░░░░░░   10.41%
denAPI                   40 mins             ██░░░░░░░░░░░░░░░░░░░░░░░   7.66%
```

`SHOW_TIMEZONE` can be set to `False` to hide the time zone you commit from.

```text
⌚︎ Timezone: Asia/Calcutta
```

`SHOW_EDITORS`  can be set to `False` to hide the list of code-editors used.

```text
📝 Editors:
WebStorm                 6 hrs 47 mins       ███████████████████░░░░░░   77.43%
PhpStorm                 1 hr 35 mins        ████░░░░░░░░░░░░░░░░░░░░░   18.07%
PyCharm                  23 mins             █░░░░░░░░░░░░░░░░░░░░░░░░   4.49%
```

`SHOW_LANGUAGE_PER_REPO`  can be set to `False` to hide the number of repositories per language.

**I mostly code in Vue** 

```text
Vue          8 repos        ██████░░░░░░░░░░░░░░░░░░░   25.0% 
Java         6 repos        ████░░░░░░░░░░░░░░░░░░░░░   18.75% 
JavaScript   6 repos        ████░░░░░░░░░░░░░░░░░░░░░   18.75% 
PHP          3 repos        ██░░░░░░░░░░░░░░░░░░░░░░░   9.38% 
Python       2 repos        █░░░░░░░░░░░░░░░░░░░░░░░░   6.25% 
Dart         2 repos        █░░░░░░░░░░░░░░░░░░░░░░░░   6.25% 
CSS          2 repos        █░░░░░░░░░░░░░░░░░░░░░░░░   6.25%

```


`SHOW_SHORT_INFO`  can be set to `False` to hide a general summary of your github profile.

**The following section requires personal access token with user permission otherwise data shown will be incorrect.**

**🐱 My GitHub Data** 

> 🏆 433 Contributions in year 2020
 > 
> 📦 Used 292.3 kB in GitHub's Storage 
 > 
> 💼 Opted to Hire
 > 
> 📜 25 Public Repository 
 > 
> 🔑 15 Owned Private Repository 

`SHOW_LOC_CHART`  can be set to `False` to hide the chart showing the lines of code written in different quarters.

`IGNORED_REPOS`  can be set to any string, containing valid repositories names, to ignore some repos you don’t want to be counted

### This is a fork of anmol098's [waka-readme-stats](https://github.com/anmol098/waka-readme-stats).
