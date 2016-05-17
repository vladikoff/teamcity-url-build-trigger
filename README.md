# TeamCity Url Build Trigger Plugin

> from [confluence.jetbrains.com/display/TW/Url+Build+Trigger](https://confluence.jetbrains.com/display/TW/Url+Build+Trigger)

> This is mirrored because the original page fails to download the file.

## General Info
Author
Victory Bedrosova

### License
Apache 2.0
Type
free, open-source

### Plugin Description
Adds a build to the build queue when the content returned by a specified URL changes.

### HTTP response processing

To improve performance, the trigger first tries to detect if the resource has changed by sending a HEAD request and reading the ETag header attribute.

Only if the server provides no ETag, the trigger sends a GET request and reads the returned content.
The returned content is ignored and the build is not triggered in case of error response status code (>= 300).

### FTP and FILE response processing
For these resources the trigger normally performs comparison by matching the type (file or directory), size and last modification.
A build is not triggered if the FTP server returns the code which is not a positive intermediate response (300 <= reply < 400)

### TeamCity Versions Compatibility
TeamCity 6.0 and above

### Installation
See the generic plugin install instructions.

### Plugin usage
Add a new trigger, specify a URL to be monitored for changes.
The supported URL format is

```<protocol>://[[<login>:<password>@]<host>[:<port>]]/<path_to_resource>```
