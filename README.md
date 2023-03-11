# Taboo Data

More than 700 English and 500 Turkish taboo data that you can use wherever you want.



| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `_language`      | `String` | **The Language of Taboo** |
| `word`      | `String` | **The word want to tell** |
| `forbidden_words`      | `List<String>` | **Forbidden Words**, (lenght is 5 each data)|



### Model (with Dart)
```dart
// To parse this JSON data, do
//
//     final tabooModel = tabooModelFromJson(jsonString);

import 'dart:convert';

TabooModel tabooModelFromJson(String str) => TabooModel.fromJson(json.decode(str));

String tabooModelToJson(TabooModel data) => json.encode(data.toJson());

class TabooModel {
    TabooModel({
        required this.language,
        required this.word,
        required this.forbiddenWords,
    });

    String language;
    String word;
    List<String> forbiddenWords;

    factory TabooModel.fromJson(Map<String, dynamic> json) => TabooModel(
        language: json["_language"],
        word: json["word"],
        forbiddenWords: List<String>.from(json["forbidden_words"].map((x) => x)),
    );

    Map<String, dynamic> toJson() => {
        "_language": language,
        "word": word,
        "forbidden_words": List<dynamic>.from(forbiddenWords.map((x) => x)),
    };
}


```
