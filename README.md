# NetBridge - NetBridge is used for making synchronous network (ajax) calls on web applications.

<h2>Usage</h2>

```
let instance = NetBridge.getInstance();

instance.addToRequestQueue({
    url: "https://swapi.co/api/people",
    method: "post",
    data: {
        userID: 2
    },
    queue: function () {
        console.log('comment', 'I am a post request and am waiting');
    },
    beforeSend: function () {
        console.log('comment', 'I am a post request and I ran beforeSend');
    },
    success: (data, status, xhr) => {
        console.log(data, status, xhr);
    }
});

instance.addToRequestQueue({
    url: "https://swapi.co/api/people/2",
    method: "get",
    queue: function () {
        console.log('comment', 'I am a get request and am waiting');
    },
    beforeSend: function () {
        console.log('comment', 'I am a get request and I ran beforeSend');
    },
    success: (data, status, xhr) => {
        console.log(data, status, xhr);
    }
});
```

> `NetBridge.getInstance()` returns a singleton from which you can use the `addToRequestQueue()` method
to queue up requests that are to be dispatched synchronously, making network calls easier on your browser.
