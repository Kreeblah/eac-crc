eac-crc
=======

# Description

A `bash` script to compute the CRC of audio files which Exact Audio Copy shows in its log files.  Supported files are any file type that `sox_ng` supports.

# Installation:

This script was written on macOS 26.4.1. It should work on any UNIX or UNIX-like system that has the following tools available:

    file
    sox_ng
	rhash

For most systems, `file` should be part of the normal installation, but the other dependencies are typically available as packages.

# Syntax:

For normal operation:

	eac-crc (filename audio) (optional file type sox_ng recognizes)

To only print the version number:

	eac-crc --version

# Examples:

To assess a well-formed FLAC file:

    eac-crc testfile.flac

To assess a well-formed WAV file:

    eac-crc testfile.wav

To assess an MP3 file `sox_ng` can't automatically recognize as an MP3 file:

    eac-crc testfile.mp3 mp3

# Output

Upon success, it prints the EAC CRC to stdout and nothing else. The CRC is computed by using `sox_ng` to feed the raw audio stream into without file headers or metadata into a standard CRC32 computation by `rhash`.

# Exit code

The exit code is zero upon success and non-zero upon failure.

Upon failure, the exit code of `sox_ng`, or `rhash` might be returned.
`sox_ng` is piped to `rhash` and the `bash` option `pipefail` is used to obtain the exit code. For determining which exit code is returned upon failure, read up the `pipefail` option.

# Version:

1.3

# License:

GPLv3
