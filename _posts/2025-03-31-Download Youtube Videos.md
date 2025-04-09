---
title: Download YouTube member videos
date: 2025-03-31 22:25:00 +200
categories: [Knowledge]
tags: [download, youtube] # TAG names should always be lowercase
---

There's a lot of websites that allow you to download YouTube videos but they fail when it comes to member videos.
Below guide will allow you to download Member videos that you have access to on your YouTube account.

## Installation

We'll need to download **[yt-dlp](https://github.com/yt-dlp/yt-dlp/wiki/Installation)** and preferably **[FFmpeg](https://ffmpeg.org/download.html)** so we have more options when it comes to conversion of downloaded videos to different formats and resolutions.

---

### yt-dlp

**Install yt-dlp** <https://github.com/yt-dlp/yt-dlp/wiki/Installation> in a empty folder

### FFmpeg

**Download FFmpeg** <https://ffmpeg.org/download.html> (for better format conversion)

Extract the FFmpeg files and add ffmpeg.exe to your system PATH (or place it in the same folder as yt-dlp.exe).

&nbsp;

You're now able to download public non-member videos and don't need to do anything more if you're not interested in member content.
Open a terminal in the same folder where you installed yt-dlp and try below command, remeber to replace "[URL]" with an actual Youtube link. It will save videos by default in the same folder as the yt-dlp.exe file are located.

```bash
yt-dlp [URL]
```

&nbsp;

## Cookies

For yt-dlp to be able to access member videos it needs access to your browser cookies.
The easiest way is to use `--cookies-from-browser [Browser]`.

This isn't working with Chrome and may be because of <https://security.googleblog.com/2024/07/improving-security-of-chrome-cookies-on.html> which once rolled out and will likely mean --cookies-from-browser chrome will be permanently broken on Windows. Read more about this issue here: <https://github.com/yt-dlp/yt-dlp/issues/10927>

So we'll use [Firefox](https://www.mozilla.org/en-GB/firefox/new/).
Make sure you have it installed and have signed into your YouTube account.

&nbsp;

## Commands

### Download all members from a channel (You must be a member of their chanel)

Go to a YouTube chanel, click on the Videos tab and copy the URL. Replace https://www.youtube.com/c/Chanelname/videos with the URL and use "" around it

```bash
yt-dlp --cookies-from-browser firefox --match-filter "availability=members" -f bestvideo+bestaudio --merge-output-format mp4 "https://www.youtube.com/c/Chanelname/videos"
```

&nbsp;

### Download all non-members from a channel

To download all non-member videos change filter to `"availability=public”`

```bash
yt-dlp --cookies-from-browser firefox --match-filter "availability=public" -f bestvideo+bestaudio --merge-output-format mp4 "https://www.youtube.com/c/Chanelname/videos" 
```

&nbsp;

### Download a specific video

```bash
yt-dlp -f bestvideo+bestaudio --merge-output-format mp4 --cookies-from-browser firefox "VIDEO_URL"
```

More information about yt-dlp commands <https://github.com/yt-dlp/yt-dlp?tab=readme-ov-file#general-options>

&nbsp;

## Update yt-dlp

If running into any issues, try updating **[yt-dlp](https://github.com/yt-dlp/yt-dlp)**.

You can use `yt-dlp -U` command to update if you are using the release binaries

```bash
yt-dlp -U
```

If you installed with pip, simply re-run the same command that was used to install the program

<!--
There's two alternatives, to save your cookies from the browser in a file or give it direct access from the browser itself.

If they are manually saved to a file it will expire and needs to be updated after they expire.
I recomend giving direct access which won't need to be updated at the moment dosen't work with chrome

Exported chrome cookies with [**Get cookies.txt LOCALLY](https://chromewebstore.google.com/detail/get-cookiestxt-locally/cclelndahbckbenkjhflpdbgdldlbecc)** and saved them in a ****`cookies.txt` file in the same folder (more info about [**cookies**](https://www.reddit.com/r/youtubedl/wiki/cookies/))

~~or --cookies-from-browser chrome [Note! Chrome needs to be closed]~~

So if using the browser instead of manually downloading a file with browser cookies that will expire after a short period of time, download Firefox and sign into your google account in YouTube

Replace `--cookies cookies.txt` With `--cookies-from-browser firefox` in below commands
-->