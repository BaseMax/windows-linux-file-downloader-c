# Windows/Linux File Downloader in C

A C program that demonstrates how to download a file over HTTP from a server using sockets. The program is cross-platform, working on both Windows and Linux systems.

## Features

- **Cross-platform support:** Works on both Windows and Linux.
- **Socket:** Uses sockets to connect to a server and download a file.
- **Minimal dependencies:** Only standard C libraries and platform-specific socket libraries are used.

## Requirements

### Windows

- GCC (MinGW or similar)
- Winsock2 library (comes with Windows)

### Linux

- GCC
- Standard POSIX libraries (usually included with most Linux distributions)

## Building the Project

### Windows

To build the program on Windows, use the following command:

```bash
gcc downloader.c -o downloader -g -Wextra -std=c11 -lws2_32
```

### Linux

To build the program on Linux, use the following command:

```bash
gcc downloader.c -o downloader -g -Walloca -Wextra -Wall -fsanitize=address,undefined -std=c11
```

## Usage

After compiling, you can run the program as follows:

```bash
./downloader
```

The program will connect to example.com and download the file located on remote server, saving it locally as `downloaded_file.log`.

### Customization

- **Hostname:** The hostname to connect to is currently set to example.com.
- **Path:** The path to the file on the server is set to /file.txt.
- **Port:** The port used for the connection is 80 (HTTP).

You can customize these values by modifying the following lines in downloader.c:

```c
const char *hostname = "example.com";
const char *path = "/file.txt";
const char *port = "80";
```

### Platform-Specific Notes

#### Windows

The program uses Winsock2 for socket communication. Ensure that Winsock2 is initialized using WSAStartup() before any socket operations and cleaned up using WSACleanup() after all operations are done.

#### Linux

The program uses POSIX-compliant socket functions and does not require any special initialization or cleanup beyond the normal opening and closing of sockets.

## Troubleshooting

- Socket Connection Issues: Ensure that the server you are trying to connect to is reachable and that the port is open.
- Compilation Errors: Make sure you are using GCC with the appropriate flags as described in the "Building the Project" section.
- File Writing Issues: Ensure that you have write permissions to the directory where the file will be saved.

### Author

Max Base

### License

This project is licensed under the GPL-3.0 License. See the LICENSE file for more details.

Copyright 2024, Max Base
