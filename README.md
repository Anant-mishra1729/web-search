# web-search plugin
**This is a standalone plugin for zsh with no need of installing Oh-my-zsh**

The code of plugin belongs to ohmyzsh, I have copied the code from the functions.zsh and web-search.plugin.zsh to make this plugin work without any need of installing Oh-my-zsh!

Open your `~/.zshrc` file and add this line `source < Path where web-search.plugin.zsh file is located >`

For example
```zsh
source ~/.config/zsh/web-search/web-search.plugin.zsh
```

## Troubleshooting
If you're getting this error
```
iconv: failed to start conversion processing
Error converting string from  to UTF-8
```
Try these solutions 
* Replace this line `local encoding=$langinfo[CODESET]` with `local encoding=$(locale charmap)`
* Replace this line `str=$(echo -E "$str" | iconv -f $encoding -t UTF-8)` with `str=$(echo -E "$str" | iconv -f US-ASCII -t UTF-8)
* Raise an isssue with the error.


## Usage
This plugin adds aliases for searching with Google, Wiki, Bing, YouTube and other popular services.


You can use the `web-search` plugin in these two forms:

* `web_search <context> <term> [more terms if you want]`
* `<context> <term> [more terms if you want]`

For example, these two are equivalent:

```zsh
$ web_search google oh-my-zsh
$ google oh-my-zsh
```

Available search contexts are:

| Context               | URL                                      |
| --------------------- | ---------------------------------------- |
| `bing`                | `https://www.bing.com/search?q=`         |
| `google`              | `https://www.google.com/search?q=`       |
| `brs` or `brave`      | `https://search.brave.com/search?q=`     |
| `yahoo`               | `https://search.yahoo.com/search?p=`     |
| `ddg` or `duckduckgo` | `https://www.duckduckgo.com/?q=`         |
| `sp` or `startpage`   | `https://www.startpage.com/do/search?q=` |
| `yandex`              | `https://yandex.ru/yandsearch?text=`     |
| `github`              | `https://github.com/search?q=`           |
| `baidu`               | `https://www.baidu.com/s?wd=`            |
| `ecosia`              | `https://www.ecosia.org/search?q=`       |
| `goodreads`           | `https://www.goodreads.com/search?q=`    |
| `qwant`               | `https://www.qwant.com/?q=`              |
| `givero`              | `https://www.givero.com/search?q=`       |
| `stackoverflow`       | `https://stackoverflow.com/search?q=`    |
| `wolframalpha`        | `https://wolframalpha.com/input?i=`      |
| `archive`             | `https://web.archive.org/web/*/`         |
| `scholar`             | `https://scholar.google.com/scholar?q=`  |
| `ask`                 | `https://www.ask.com/web?q=`             |

Also there are aliases for bang-searching DuckDuckGo:

| Context   | Bang  |
|-----------|-------|
| `wiki`    | `!w`  |
| `news`    | `!n`  |
| `youtube` | `!yt` |
| `map`     | `!m`  |
| `image`   | `!i`  |
| `ducky`   | `!`   |

### Custom search engines

If you want to add other search contexts to the plugin, you can use the
`$ZSH_WEB_SEARCH_ENGINES` variable. Set it before Oh My Zsh is sourced,
with the following format:

```zsh
ZSH_WEB_SEARCH_ENGINES=(
    <context> <URL>
    <context> <URL>
)
```

where `<context>` is the name of the search context, and `<URL>` a URL of
the same type as the search contexts above. For example, to add `reddit`,
you'd do:

```zsh
ZSH_WEB_SEARCH_ENGINES=(reddit "https://www.reddit.com/search/?q=")
```

These custom search engines will also be turned to aliases, so you can
both do `web_search reddit <query>` or `reddit <query>`.
