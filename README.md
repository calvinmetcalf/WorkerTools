# Worker tools

A collection of useful snipits for using workers including

* getPath(reletiveUrl) it returns an absolute url
* backgroundAjax(url,callback,after,notjson) creates a worker which downloads the specified url and then calls the callback with it, if after is specified then before sending it back the worker calls that function on the data, if notjson is false or undefined it's prased as json set it to true to get raw text.
* `mapReduce(threads,incremental).map(mapFunc).reduce(reduceFunc).data(dataArray).callback(callbackFunction).fetch(latter?).close();` performs multithread map reduce this needs more documentation.
```JavaScript
var mr=mapReduce(Number of map Threads,optional true for incremental);
//if incremental is false then goes through the data when you give it and then closes everythign and calls cb with the data
//other wise, see bellow
mr.map(map function).reduce(reducefunction);
mr.data(array of data)//this is where it will actually start doint stuff
mr.callback(callback function)
//if incremental is false then this is called with all the data is gone through
//if incremental is true you'll have to call fetch;
mr.fetch(true for latter);
//if just called as mr.fetch(); then imidiatly sends a message to the reducer to get the data, when it does the callback is called with it
//if later is true then it will wait for you to go through all your current data first.
```
* quickWorker(function, callback) creates a worker, when you call it's .send(data) method it sends that to the worker, and call the callback with the result, callback uses node conventions of callback(error, result);