esperecyan/webdav-server-for-local-client
=========================================
This is a simple WebDAV server running on Docker.

I created this to allow access to the local file system from WebExtensions, etc.

Usage
-----
1. Install [Docker Desktop] if not already installed.
1. [Download this repository](https://github.com/esperecyan/webdav-server-for-local-client/archive/refs/heads/master.zip).
1. Unzip it to anywhere (* Do not change the place after launching by the subsequent steps.)
1. Copy `.env.example` as `.env`.
1.
	- To allow the client to write to the folder, set `PROPFIND GET MKCOL PUT DELETE` to `METHOD`.
	- To allow `depth: Infinity` (all files and directories, including subdirectories under the specified directory, to be retrieved at once), set `DEPTH_INFINITY` to `On`.
	- Set `PORT` to any integer between 49152 and 65535.
	- Set `URL_PATH` to a random alphanumeric string beginning with `/`. (to prevent access from clients other than the intended client)
	- Set `ROOT_PATH` to the folder path to read/write to.
1. `docker-compose up --detach`
1. The root folder URL of the WebDAV server is `http://localhost:integer_set_to_PORT/random_alphanumeric_string_set_to_URL_PATH/`.
1. Since the server are started automatically, if you want to stop the automatic startup and delete it, `docker-compose down`, or DELETE from the Docker Desktop UI.

[Docker Desktop]: https://www.docker.com/get-started/

Licence
-------
Licensed under the [Mozilla Public License Version 2.0] \(MPL-2.0).

[Mozilla Public License Version 2.0]: https://www.mozilla.org/MPL/2.0/
