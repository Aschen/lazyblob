# LazyBlob

A LazyBlob is a replacement for the Blob class that allows to lazy read files in order to preserve memory.

It is a drop-in replacement for the Blob class, so you can use it as a Blob.

The main difference is the instantiation, which is done asynchronously using the `LazyBlob.create` method.

## Usage

```js
const lazyBlob = await LazyBlob.create("package.json");

await fetch("https://aschen.tech", { method: "POST", body: lazyBlob });
```

## API

`slice(start = 0, end = this.size): LazyBlob`

Returns a new instance of LazyBlob that is a slice of the current one.
The slice is inclusive of the start and exclusive of the end.
The slice method does not supports negative start/end.

`arrayBuffer(): Promise<ArrayBuffer>`

Read the part of the file delimited by the LazyBlob and returns it as an ArrayBuffer.

`text(): Promise<string>`

Read the part of the file delimited by the LazyBlob and returns it as a string.

`stream(): ReadableStream`

Returns a stream around the part of the file delimited by the LazyBlob.

## About

This was originally made for https://github.com/huggingface/huggingface.js with the help of Eliott C.