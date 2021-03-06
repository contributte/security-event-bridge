# Event Dispatcher > Nette Security Bridge

## Content :gift:

- [Usage - how to register](#usage-tada)
- [Bridge - nette application](#bridge-wrench)
- [Command - example command](#subscriber-bulb)

## Usage :tada:

```neon
extensions:
	events: Contributte\EventDispatcher\DI\EventDispatcherExtension
	events2security: Contributte\Events\Bridges\Security\DI\EventSecurityBridgeExtension
```

## Bridge :wrench:

There are several Nette Security events on which you can listen to.

```php
use Contributte\Events\Bridges\Security\Event\LoggedInEvent;
use Contributte\Events\Bridges\Security\Event\LoggedOutEvent;
```

- `LoggedInEvent::NAME` && `SecurityEvents::ON_LOGGED_IN`
- `LoggedOutEvent::NAME` && `SecurityEvents::ON_LOGGED_OUT`

## Subscriber :bulb:

```php
use Contributte\EventDispatcher\EventSubscriber;
use Contributte\Events\Bridges\Security\Event\LoggedInEvent;
use Contributte\Events\Bridges\Security\Event\SecurityEvents;

final class LoggedInSubscriber implements EventSubscriber
{

	/**
	 * @return array
	 */
	public static function getSubscribedEvents()
	{
		return [SecurityEvents::ON_LOGGED_IN => 'onLoggedIn'];
	}

	/**
	 * @param LoggedInEvent $event
	 * @return void
	 */
	public function onLoggedIn(LoggedInEvent $event)
	{
		// do magic
	}

}
```
