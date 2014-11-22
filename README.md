# Photosynth Website
This github repo contains the website visible at <a href="http://photosynth.github.io">photosynth.github.io</a>.
This website is showing the capability of the <a href="https://github.com/photosynth/PhotosynthViewer">PhotosynthViewer OSS</a>.

## How to generate the content of this repo?
This information is only useful for the person in charge of this github repo (these are explanations on how to generate this static website from the PhotosynthViewer repo).

- copy everything from the web folder of https://github.com/photosynth/PhotosynthViewer into this folder
- copy utils/AnnotationStorage/dump/*.json from https://github.com/photosynth/PhotosynthViewer into synths/
- edit js/embedScripts.js:
	- run grunt build from your local repo of https://github.com/photosynth/PhotosynthViewer then copy the build folder at the root.
	- set _useStaticStorage to true
	- change _staticStoragePrefix to "synths/"
	- override _useCompileJS to true by adding the following line:
```
_useCompileJS = true; //just before the 'if (_useCompileJS)' test
```
	- provide a bing map key:
```
var _bingMapKey = 'ArNMeVPrTEWs-raRBo8iJCBCiQNwWCRHOrJnuXekWu2EteapRA2fVBvMo_THeiqu';
```
	- change the path of minified css/js to match the location of your local build:
```
if (_useCompileJS) {
	_pathToWorkerParser = "build/js/PS2PacketPlayer.worker.min.js";

	document.write('<link rel="stylesheet" type="text/css" href="build/css/PS2PacketPlayer.min.css" />');

	document.write('<script type="text/javascript" src="build/js/PS2PacketPlayer.min.js"></script>');
	document.write('<script type="text/javascript" src="build/js/PS2API.min.js"></script>');
}
```
