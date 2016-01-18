# HashTagHelper
This is a library designed for highlighting hashtags ("#example") and catching click on them.

[![Android_weekly](https://img.shields.io/badge/Android%20Weekly-HashTagHelper-green.svg)](http://androidweekly.net/issues/issue-185)
[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-HashTagHelper-green.svg?style=true)](https://android-arsenal.com/details/1/2953) 

#Usage
Add this snippet to your project build.gradle file:
```
buildscript {
    repositories {
        jcenter()
    }
}
```
Add this snippet to your module build.gradle file:

```
dependencies {
    compile 'com.github.danylovolokh:hashtag-helper:1.1.0'
}
```
Getting click events and highligthing hashtags.
```
private HashTagHelper mTextHashTagHelper;

private TextView mHashTagText;

@Override
protected void onCreate(Bundle savedInstanceState) {

  mHashTagText = (TextView) findViewById(R.id.text);
  mTextHashTagHelper = HashTagHelper.Creator.create(getResources().getColor(R.color.colorPrimary), new HashTagHelper.OnHashTagClickListener() {
    @Override
    public void onHashTagClicked(String hashTag) {
        
    }
  });
        
  // pass a TextView or any descendant of it (incliding EditText) here.
  // Hash tags that are in the text will be hightlighed with a color passed to HasTagHelper
  mTextHashTagHelper.handle(mHashTagText);
}
```
Highlighting without click events.
Just set "null" instead of HashTagHelper.OnHashTagClickListener;
```
mTextHashTagHelper = HashTagHelper.Creator.create(getResources().getColor(R.color.colorPrimary), null);
mTextHashTagHelper.handle(mHashTagText);
```
By default only digits and letters are valid symbols for hashtag
To add support of custom symbols like '_' or '-' you need to specify another parameter when creating HashTagHelper
```
char[] additionalSymbols = new char[]{
                '_',
                '$'
        };
// If you set additional symbols not only letters and digits will be a valid symbols for hashtag
// Example: "hash_tag_with_underscore_and$dolar$sign$is$also$valid_hashtag"
mTextHashTagHelper = HashTagHelper.Creator.create(getResources().getColor(R.color.colorPrimary), null, additionalSymbols);
mTextHashTagHelper.handle(mHashTagText);

```
To get all hashtags from text.
```
// get all hashtags with "#", example: "#blueeyes"
List<String> allHashTags = mTextHashTagHelper.getAllHashTags(true);

// get all hashtags without "#", example: "blueeyes"
List<String> allHashTags = mTextHashTagHelper.getAllHashTags(false);
```
#Demo
![alt tag](https://cloud.githubusercontent.com/assets/2686355/11998408/e6aa1f62-aaa6-11e5-911a-c598b6853862.gif) ![alt tag](https://cloud.githubusercontent.com/assets/2686355/11998409/e6aa3ed4-aaa6-11e5-9797-100a024659cc.gif)

# License

Copyright 2015 Danylo Volokh

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
