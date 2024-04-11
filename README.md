# RSS-GPT

[![](https://img.shields.io/github/last-commit/yinan-c/RSS-GPT/dev?label=updated)](https://github.com/yinan-c/RSS-GPT/tree/dev)
[![](https://img.shields.io/github/last-commit/yinan-c/RSS-GPT/main?label=feeds%20refreshed)](https://yinan-c.github.io/RSS-GPT/)
[![](https://img.shields.io/github/license/yinan-c/RSS-GPT)](https://github.com/yinan-c/RSS-GPT/blob/master/LICENSE)


## What is this?

[Configuration Guide](https://yinan-c.github.io/rss-gpt-manual-en.html) | [中文简介](README-zh.md) | [中文教程](https://yinan-c.github.io/rss-gpt-manual-zh.html)

Using GitHub Actions to run a simple Python script repeatedly: Calling OpenAI API to generate summaries for RSS feeds, and push the generated feeds to GitHub Pages. Easy to configure, no server needed.

### Features

- Use ChatGPT to summarize RSS feeds, and attach summaries to the original articles, support custom summary length and target language.
- Aggregate multiple RSS feeds into one, remove duplicate articles, subscribe with a single address.
- Add filters to your own personalized RSS feeds.
- Host your own RSS feeds on GitHub repo and GitHub Pages.

![](https://i.imgur.com/7darABv.jpg)

## Quick configuration guide

- Fork this repo
- Add Repository Secrets
    - U_NAME: your GitHub username
    - U_EMAIL: your GitHub email
    - WORK_TOKEN: your GitHub personal accesstoken with `repo` and `workflow` scope, get it from [GitHub settings](https://github.com/settings/tokens/new)
    - OPENAI_API_KEY(OPTIONAL, only needed when using AI summarization feature): Get it from [OpenAI website](https://platform.openai.com/account/api-keys)
- Enable GitHub Pages in repo settings, choose deploy from branch, and set the directory to `/docs`.
- Configure your RSS feeds in config.ini

You can check out [here](https://yinan-c.github.io/rss-gpt-manual-en.html) for a more detailed configuration guide.

## ChangeLog and updates

- There is a [`dev` branch](https://github.com/yinan-c/RSS-GPT/tree/dev) for manual updates on the script, auto commits will no longer be pushed to this `dev` branch. The purpose of doing this is to separate the manual updates and auto commits, so that it is easier to check the updates and pull to your repo.
- As OpenAI released a new version of `openai` package on Nov 06, 2023.  [More powerful models are coming](https://openai.com/blog/new-models-and-developer-products-announced-at-devday), the way to call API also changed. As a result, the old script will no longer work with the latest version installed, and needs to be updated. Otherwise, you will have to set `openai==0.27.8` in `requirements.txt` to use the old version.
-  In the latest updates, **contexts longer than 16k tokens are no longer truncated, instead, will use the `gpt-4-1106-preview` model.** If you don't like this, let me know and I'll think about adding customizability to choose whether truncate or use `gpt-4-1106-preview` model.
- Check out the [CHANGELOG.md](CHANGELOG.md).

### Contributions are welcome!

- Feel free to submit issues and pull requests. Please submit pull requests to the `dev` branch.

## Example feeds being processed

These feeds on hosted in the [`docs/` subdirectory](https://github.com/yinan-c/RSS-GPT/tree/main/docs) in this repo as well as on my [GitHub Pages](https://yinan-c.github.io/RSS-GPT/). Feel free to subscribe in your favorite RSS reader.

I will consider hosting more feeds in the future. Email me or submit an issue if there is any question using the script or any suggestions.

- https://glacier0000.vercel.app/woshipm/popular -> https://glacier0000.github.io/RSS-GPT/ren-ren-pm.xml
- https://meta.appinn.net/tag/chrome.rss, https://meta.appinn.net/tag/ios.rss, https://meta.appinn.net/tag/macos.rss -> https://glacier0000.github.io/RSS-GPT/appinn.xml
- https://rsshub.app/sspai/index -> https://glacier0000.github.io/RSS-GPT/sspai.xml
- https://glacier0000.vercel.app/sspai/matrix -> https://glacier0000.github.io/RSS-GPT/shao-shu-pai.xml
- https://glacier0000.vercel.app/huxiu/article -> https://glacier0000.github.io/RSS-GPT/hu-xiu.xml
- https://wechat2rss.xlab.app/feed/90c827b8290310a96ef80a13df9dbcc06ab69892.xml -> https://glacier0000.github.io/RSS-GPT/wu-ai-po-jie.xml
- https://rsshub.app/36kr/motif/327685554177, https://rsshub.app/36kr/motif/327687077889, https://rsshub.app/36kr/motif/1366661828936836, https://rsshub.app/36kr/motif/1366662419875203, https://rsshub.app/36kr/motif/1756302767423108, https://rsshub.app/36kr/motif/327686815745, https://rsshub.app/36kr/motif/327685734401 -> https://glacier0000.github.io/RSS-GPT/36kr.xml
- https://rsshub.app/36kr/motif/327686782977 -> https://glacier0000.github.io/RSS-GPT/36kr-ai.xml
- https://wechat2rss.xlab.app/feed/574587b13c6f60617fc74605702258ddf4aefac6.xml -> https://glacier0000.github.io/RSS-GPT/lao-gao.xml
- https://wechat2rss.xlab.app/feed/6111a6d5ecf28cfdd4fc9b664244c05ddacef15c.xml -> https://glacier0000.github.io/RSS-GPT/qian-hei.xml
- https://wechat2rss.xlab.app/feed/31436fcc3bba8c2c2a9337a163afcb3b5a57a0a0.xml -> https://glacier0000.github.io/RSS-GPT/42-zhang-jing.xml
- https://wechat2rss.xlab.app/feed/8d839de8dd3290a1f1be7a94423cccb30c1b087d.xml -> https://glacier0000.github.io/RSS-GPT/cha-ping.xml
