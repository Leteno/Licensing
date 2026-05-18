---
title: Video Companion — Privacy Policy
permalink: /video-companion/
---

English
-------

Video Companion is a browser extension that acts as an AI viewing
companion for **Bilibili** and **YouTube**. We care about your privacy.
We do not sell your data, we do not build an advertising profile of
you, and we keep on-device what can stay on-device. Every way in which
Video Companion uses your data is described below.

### Single purpose

Video Companion has a single purpose: to help you understand and
interact with the video you are currently watching on Bilibili or
YouTube. It does this by reading the **subtitle track that the video
page itself already serves** and letting you run on-demand AI actions
against that text from a floating panel on the page.

The actions available are:

- Summarize the video.
- Ask questions about the video ("Q&A").
- Extract timestamped highlights.
- Generate a quiz from the content.
- Generate a cooking-recipe brief from a recipe video (uses a few
  small video-frame thumbnails — see below).

Video Companion does **not** download the video itself, does **not**
record your screen or microphone, and does **not** modify the video
stream in any way.

### What happens automatically on a video page

When you visit a Bilibili or YouTube video page, Video Companion's
content script loads as part of normal browser extension behavior.
While the page is open, the extension does the following **locally,
without sending anything off your device**:

- Observes the site's own subtitle API responses
  (e.g. `/x/player/wbi/v2` on Bilibili, `/youtubei/v1/player` and
  `/api/timedtext` on YouTube) to learn which subtitle tracks the
  video offers and to read the subtitle text.
- Caches the subtitle text for that specific video in your browser's
  local extension storage, so reopening the same video does not have
  to refetch.
- Shows a small floating panel on the page so you can trigger AI
  actions when you want them.

No data is sent to any AI provider, to our servers, or to anywhere
else, at this stage. Reading the subtitles the site already exposed
to your browser stays entirely on your device until you press a
button.

### What happens when you trigger an AI action

When you press a button in the panel (or type a question and submit
it), Video Companion sends the following to an AI provider you have
chosen, over HTTPS:

- The subtitle text of the current video (or the relevant excerpt).
- Your prompt / question / chosen action.
- The minimum surrounding context the feature needs (for example, the
  video title and the timestamp of a clip).
- For the cooking-recipe brief feature only: a small number of
  low-resolution still images (320×180 JPEGs) sampled from the
  video element on the page, so the model can see ingredient labels
  or pan contents that aren't described in the subtitles.

We do **not** send your browsing history, the contents of other tabs,
cookies, account credentials, or pages you have not asked Video
Companion to act on.

If the current video does not expose a subtitle track, the AI
features are simply unavailable for that video — Video Companion
does not attempt to transcribe the audio itself.

### AI provider

The AI actions run on a third-party large-language-model provider that
you configure. By default Video Companion looks for a local LLM
gateway running on `localhost` (so privacy-conscious users can keep
everything on their own machine); if you instead enter an OpenAI API
key in our settings, requests go directly from your browser to
`https://api.openai.com` over HTTPS, using your own key. **Video
Companion does not run any LLM proxy of its own** — request content
does not pass through any server we operate.

The provider you chose may retain request data for a short period for
abuse prevention and reliability, in accordance with that provider's
own privacy policy. We have no access to that retained data.

We do not use any of your data to train any model.

### Text-to-Speech (currently disabled in the published build)

Video Companion ships with a Text-to-Speech (TTS) module that can
read a subtitle line aloud through Microsoft Edge's free Read Aloud
service. **In the current Chrome Web Store release this feature is
intentionally hidden**: the underlying code is bundled with the
extension but the user-facing entry point is removed, so the TTS
WebSocket is never opened in normal use. The module is retained so
it can be enabled in a future release without re-requesting
permissions.

If and when TTS is exposed in a future build, the behavior will be:
the extension opens a WebSocket connection to
`wss://speech.platform.bing.com` only at the moment you press the
"speak this" control on a subtitle line, sends that single line of
subtitle text plus the chosen voice and rate, receives synthesized
audio, plays it back, and closes the connection. No audio is ever
recorded from your microphone, and no subtitle text is sent to the
TTS service unless you press the control.

### Local data

The following data is stored **only in your browser**, using the
browser's extension storage, and never leaves your device unless you
trigger an AI action that explicitly needs it:

- Your settings (interface language, panel position, the LLM endpoint
  URL you configured, your optional API key, popup toggles).
- A per-video subtitle cache, so reopening the same video does not
  refetch the subtitles.
- A short history of recent AI results (so reopening the panel on the
  same video can show you what you last got).
- A token-usage ledger so you can see how much you've spent.

`unlimitedStorage` is requested so this cache can grow past the
default 10 MB extension-storage quota for users who watch many long
videos.

You can clear all local data at any time by removing the extension or
clearing extension storage in your browser.

### What we do not do

- We do not insert ads into the page.
- We do not inject scripts unrelated to Video Companion's features.
- We do not track your browsing across sites.
- We do not sell, rent, or share your data with third parties for
  marketing.
- We do not collect personal information such as name, email, phone
  number, or payment details. (If a future paid tier requires an
  account, this policy will be updated before that feature ships.)
- We do not operate any server that receives your subtitle text,
  prompts, or API keys.

### Permissions

Video Companion requests the minimum browser permissions needed for
its features:

| Permission                                  | Why it is needed                                                                                                |
|---------------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| `storage`                                   | Save your settings, your subtitle/result cache, and your usage ledger in the browser, all locally.              |
| `unlimitedStorage`                          | Allow the local subtitle/result cache to grow past the default 10 MB quota for users who watch many videos.     |
| Host access to `*.bilibili.com`             | Inject the floating panel on Bilibili video pages and read the subtitle track the page already serves.          |
| Host access to `*.youtube.com`              | Inject the floating panel on YouTube video pages and read the caption track the page already serves.           |
| Host access to `api.openai.com`             | Send your AI request directly from your browser to OpenAI when you have configured an OpenAI key. Optional.     |
| Host access to `127.0.0.1` and `localhost`  | Let users who run a local LLM gateway (e.g. LiteLLM) on their own machine keep all AI traffic on the device.    |
| Host access to `speech.platform.bing.com`   | Reserved for the bundled-but-currently-hidden Edge Read Aloud TTS module; not used in the published build.      |

### Changes to this policy

We may update this Privacy Policy when Video Companion's features
change. The "Last updated" date below indicates when this page was
last modified.

### Contact

For questions about this Privacy Policy, contact:

**mszheng94@outlook.com**

_Last updated: 2026-05-18_


中文
----

Video Companion 是一个浏览器扩展，作为 **Bilibili** 和 **YouTube** 的
AI 观看助手。我们尊重您的隐私权。我们不会出售您的数据，不会为您建立
广告画像，也会让能够留在本地的数据尽可能留在本地。以下列出了 Video
Companion 使用数据的所有方式。

### 单一用途

Video Companion 只有一个用途：帮助您理解和交互您当前在 Bilibili 或
YouTube 上观看的视频。它通过读取**视频页面本身已经提供的字幕轨道**，
并在页面上的浮动面板中按需运行 AI 操作来实现这一点。

可用的操作包括：

- 视频内容总结。
- 针对视频内容进行问答（Q&A）。
- 提取带时间戳的精彩片段。
- 根据内容生成测验题。
- 针对菜谱类视频生成菜谱卡片（会用到少量低分辨率画面截图——见下文）。

Video Companion **不会**下载视频本身，**不会**录制您的屏幕或麦克风，
也**不会**以任何形式修改视频流。

### 在视频页面上自动发生的事

当您访问 Bilibili 或 YouTube 视频页面时，Video Companion 的内容脚本
会按照浏览器扩展的常规机制随页面加载。页面打开期间，扩展只在**您的
设备本地**做以下事情，不会向任何外部服务器发送数据：

- 观察网站自身的字幕接口响应（例如 Bilibili 的
  `/x/player/wbi/v2`，YouTube 的 `/youtubei/v1/player` 与
  `/api/timedtext`），以便知道该视频有哪些字幕轨道并读取字幕文本。
- 将该视频的字幕文本缓存到浏览器的本地扩展存储中，下次重新打开同一
  视频时无需再次拉取。
- 在页面上显示一个小的浮动面板，方便您在需要时触发 AI 操作。

在此阶段，扩展不会把任何数据发送给 AI 服务商、我们的服务器或其他任何
位置。读取浏览器本来就能从网站收到的字幕，完全发生在您的本地设备上，
直到您主动按下某个按钮为止。

### 您触发 AI 操作时发生的事

当您点击面板里的某个按钮（或输入问题并提交）时，Video Companion 会
通过 HTTPS 把以下内容发送给您所选择的 AI 服务商：

- 当前视频的字幕文本（或相关片段）。
- 您输入的指令 / 问题 / 选定的操作。
- 该功能正常工作所需的最小上下文（例如视频标题、片段时间戳）。
- 仅菜谱卡片功能会用到：从页面上的 `<video>` 元素采样的若干张低
  分辨率静态画面（320×180 JPEG），以便模型能够看到食材标签或锅中
  内容等字幕里没有描述的画面信息。

我们**不会**发送您的浏览历史、其他标签页的内容、Cookie、账号凭据，
或您未要求 Video Companion 处理的页面。

如果当前视频没有提供字幕轨道，相关 AI 功能在该视频上将不可用 ——
Video Companion 不会尝试自行转录音频。

### AI 服务商

AI 操作运行在您所配置的第三方大语言模型服务商上。Video Companion
默认会先在 `localhost` 上寻找本地 LLM 网关（方便注重隐私的用户把
一切留在自己机器上）；如果您在设置里填入 OpenAI API 密钥，那么请求
会通过 HTTPS 由您的浏览器**直接发往** `https://api.openai.com`，
使用您自己的密钥。**Video Companion 不运营任何 LLM 代理服务器** ——
请求内容不会经过任何我们运营的服务器。

您所选择的服务商可能会按其自身的隐私政策，出于防滥用和可用性目的
短期保留请求数据。我们对这些被保留的数据没有访问权。

我们不会使用您的任何数据训练任何模型。

### 文本转语音（当前已在发布版本中隐藏）

Video Companion 内置了一个文本转语音（TTS）模块，可以通过 Microsoft
Edge 的免费朗读服务把一条字幕读出来。**在当前 Chrome 应用商店发布的
版本中，此功能被刻意隐藏**：相关代码仍随扩展一同打包，但用户可见的
入口已被移除，因此在正常使用过程中不会建立 TTS WebSocket 连接。保留
该模块是为了未来版本可以直接启用，无需重新申请权限。

未来版本如果重新开放此功能，其行为如下：当且仅当您点击某条字幕旁的
"朗读"按钮时，扩展才会与 `wss://speech.platform.bing.com` 建立
WebSocket 连接，将该条字幕文本以及所选发音人和语速发送过去，接收
合成后的音频并播放，然后关闭连接。我们永远不会通过麦克风录音，也
不会在您未点击该按钮的情况下把字幕文本发送给 TTS 服务。

### 本地数据

以下数据**仅**通过浏览器的扩展存储保存在您的浏览器中，除非您触发
明确需要把它发送出去的 AI 操作，否则不会离开您的设备：

- 您的设置（界面语言、面板位置、您配置的 LLM 服务地址、可选的 API
  密钥、Popup 中的开关）。
- 按视频的字幕缓存，以便您重新打开同一视频时无需重新拉取。
- 最近的 AI 结果短期历史，以便您在同一视频上重新打开面板时还能看到
  上次的结果。
- 用量账本（Token usage ledger），方便您查看自己的消耗。

为了让上述缓存在重度用户场景下不会撞上扩展存储默认 10 MB 上限，我们
申请了 `unlimitedStorage` 权限。

您可以随时通过卸载扩展或清除浏览器中的扩展存储来删除所有本地数据。

### 我们不会做的事

- 不会在页面中插入广告。
- 不会注入与 Video Companion 功能无关的脚本。
- 不会跨站点跟踪您的浏览行为。
- 不会为营销目的出售、出租或共享您的数据。
- 不会收集姓名、邮箱、电话号码、支付信息等个人信息。（如未来推出
  需要账号的付费功能，我们会在该功能上线前更新本政策。）
- 不会运营任何接收您字幕文本、指令或 API 密钥的服务器。

### 权限

Video Companion 只申请实现其功能所必需的最小浏览器权限：

| 权限                                              | 用途                                                                                       |
|---------------------------------------------------|--------------------------------------------------------------------------------------------|
| `storage`                                         | 在浏览器本地保存您的设置、字幕/结果缓存以及用量账本。                                       |
| `unlimitedStorage`                                | 允许字幕/结果本地缓存超过默认 10 MB 扩展存储配额，以适配长期、大量观看视频的用户。           |
| 对 `*.bilibili.com` 的主机访问                    | 在 Bilibili 视频页面注入浮动面板，并读取页面本身已提供的字幕轨道。                          |
| 对 `*.youtube.com` 的主机访问                     | 在 YouTube 视频页面注入浮动面板，并读取页面本身已提供的字幕轨道。                           |
| 对 `api.openai.com` 的主机访问                    | 当您配置了 OpenAI 密钥时，让浏览器直接把 AI 请求发往 OpenAI。可选。                          |
| 对 `127.0.0.1` 和 `localhost` 的主机访问           | 让使用本地 LLM 网关（例如 LiteLLM）的用户能够把全部 AI 流量保留在本机。                      |
| 对 `speech.platform.bing.com` 的主机访问           | 为已内置但当前隐藏的 Edge 朗读 TTS 模块预留；在当前发布版本中不会被使用。                    |

### 政策变更

当 Video Companion 的功能发生变化时，我们可能会更新本隐私政策。本页
底部的"最后更新"日期表示本政策的最近一次修改时间。

### 联系方式

如果您对本隐私政策有任何疑问，请联系：

**mszheng94@outlook.com**

_最后更新：2026-05-18_
