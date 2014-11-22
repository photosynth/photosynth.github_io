Website presenting the PhotosynthViewer package available at: https://github.com/photosynth/PhotosynthViewer

How to generate this content?
-----------------------------

copy everything from the web folder of https://github.com/photosynth/PhotosynthViewer into this folder
copy utils/AnnotationStorage/dump/*.json from https://github.com/photosynth/PhotosynthViewer into synths/
edit js/embedScripts.js:
	- run grunt build from your local repo of https://github.com/photosynth/PhotosynthViewer then copy the build folder at the root.
	- set _useStaticStorage to true
	- change _staticStoragePrefix to "synths/"
	- override _useCompileJS to true by adding the following line:
		_useCompileJS = true; //just before the 'if (_useCompileJS)' test
	- provide a bing map key:
		var _bingMapKey = 'ArNMeVPrTEWs-raRBo8iJCBCiQNwWCRHOrJnuXekWu2EteapRA2fVBvMo_THeiqu';
	- change the path of minified css/js to match the location of your local build:

		if (_useCompileJS) {
			_pathToWorkerParser = "build/js/PS2PacketPlayer.worker.min.js";

			document.write('<link rel="stylesheet" type="text/css" href="build/css/PS2PacketPlayer.min.css" />');

			document.write('<script type="text/javascript" src="build/js/PS2PacketPlayer.min.js"></script>');
			document.write('<script type="text/javascript" src="build/js/PS2API.min.js"></script>');
		}
