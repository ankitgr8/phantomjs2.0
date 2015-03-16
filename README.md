# phantomjs2.0
phantomjs.exe from phantomjs 2.0 branch which includes the download feature of the phantomjs download_support branch by Vitallium


sample JS , on how to use the download API --


IMPORTANT - the script is exited on checking the status of the "onResourceReceived" callback.

var page = require('webpage').create();  
 page.onFileDownload = function(status){console.log('onFileDownload(' + status + ')'); return 'test.pdf'; }
 page.onResourceReceived = function(status){console.log('onResourceReceived(' + status.stage + ')'); if(status.stage === 'end'){phantom.exit(1);}}
 page.onResourceRequested = function(status){console.log('onResourceRequested(' + status + ')'); }
 page.onFileDownloadError = function(status){console.log('onFileDownloadError(' + status + ')');phantom.exit(1);}
 page.onLoadStarted = function(status){console.log('onLoadStarted(' + status + ')');}
 page.onLoadFinished = function(status){console.log('onLoadFinished(' + status + ')');}
 page.open('https://abc.com/test');
