# Larastoned

#### A collection of advanced tricks in Laravel 5+


##### Collections
+ Array as a collection.
```php
$array = ['name' => 'No one', 'age' => 22];
$collection = collect($array);
```
+ Implode
```php
$collection->implode('first_name', ',');
```
+ List
```php
// returns collection of first_name values
$collection->lists('first_name');
```
+ Unions
```php
$collection->merge($collection1)->merge($collection2)->merge($collection3);
```
+ Lookaheads
```php
$collection = collect([1=>11, 5=>13, 12=>14, 21=>15])->getCachingIterator();
foreach ($collection as $key => $value) {
    dump($collection->current() . ':' . $collection->getInnerIterator()->current());
}   
// The $collection refers to the outer, CachingIterator, which starts empty (it's a cache, and nothing has been put there yet).
// The inner iterator is just an ArrayIterator.
// Each time it is called, it passes its value out to the cache.
// Therefore, the CachingIterator always seems to be "one behind" its inner object.
```
+ Wildcards
```php
// return titles for all posts
$titles = $posts->pluck('posts.*.title');
```
