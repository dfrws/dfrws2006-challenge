# dfrws2006-challenge
The results of existing file carving tools typically contain many false positives. An investigator must test each of the extracted files by opening them in an application that supports the file type. The goal of the DFRWS 2006 Forensics Challenge was to design and develop file carving algorithms that identify more files and reduce the number of false positives.

## Challenge Data
THE DATA SET for this challenge is a 50MB raw file. It has no file system, but it contains JPEG, ZIP, HTML, Text, and Microsoft Office files and fragments. The goal is to extract as many full JPEG, ZIP, HTML, Text, and Office files as possible from it. You can (and are encouraged to) develop tools to solve this challenge, but all source code must be released at the end of the challenge.

dfrws-2006-challenge.zip (ZIP of raw file, 41 MB)
MD5 of raw file: bd09d612fc8b3f92662b98f9456f2ada

## Submission Information
To submit your results, you must document the following for each extracted file:

- File type (JPG, ZIP, HTML, Text, or Office)
- File size (in bytes)
- MD5 hash
- Sectors from where the file was carved (assume 512-byte sectors)

You must also describe how the files were extracted and tested. This includes:

- The name and version of existing carving programs that were used.
- A description of algorithms you developed for the challenge.
- Working source code of tools you developed for the challenge.
- How the number of false positives was reduced.

## Challenge Organizers
- Brian Carrier
- Eoghan Casey
- Wietse Venema
