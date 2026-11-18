# ShortsReplay-10K

Most Replayed curves ("replay signatures") and metadata of YouTube Shorts and of long regular videos from the same
channels, released with the paper "ShortsReplay-10K: A Dataset for Measuring and Predicting Replay in YouTube Shorts".

## Contents

| Path | What it holds |
|---|---|
| `YouTubeShortsData.csv` | The AMPS video list (Cho et al., 2024): 12,511 Shorts from 47 channels with metadata collected in July 2023 (title, description, counts, upload time, English translations). The column with local file paths was removed. |
| `shorts/<id>/` | 11,885 Shorts of that list that were still available in September 2026; 10,725 have a Most Replayed curve. |
| `long_videos/<id>/` | 1,494 regular (long) videos from channels of the same creators, collected in November 2026; 1,136 have a Most Replayed curve. |

Each video folder holds two files:

* `<id>_metadata.json`: `id`, `title`, `description`, `tags`, `categories`, `language`, `media_type`, `channel_id`, `channel`, `channel_follower_count`, `duration`, `view_count`, `like_count`, `comment_count`, `upload_date`, `timestamp`, `epoch`, `webpage_url`, `fps`, `width`, `height` (as returned by yt-dlp; a key is missing when YouTube did not provide it).
* `<id>_heatmap.json`: the Most Replayed data, a list of 100 markers `{"start_time", "end_time", "value"}` in seconds
  that tile the video in equal slices. The list is empty when YouTube shows no curve for the video (too few views).

## How to read the values

Within every video the values span exactly 0 to 1: YouTube rescales each curve between its least and most watched
slice. A value of 0 marks the least watched slice of that video, not a slice nobody watched, and heights cannot be
compared between videos. Differences and positions within a curve are meaningful; ratios are not.

## What is not included

No video files and no data about individual viewers: each curve is an aggregate over all views of a video.
Titles, descriptions and tags are the creators' own text and remain theirs.

## Provenance

* Video list: AMPS (Cho et al., 2024). Please cite it together with this dataset.
* Curves and current metadata: public YouTube pages, collected with yt-dlp in September 2026 (Shorts) and
  November 2026 (regular videos).

## Citation

To be added after publication.

## Licence and takedown

The compilation (curves, folder structure, this card) is released under CC BY 4.0 (see LICENSE). Video content,
titles, descriptions and tags belong to their creators and are subject to YouTube's terms. Creators who want a video
removed from the dataset can contact the authors; the entry will be deleted in the next version.
