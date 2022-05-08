## Overview
The File Carving Challenge file contained 32 files (not including the embedded files, such as pictures in Word documents or the files inside of ZIP files). The 32 files were used to create 22 different scenarios, which are described in the next section. Each scenario was designed to test a specific situation that might occur in a real file system. For example, there were different scenarios for fragmented JPEG files with text in between and with random data in between.

The image file was initialized by creating a 50MB file with random data (using /dev/urandom). The files needed to create each scenario were found from the public domain on the Internet. They were copied into the image file at places that would create the needed scenarios and would make each scenario isolated (i.e. not using the same file for multiple scenarios). The data in between each scenario is random.

Note that one of the downsides of using public domain material was that some submissions found the fragmented files by locating the full file on the Internet and then searching the image file for the missing parts. Although, if we had created every file from scratch, then we may not have created a diverse set of different file types from different applications.

## Scenarios
The scenarios used for the challenge were organized into four categories, based on file type. Each category had one or more scenarios and each scenario was labeled with category number and a letter.

### Category 1 focused on HTML files with ASCII text:
1a) One HTML non-fragmented

1b) One HTML fragmented with a JPEG in between

1c) One HTML fragmented with Unicode text in between

1d) Two HTML files that are intertwined

### Category 2 focused on Microsoft Office documents:
2a) One Word file, non-fragmented

2b) One Word file, fragmented with 3 fragments and random data in between

2c) One Excel file fragmented with random data in between

2d) One Word file fragmented with a JPEG in between

2e) One Word file fragmented with text in between

### Category 3 focused on JPEG files:
3a) One JPEG non-fragmented

3b) One JPEG non-fragmented, larger than a typical default max file size

3c) One JPEG non-fragmented, but sector before it has 0xffd8 in the first two bytes

3d) One JPEG fragmented with text in between

3e) One JPEG fragmented with a Word document in between

3f) One JPEG fragmented with random data in between

3g) One JPEG fragmented with a JPEG in between

3h) Two JPEGs that are intertwined

3i) One JPEG non-fragmented that is REALLY big

3j) One JPEG fragmented with singe sector in between that starts with 0xffd9

### Category 4 focused on ZIP files:
4a) One ZIP file, non-fragmented

4b) One ZIP file fragmented with text in between

4c) One ZIP file fragmented with random data in between


## Image File Layout
Based on the scenarios described in the previous section, the following layout of files was created. Sector numbers start with 0 and each sector is 512 bytes.

Start Sector | End Sector | Scenario | Description
| --- | --- | --- | --- | 
9 | 44 | 1a | HTML, non-frag
2051 | 3050 | 2c | Excel, frag 1 of 2
3051 | 3071 | 2c | Random
3072 | 3770 | 	2c | Excel, frag 2 of 2
3868 | 4428	 | 3a | JPEG, non-frag
4436 | 4455	 | 1d | HTML 1, frag 1 of 2
4456 | 4485	 | 1d | HTML 2, frag 1 of 2
4486 | 4501	 | 1d | HTML 1, frag 2 of 2
4502 | 4556	 | 1d | HTML 2, frag 2 of 2
7964 | 8284	 | 2d | Word, Frag 1 of 2
8285 | 9473	 | 2d | JPEG, non-frag
9474 | 10031 | 2d | Word, Frag 2 of 2
11619 | 11822 | 3d | JPG, frag 1 of 2
11823 | 11848 | 3d | Text
11849 | 12017 | 3d | JPG, frag 2 of 2
12222 | 26116 | 3b | BIG JPEG
27496 | 27606 | 1b | HTML, frag 1 of 2
27607 | 27977 | 1b | JPEG
27978 | 28196 | 1b | HTML, frag 2 of 2
28244 | 	28245 | 1c | HTML, frag 1 of 2
28246 | 	28306 | 1c | Unicode text
28307 | 	28344 | 1c | HTML, frag 2 of 2
28439 | 	28726 | 4a | ZIP 1, non-frag
28729 | 	29528 | 4b | Zip, frag 1 of 2
29529 | 	29895 | 4b | 	HTML
29896 | 	31368	 | 4b | Zip, frag 2 of 2
31475 | 	31532	 | 3h | JPEG 1, Frag 1 of 2
31533 | 	31752	 | 3h | JPEG 2, Frag 1 of 2
31753 | 	31887	 | 3h | JPEG 1, Frag 2 of 2
31888 | 	32036	 | 3h | JPEG 2, Frag 2 of 2
32837 | 	33397	 | 2a | Word, non-frag
34288 | 	34306	 | 2e | Word, Frag 1 of 2
34307 | 	34412	 | 2e | Text, non-frag
34413	 | 36236	 | 2e | Word, Frag 2 of 2
36291 | 	36291	 | 3c | Sector with 0xffd8
36292	 | 36640	 | 3c | JPEG
36998 | 	37649	 | 2b | Word, frag 1 of 3
37650 | 37726	 | 2b | 	Random
37727 | 	39427	 | 2b | 	Word, frag 2 of 3
39428 | 	39476	 | 2b | 	Random
39477 | 	40380	 | 2b | 	Word, frag 3 of 3
40638 | 	41219	 | 3f | JPG, frag 1 of 2
41220	 | 41238	 | 3f | 	Random
41239 | 	41609	 | 3f | JPG, frag 2 of 2
41611 | 43433	 | 3g | JPEG 1, Frag 1 of 2
43434 | 44028	 | 3g | JPEG 2, non-frag
44029 | 44200	 | 3g	 | JPEG 1, Frag 2 of 2
45015 | 	45386	 | 4c	 | Zip, frag 1 of 2
45387 | 	45389	 | 4c | 	Random
45390 | 	45545	 | 4c	 | Zip, frag 2 of 2
45566 | 	45963	 | 3e	 | JPG, frag 1 of 2
45964 | 	46103	 | 3e | 	Office
46104 | 	46826	 | 3e | JPG, frag 2 of 2
46910 | 	94836	 | 3i | 	Really Big JPG
94846 | 	95628	 | 3j | 	JPEG , frag 1 of 2
95629 | 	95629	 | 3j | 	Sector with ffd9
95630	 | 96653	 | 3j | 	JPEG, frag 2 of 2

## Individual File Information

The information for each of the files can be found in the following table. The [individual files are also available for download](https://www.dropbox.com/s/aqdsxy0juetbcym/dfrws-2006-challenge-files.zip?dl=0) (35MB, ZIP file).

File Name	| MD5 Hash | Size (bytes)
| --- | --- | --- |
1a.html | eec87931b03e5a4a4ef8fd51109a1227 | 18147
1b.html | a80ee062aed8279304faae8f20f6d48e | 168527
1b.jpg | fe7e7ac67709f2d9c2483aa98c681b99 | 189534
1c.html | 045798407b927321326a547704e67831 | 20019
1c.txt | 616a6bbe915c3dbf51014fd76f55b0e3 | 30816
1d1.html | 8a1ac28fe7bd144b8230b38b284a3827 | 18426
1d2.html | 80e6b9221ef308ff1639fd19df036e34 | 43236
2a.doc | 0e52e75029e99cd2e9dcd0af271cf4a2 | 287232
2b.doc | 4a22f04b097920d11fff4e192e0667a4 | 1667584
2c.xls | 03d1deff4774c932358d3580a3bbae66 | 869888
2d.doc | 8d2a9a284e078805ada47db191f35244 | 450048
2d.jpg | 4efc6c572683878efd8f3404ddaded7b | 608703
2e.doc | d7ff92b8cc1c89c46a78288b9c673152 | 943616
2e.txt | 5a12ef9dba88a186ef18a5d349b28e37 | 53870
3a.jpg | daf4205574abd6919b10ca8be92d17a3 | 287186
3b.jpg | b070beae1606f67a342bc5f78c29c743 | 7113968
3c.jpg | 2fae8770cc013d22e9ea1c070f2f509b | 178659
3d.jpg | 7b07320709e0caa947663f5df3a0a390 | 190720
3d.txt | f800a46e18fafd309825c5ee84a654a2 | 12826
3e.doc	 | 109284cc5abddc83879a29785795fd75 | 	71680
3e.jpg | 2320fe9c41eaddb864a56c2ddc4dd186 | 573499
3f.jpg | f8c51e0688796b5d616f0e5d4a94d104 | 487473
3g1.jpg | 7cce072e518fd72484c97adb1b4be08e | 1021085
3g2.jpg | c0da37b3f1a07af790e6e9171cedc4d2 | 304413
3h1.jpg | db89684c177168036e274140ecf766a1 | 98354
3h2.jpg | 0915313e99af0f6bf13bc06bcd003113 | 188693
3i.jpg | db32b271506b2f4974791957627c61cc | 24538540
3j.jpg | 1a5a843000ef617af93a9cad645e3cdf | 924877
4a.zip | ebabde39ba44d38888dd82606980498a | 147150
4b.html | 643d159339bd2c9e7604e6fac8e7facc | 187795
4b.zip | 9a4c2d3a9bd203eb39c9f954a3c997e4 | 1163745
4c.zip | f940fcc37c82e8ff1431e5c3c061611e | 270181
