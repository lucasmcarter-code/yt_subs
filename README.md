# North Star

A private, single-page front end for YouTube. It shows your subscriptions as a wall of cards, finds new videos on topics you choose, and keeps everything you teach it in your own browser and your own Google Drive.

Live app: https://lucasmcarter-code.github.io/yt_subs/

Current version: 52

## What it does

- **Subs**: recent uploads from your subscriptions. Several uploads from one channel within 24 hours fold into one card. Sort by newest, oldest, for you, most viewed, length or channel. Hide watched videos, filter by length, or search.
- **Discover**: recent videos on the topics you list, ranked by what you keep and skip.
- **Following**: your channels, grouped by topic, with a page per channel.
- **Jukebox**: music from the bands you list and bands like them, with a Music and Talk switch, autoplay and shuffle. It reshuffles each time you open it and refills itself once a day. A thumbs-up moves a song to Keepers. **Wrong section** moves a video between Music and Talk, or removes one that is not music or is by the wrong band, and the sorter learns from the words in the title, description and tags.
- **Shorts**: a swipe view for short videos.
- **Learning**: the check and X on each card teach the app what you like. Muted words and blocked categories hide what you don't want.
- **Quality filter**: Discover, Search and Shorts leave out AI-made and content-farm videos, using YouTube's altered-content label, channel age and upload rate, clickbait title patterns, and a **Not legit** button that mutes the channel and teaches a word filter. Channels you subscribe to are not affected in Discover or Search. A Settings switch turns it off.
- **Bell**: notices such as quota use, sync status and new versions.
- **Sync**: optional. Saves your lists and settings to a private file in your own Google Drive so your phone, computer and TV match. The file is `north-star-sync.json` in the app's hidden Drive folder: it does not show among your Drive files, but appears under Drive, Settings, Manage apps. Settings shows when it last synced.
- **Layouts**: phone, desktop (side bar, card wall and an in-page player) and TV (LG webOS browser, remote-control navigation).

## What you need

- A Google account.
- A free YouTube Data API key, or an invite code from someone who already runs North Star.
- For Google sign-in and sync: an OAuth client ID. An invite code can carry this too.

## Install

### Quick start with an invite code

1. Open the live app link.
2. Paste the invite code into step 1 of the welcome page.
3. Sign in with Google, or type your channel handle if your subscriptions are public.
4. Pick a few interests, then choose **Load my feed**.

An invite code shares the sender's API key and its daily quota. It does not share their subscriptions, lists or training. Those are always your own.

### Your own API key

1. Go to console.cloud.google.com and create a project.
2. Open **APIs & Services**, then **Library**, and enable **YouTube Data API v3**.
3. Open **Credentials**, choose **Create credentials**, then **API key**.
4. Restrict the key to YouTube Data API v3, and to the app's web address under Website restrictions.
5. Paste the key into the welcome page or Settings.

### Google sign-in and sync (optional)

1. In the same project, open **Credentials** and create an **OAuth client ID** of type Web application.
2. Add the app's web address as an authorised JavaScript origin.
3. On the OAuth consent screen, add each person who will sign in as a test user.
4. For sync, also enable the **Google Drive API** in the Library.
5. Paste the client ID into Settings, then choose **Turn on sync**.

### Add it to a device

- **iPhone**: open the link in Safari, then Share, then Add to Home Screen.
- **Mac**: open the link in Safari, then File, then Add to Dock. The Dock app keeps its own storage, so set it up or sync it separately.
- **LG TV**: open the link in the TV's web browser and bookmark it. TV mode turns on by itself.

### Host your own copy

Fork this repository and turn on GitHub Pages for the main branch. The whole app is `index.html`. Use your own page address in the API key and OAuth settings.

## Guide

- **Check** marks a video watched and teaches the app you liked it. **X** hides it and teaches the opposite.
- **Refresh** (top bar) fetches new uploads. Discover refreshes are limited per day to protect the API quota. The ring on the Settings button shows quota used.
- **Grouped cards** show the channel name with the videos listed underneath. Tap a title to play it, or the "+N more" badge to spread them out.
- **Settings** is grouped into sections you tap to open (Account, Discover, Jukebox, Look, TV, Sync and backup, Advanced). It holds your topics, tags, muted words, blocked categories, Jukebox bands and search words, the Polaroid title font, a button to refresh your subscription list, sync, backup and TV options.
  - **My topics**: which topics label your cards. Add your own.
  - **My tags**: one per line, such as `Tiny Desk: tiny desk`. A matching video gets that tag.
  - **Start fresh** clears training and lists on one device.
- **Keyboard (desktop)**: Esc closes, space pauses, arrows seek, `/` searches.
- **TV remote**: arrows move card to card. OK selects a card, OK again opens it, and the arrows reach its buttons. Back closes. If the TV browser bar covers the top, adjust "Space for the TV browser bar" in Settings.

## Privacy

- Your API key and client ID stay in the browser you typed them into. They are never synced or backed up.
- Your lists, training and settings stay in your browser. With sync on, a copy goes to a private app folder in your own Google Drive.
- There is no server. The page talks only to Google's YouTube and Drive services, and to MusicBrainz for band-name suggestions.

## Limits

- The YouTube API allows about 10,000 units a day per key. People sharing one key share that quota.
- On phones, videos open in the YouTube app. The in-page player is for desktop and TV.
- Ad-free playback in the in-page player depends on your browser being signed in to a YouTube Premium account, and is not guaranteed.
