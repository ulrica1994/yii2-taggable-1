# Taggable Behavior for Yii 2

[![PayPal Donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=HJ6LFVXEX8NDW)
[![Build Status](https://img.shields.io/travis/creocoder/yii2-taggable/master.svg?style=flat-square)](https://travis-ci.org/creocoder/yii2-taggable)
[![Code Coverage](https://img.shields.io/scrutinizer/coverage/g/creocoder/yii2-taggable/master.svg?style=flat-square)](https://scrutinizer-ci.com/g/creocoder/yii2-taggable/?branch=master)

A modern taggable behavior for the Yii framework.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```bash
$ php composer.phar require creocoder/yii2-taggable:dev-master
```

or add

```
"creocoder/yii2-taggable": "dev-master"
```

to the `require` section of your `composer.json` file.

## Configuring

Configure model as follows:

```php
use creocoder\taggable\TaggableBehavior;

class Post extends \yii\db\ActiveRecord
{
    public $tagNames;

    public function behaviors()
    {
        return [
            TaggableBehavior::className(),
        ];
    }

    public function rules()
    {
        return [
            //...
            ['tagNames', 'safe'],
        ];
    }

    public function transactions()
    {
        return [
            self::SCENARIO_DEFAULT => self::OP_ALL,
        ];
    }

    public function getTags()
    {
        return $this->hasMany(Tag::className(), ['id' => 'tag_id'])->viaTable('post_tag_assn', ['post_id' => 'id']);
    }
}
```

## Usage

TBD.
