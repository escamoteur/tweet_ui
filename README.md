# tweet_ui

Flutter Tweet UI - Flutter package that is inspired from [twitter-kit-android](https://github.com/twitter-archive/twitter-kit-android). 

Works on iOS and Android.

## Getting Started

To use this package add it to the pubspec.yaml file:

`tweet_ui: <latest_version>`

import it:
 
`import 'package:tweet_ui/tweet_ui.dart';`

and create a `TweetView` from a JSON:

```dart
TweetView.fromTweet(
    Tweet.fromRawJson(
        jsonFromTwitterAPI
        // {"created_at": "Mon Nov 12 13:00:38 +0000 2018", "id": 1061967001177018368, ...
    )
);
```

or a `CompactTweetView`

```dart
CompactTweetView.fromTweet(
    Tweet.fromRawJson(
        jsonFromTwitterAPI
        // {"created_at": "Mon Nov 12 13:00:38 +0000 2018", "id": 1061967001177018368, ...
    )
);
```

There is also a special `QuoteTweetView` that is embedded in a `TweetView` or a `CompactTweetView`. This depends if a Tweet has a `quoted_status` value in the JSON.

## Example of supported view and media types:

> Sample tweets use real life tweet ids but for example purposes their content was changed.

| Variant  | Standard tweet                                                           | Compact tweet                                                           | Standard Quote tweet                                                           | Compact Quote tweet                                                           |
|:--------:|:-------------------------------------------------------------------------|:------------------------------------------------------------------------|:-------------------------------------------------------------------------------|:------------------------------------------------------------------------------|
| 1 photo  | <img src="screenshots/standard_1_photo.png" width="150" height="300" />  | <img src="screenshots/compact_1_photo.png" width="150" height="300" />  | <img src="screenshots/standard_quote_1_photo.png" width="150" height="300" />  | <img src="screenshots/compact_quote_1_photo.png" width="150" height="300" />  |
| 2 photos | <img src="screenshots/standard_2_photos.png" width="150" height="300" /> | <img src="screenshots/compact_2_photos.png" width="150" height="300" /> | <img src="screenshots/standard_quote_2_photos.png" width="150" height="300" /> | <img src="screenshots/compact_quote_2_photos.png" width="150" height="300" /> |
| 3 photos | <img src="screenshots/standard_3_photos.png" width="150" height="300" /> | <img src="screenshots/compact_3_photos.png" width="150" height="300" /> | <img src="screenshots/standard_quote_3_photos.png" width="150" height="300" /> | <img src="screenshots/compact_quote_3_photos.png" width="150" height="300" /> |
| 4 photos | <img src="screenshots/standard_4_photos.png" width="150" height="300" /> | <img src="screenshots/compact_4_photos.png" width="150" height="300" /> | <img src="screenshots/standard_quote_4_photos.png" width="150" height="300" /> | <img src="screenshots/compact_quote_4_photos.png" width="150" height="300" /> |
|  video*   | <img src="screenshots/standard_video.png" width="150" height="300" />    | <img src="screenshots/compact_video.png" width="150" height="300" />    | <img src="screenshots/standard_quote_video.png" width="150" height="300" />    | <img src="screenshots/compact_quote_video.png" width="150" height="300" />    |
|   GIF    | <img src="screenshots/standard_gif.png" width="150" height="300" />      | <img src="screenshots/compact_gif.png" width="150" height="300" />      | <img src="screenshots/standard_quote_gif.png" width="150" height="300" />      | <img src="screenshots/compact_quote_gif.png" width="150" height="300" />      |

> *If you want to show tweets with videos, please check the [video_player installation](https://pub.dev/packages/video_player#installation).

## Styling Tweets

By default the `chewie`/`video_player` package is used to show a gif/video, but you can set the `useVideoPlayer` flag to `false` if you want to show a image placeholder provided by the Twitter API and open a video in a new page.

|    Variant    | With video_player/chewie                                                               | With placeholder                                                         |
|:-------------:|:-----------------------------------------------------------------------------|:----------------------------------------------------------------------------|
| Standard Video | <img src="screenshots/standard_video.png" width="150" height="300" /> | <img src="screenshots/standard_video_placeholder.png" width="150" height="300" /> |
| Compact Video | <img src="screenshots/compact_video.png" width="150" height="300" /> | <img src="screenshots/compact_video_placeholder.png" width="150" height="300" /> |
| Standard GIF | <img src="screenshots/standard_gif.png" width="150" height="300" /> | <img src="screenshots/standard_gif_placeholder.png" width="150" height="300" /> |
| Compact GIF | <img src="screenshots/compact_gif.png" width="150" height="300" /> | <img src="screenshots/compact_gif_placeholder.png" width="150" height="300" /> |


All texts are customizable. You can copy from the `defaultxxx`, `defaultCompactxxx` and `defaultQuotexxx`styles like in the example below.

```dart
Card(
    color: Colors.grey,
    child: Padding(
      padding: const EdgeInsets.all(8.0),
      child: CompactTweetView.fromTweet(
        Tweet.fromRawJson(
          snapshot.data,
        ),
        useVideoPlayer: false,
        userNameStyle: defaultUserNameStyle.copyWith(fontWeight: FontWeight.w200),
        userScreenNameStyle: defaultUserScreenNameStyle.copyWith(fontWeight: FontWeight.w600),
        textStyle: defaultTextStyle.copyWith(
          fontWeight: FontWeight.w200,
          fontStyle: FontStyle.italic,
          shadows: [Shadow(color: Colors.white30)],
        ),
        clickableTextStyle: defaultClickableTextStyle.copyWith(color: Colors.white),
        backgroundColor: Colors.grey,
        quoteUserNameStyle: defaultQuoteUserNameStyle.copyWith(fontWeight: FontWeight.w800),
        quoteUserScreenNameStyle: defaultQuoteUserScreenNameStyle.copyWith(fontWeight: FontWeight.w100),
        quoteTextStyle: defaultQuoteTextStyle.copyWith(fontStyle: FontStyle.italic),
        quoteClickableTextStyle: defaultQuoteClickableTextStyle.copyWith(color: Colors.cyanAccent),
        quoteBorderColor: Colors.blueAccent,
        quoteBackgroundColor: Colors.blueGrey,
      ),
    ),
  );
```

|    Variant    | Standard tweet                                                               | Compact tweet                                                               |
|:-------------:|:-----------------------------------------------------------------------------|:----------------------------------------------------------------------------|
| Custom styles | <img src="screenshots/standard_quote_custom.png" width="150" height="300" /> | <img src="screenshots/compact_quote_custom.png" width="150" height="300" /> |

<img src="screenshots/diagram.jpg"/>


## TODO

1. Get Tweets from Twitter API
2. Write tests
3. Add option to set image quality