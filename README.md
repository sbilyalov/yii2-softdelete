# Yii2 Soft Delete

This behaviour added soft-delete functionality to your active record


##Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Run:

```
php composer.phar require sbilyalov/yii2-softdelete "*"
```

or add

```
"sbilyalov/yii2-softdelete": "*"
```

to your `composer.json` file.


## Usage

```php
use sbilyalov\yii2\behaviors\SoftDelete;

public function behaviors ()
{
    return [
        SoftDeleteBehavior::className()
    ];
}
```

By default the SoftDelete behavior fills the `is_deleted` attribute with the number - 1

If your attribute names are different or you want to use a different way of mark deleted record
you may configure the [[attribute]] and [[value]] properties like the following:


```php
use sbilyalov\yii2\behaviors\SoftDelete;
use yii\db\Expression;

public function behaviors ()
{
    return [
        [
            'class' => SoftDeleteBehavior::className(),
            'attribute' => 'deleted_time',
            'value' => new Expression('NOW()'),
            'restoreValue' => null
        ]
    ];
}
```

## Additional functions for active record model

```php
// soft delete model
$model->remove();

// delete soft-deleted model from database
$model->forceDelete();

// restore soft-deleted model
$model->restore();

// call SoftDelete::remove()
$model->delete();
```