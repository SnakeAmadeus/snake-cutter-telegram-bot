# Snake Cutter Telegram Bot
Telegram bot that cuts YouTube and Twitter videos conveniently.

# Deployment
The bot is deployed on Vercel. You can tweak the deployment specification in `vercel.json`

# APIs
## Timestamp Format:
video timestamp supports the following formats:
- SSs e.g. 69s 420s
- MM:SS e.g. 1:09 7:00
- MM:SS.MSS e.g. 1:09.240
- `HH:MM:SS` e.g. 1:09:42
Any time that exceeds the video length will be trimmed to the last frame of the video.
## Time Interval Format:
To specify an time interval for cutting the video, use the following format:
use hyphen:
- `start-end`
OR use tilde:
- `start~end`
The `start` and `end` both follow the timestamp format.
If only one timestamp specified, by default, it will cuts the video by the starting time:
- `start`: cut the video from `start` to the very end
- `start-`: same as above
However, you can also cut video until the end time:
- `-end`: cut the video from the very begining to `end`
## Commands:
### `/cut`
```shell
/cut [options] [url] [interval]
```
options: -a, --audio convert the cutting result to .mp3 and return
interval: interval is optional, if no interval specified then it will return the full video
url: url is also optional, if no url specified then it will cut the last cutted video. 

### `/compress`
```shell
/compress [url] rate
```
url: url is optional, if no url specified, it will use the last cutted video as oprands.
rate: specify the size compression of the video, supports the following format:
- MB, e.g. "20MB" "20mb" "20"
- %, e.g. "90%" "80%"
- float, e.g. "0.9" ".8"
any rate that exceeds the original video size will force the bot use the default compression rate of 80%

### `/info`
```shell
/info
```
Print the codecs/size information of the last cutted video.

### User Upload
User can upload a media (video or audio) and the bot will automatically set that video as the last cutted video.

# Dependency
- fastAPI
- telelgram-bot-api
- ffmpeg

