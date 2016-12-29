# I'm watching you

Observer pattern uses three actor classes. Subject, Observer and Client. Subject is an object having methods to attach and detach observers to a client object and notifies them automatically of any state changes, usually by calling one of their methods.

```php
<?php

interface Subject {
  public function attach($observable);
  public function dettach($index);
  public function notify();
}

interface Observer {
  public function handle();
}

class Login implements Subject {
  protected $observers = [];

  public function attach($observable) {
    if (is_array($observable)) {
      return $this->attachObservers($observable);
    }

    $this->observers[] = $observable;
  }

  public function detach($index) {
    unset($this->observers[$index]);
  }

  public function fire() {
    $this->notify();
  }

  public function notify() {
    foreach ($this->observers as $observer) {
      $observer->handle();
    }
  }

  private function attachObservers($observable) {
    foreach ($observable as $observer) {
      if ( ! $observable instanceof Observer) {
        throw new InvalidArgumentException();
      }
    }
  }
}

class EmailNotifier implements Observer {
  public function handle() {
    var_dump('notified by email');
  }
}

class Logger implements Observer {
  public function handle() {
    var_dump('logged the login')
  }
}

$login = new Login;

$login->attach([
  new EmailNotifier,
  new Logger
]);

$login->fire();
```

