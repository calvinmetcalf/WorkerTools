# Worker tools

A collection of useful snipits for using workers including

* getPath(reletiveUrl) it returns an absolute url
* backgroundAjax(url,callback,after,notjson) creates a worker which downloads the specified url and then calls the callback with it, if after is specified then before sending it back the worker calls that function on the data, if notjson is false or undefined it's prased as json set it to true to get raw text.
* mapReduce(threads,incremental).map(mapFunc).reduce(reduceFunc).data(dataArray).callback(callbackFunction).fetch(latter?); performs multithread map reduce this needs more documentation.