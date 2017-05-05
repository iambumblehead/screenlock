screenlock
==========

```javascript
// https://developer.mozilla.org/en-US/docs/Web/API/Screen/orientation

const screenlock = module.exports = (o => {

  let orientation = typeof screen === 'object'
        && (screen.orientation ||
            screen.mozOrientation ||
            screen.msOrientation);

  return {
    lock : (type='landscape-primary') => {
      if (orientation && orientation.lock) {
        try {
          orientation.lock(type);
        } catch (e) {}
      }
    },

    unlock : () => {
      if (orientation && orientation.unlock) {
        try {
          orientation.unlock();
        } catch (e) {}
      }
    }
  };

  
})({});
```
