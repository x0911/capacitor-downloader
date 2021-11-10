# Capacitor v3 Downloader

Forked from [Capacitor Downloader](https://github.com/triniwiz/capacitor-downloader)

## Why this package?

This package was creating to handle Capacitor v3 updates, it's prefered to not use this package alone, but instead, use [capacitor-plugin-downloader](https://www.npmjs.com/package/capacitor-plugin-downloader)

So, When you install this package, install `capacitor-plugin-downloader` too.

## Installation

* `npm i https://github.com/x0911/capacitor-downloader.git capacitor-plugin-downloader`

## Usage 

```js
import { Downloader } from 'capacitor-downloader';
const downloader = new Downloader();
const data = await downloader.createDownload({
  url: 'https://wallpaperscraft.com/image/hulk_wolverine_x_men_marvel_comics_art_99032_3840x2400.jpg'
});
const imageDownloaderId = data.value;
downloader
  .start({ id: imageDownloaderId }, (progressData) => {
    console.log(`Progress : ${progressData.value}%`);
    console.log(`Current Size : ${progressData.currentSize}%`);
    console.log(`Total Size : ${progressData.totalSize}%`);
    console.log(`Download Speed in bytes : ${progressData.speed}%`);
  })
  .then((completed) => {
    console.log(`Image : ${completed.path}`);
  })
  .catch(error => {
    console.log(error.message);
  });
```

## Api

| Method                                   | Default | Type                         | Description                                           |
| ---------------------------------------- | ------- | ---------------------------- | ----------------------------------------------------- |
| createDownload(options: DownloadOptions) |         | `Promise<Options>`                     | Creates a download task it returns the id of the task |
| getStatus(options:Options)                    |         | `Promise<StatusCode>`                 | Gets the status of a download task.                   |
| start(options:Options, progress?: Function)   |         | `Promise<DownloadEventData>` | Starts a download task.                               |  |
| resume(options:Options)                       |         | `Promise<void>`                       | Resumes a download task.                              |
| cancel(options:Options)                       |         | `Promise<void>`                       | Cancels a download task.                              |
| pause(options:Options)                        |         | `Promise<void>`                       | Pauses a download task.                               |
| getPath(options:Options)                      |         | `Promise<void>`                       | Return the path of a download task.                   |
