# Adapter

In software engineering, the adapter pattern is a software design pattern (also known as Wrapper, an alternative naming shared with the Decorator pattern) that allows the interface of an existing class to be used as another interface.

```php
<?php

interface BookInterface {
    public function open();
    public function turnPage();
}

interface eReader {
    public function turnOn();
    public function pressTheNextButton();
}

class Book implements BookInterface {
    public function open() { var_dump('opening the book'); }
    public function turnPage { var_dump('turning the page of the paper book'); }
}

Class Kindle implements eReaderInterface {
    public function turnOn() { var_dump('turning on the eReader'); }
    public function pressTheNextButton() { var_dump('pressing the next button'); }
}

class eReaderAdapter implements BookInterface {
    public function __construct(eReaderInterface $reader) {
        $this->reader = $reader;
    }

    public function open() { $this->reader->turnOn(); }
    public function turnPage() { $this->reader->pressTheNextButton(); }
}

class Person {
    public function read(BookInterface $book) {
        $book->open();
        $book->turnPage();
    }
}

(new Person)->read->(new eReaderAdapter(new Kindle));
```