---
title: 3 Reasons Your First Programming Job Should be at a Startup
tags: [typescript, javascript, rxjs]
date: 2018-12-30T05:25:44.226Z
path: blog/first-programming-job-startup
cover: ./preview.png
excerpt: Find out the 3 reasons why your first job should be at a startup.
---

Observables are lazy Push collections of multiple values. They fill the missing spot in the following table:

| | Single | Multiple |
| --- | --- | --- |
| **Pull** | [`Function`](https://developer.mozilla.org/en-US/docs/Glossary/Function) | [`Iterator`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Iteration_protocols) |
| **Push** | [`Promise`](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/Promise.jsm/Promise) | [`Observable`](../class/es6/Observable.js~Observable.html) |

**Example.** The following is an Observable that pushes the values `1`, `2`, `3` immediately (synchronously) when subscribed, and the value `4` after one second has passed since the subscribe call, then completes:

```typescript
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  setTimeout(() => {
    subscriber.next(4);
    subscriber.complete();
  }, 1000);
});
```

To invoke the Observable and see these values, we need to *subscribe* to it:

```typescript
import { Observable } from 'rxjs';

const observable = new Observable(subscriber => {
  subscriber.next(1);
  subscriber.next(2);
  subscriber.next(3);
  setTimeout(() => {
    subscriber.next(4);
    subscriber.complete();
  }, 1000);
});

console.log('just before subscribe');
observable.subscribe({
  next(x) { console.log('got value ' + x); },
  error(err) { console.error('something wrong occurred: ' + err); },
  complete() { console.log('done'); },
});
console.log('just after subscribe');
```

Which executes as such on the console:

```none
just before subscribe
got value 1
got value 2
got value 3
just after subscribe
got value 4
done
```
