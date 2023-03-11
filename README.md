# Taboo Data

More than 700 English and 500 Turkish taboo data that you can use wherever you want.


#### ITEM

| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `_language`      | `String` | **The Language of Taboo** |
| `word`      | `String` | **The word want to tell** |
| `forbidden_words`      | `List<String>` | **Forbidden Words**, (lenght is 5 each data)|




## Example Parse

### Model
```dart
class TabooModel {
  final String? word;
  final List<String>? forbiddenWords;
  final String? language;

  const TabooModel({this.word, this.forbiddenWords, this.language});

  factory TabooModel.fromJson(Map<String, dynamic> json) {
    return _$TabooModelFromJson(json);
  }

  Map<String, dynamic> toJson() => _$TabooModelToJson(this);

  Taboo toEntity() {
    // var customForbiddenWords = '';

    final buffer = StringBuffer();

    for (final e in forbiddenWords!) {
      // customForbiddenWords += '$e,';

      buffer.write('$e,');

      //* we  can't store the array in sqlite database, so we can add a comma at the end of each word
      //* and split it with a comma and use it in future operations.
    }

    return Taboo(
        word: word, forbiddenWords: buffer.toString(), language: language);
  }

}

```
