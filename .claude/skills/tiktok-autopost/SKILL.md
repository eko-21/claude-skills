---
name: tiktok-autopost
description: Posts the user's finished video clips to their TikTok account with their saved default settings. Use right after a clip is generated with the Videos (Higgsfield) tools, and whenever the user asks to post, upload or publish a clip or video to TikTok ("poste das auf TikTok", "hochladen", "veröffentlichen").
---

# TikTok Autopost

The user wants every clip made for them to go to TikTok straight away. After a clip is finished, prepare the TikTok post without asking first, unless the user said that this clip is not for TikTok.

## Saved defaults

| Setting | Value | Tool parameter |
|---|---|---|
| Mode | Post directly to the profile | `mode: "DIRECT_POST"` |
| Visibility | Everyone | `privacy_level: "PUBLIC_TO_EVERYONE"` |
| Comments | allowed | `allow_comment: true` |
| Duets | allowed | `allow_duet: true` |
| Stitch | allowed | `allow_stitch: true` |
| Caption language | English | `title`, `description` |
| AI-generated label | on for clips made with the Videos tools | `is_aigc: true` |

A setting the user names for a single clip (for example "only for me" or "save as draft") overrides the default for that clip only. Do not prefill `commercial_content_disclosure` unless the user said the clip is an ad or sponsored; the publish form asks for it.

## Workflow

1. **Account.** Call `mcp__Videos__tiktok_accounts` and take the `connector_id` of the account with status `active`.
   - No account: call `mcp__Videos__tiktok_connect` and give the user the link.
   - Status `error`: call `mcp__Videos__tiktok_reconnect` and give the user the link.
2. **Video.** The `video_url` must be the Higgsfield-hosted URL of the finished clip; TikTok accepts no other source. Check TikTok's limits before preparing: MP4, WebM or MOV, at most 1 GB, 3 to 600 seconds, at least 360 px on both sides, 23 to 60 FPS. If the clip breaks a limit, tell the user and fix it first (for example `mcp__Videos__upscale_video` or a re-render).
3. **Caption** in English:
   - `title`: a hook of at most 150 characters, ending with 3 to 5 relevant hashtags.
   - `description`: one or two short sentences about the clip, at most 4000 characters.
   - Apply the `stop-slop` rules if that skill is available.
4. **Prepare.** Call `mcp__Videos__tiktok_prepare_publish` with `media_type: "VIDEO"`, the `connector_id`, `video_url`, `title`, `description` and the defaults from the table.
5. **Hand over.** The publish form appears for the user. Tell them in one line (in German) to check it and click post. Never call `tiktok_publish` yourself: the connector requires the user's own submission.
6. **Status.** When the user says they posted, call `mcp__Videos__tiktok_publish_status` and report the result.

## Limits

- The publish form needs a client that shows MCP Apps (the Claude app or claude.ai). In a terminal, tell the user to open this conversation in the Claude app to finish the post.
- This skill covers TikTok only.
