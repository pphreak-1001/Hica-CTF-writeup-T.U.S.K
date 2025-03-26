The file: Stego2_F.jpg has embedded files inside it:

Used binwalk to know this:
binwalk -v Stego2_F.jpg

Scan Time:     2025-03-26 03:58:35
Target File:   /sec/root/hicathon/Stego2_F.jpg
MD5 Checksum:  c45228f5f11195a32c0b42d364bddc37
Signatures:    436

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0             0x0             JPEG image data, JFIF standard 1.01
2587844       0x277CC4        Zip archive data, at least v2.0 to extract, compressed size: 120364, uncompressed size: 120364, name: image_0.png
2708249       0x295319        Zip archive data, at least v2.0 to extract, compressed size: 120364, uncompressed size: 120364, name: image_1.png
2828654       0x2B296E        Zip archive data, at least v2.0 to extract, compressed size: 120364, uncompressed size: 120364, name: image_2.png
2949059       0x2CFFC3        Zip archive data, at least v2.0 to extract, compressed size: 120430, uncompressed size: 120430, name: image_3.png
3069530       0x2ED65A        Zip archive data, at least v2.0 to extract, compressed size: 120364, uncompressed size: 120364, name: image_4.png
3189935       0x30ACAF        Zip archive data, at least v2.0 to extract, compressed size: 120365, uncompressed size: 120365, name: image_5.png
3310341       0x328305        Zip archive data, at least v2.0 to extract, compressed size: 120366, uncompressed size: 120366, name: image_6.png
3430748       0x34595C        Zip archive data, at least v2.0 to extract, compressed size: 120365, uncompressed size: 120365, name: image_7.png
3551154       0x362FB2        Zip archive data, at least v2.0 to extract, compressed size: 120364, uncompressed size: 120364, name: image_8.png
3671559       0x380607        Zip archive data, at least v2.0 to extract, compressed size: 120365, uncompressed size: 120365, name: image_9.png
3792535       0x39DE97        End of Zip archive, footer length: 22



Extracted all files:
Looked through all png files and found one file to have extra data chunk at the end:
exiftool *
======== 00005054.png
ExifTool Version Number         : 13.00
File Name                       : 00005054.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00005289.png
ExifTool Version Number         : 13.00
File Name                       : 00005289.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00005524.png
ExifTool Version Number         : 13.00
File Name                       : 00005524.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00005759.png
ExifTool Version Number         : 13.00
File Name                       : 00005759.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Warning                         : Invalid eXIf chunk
EX If                           : (Binary data 52 bytes, use -b option to extract)
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00005995.png
ExifTool Version Number         : 13.00
File Name                       : 00005995.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00006230.png
ExifTool Version Number         : 13.00
File Name                       : 00006230.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00006465.png
ExifTool Version Number         : 13.00
File Name                       : 00006465.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00006700.png
ExifTool Version Number         : 13.00
File Name                       : 00006700.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00006935.png
ExifTool Version Number         : 13.00
File Name                       : 00006935.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
======== 00007171.png
ExifTool Version Number         : 13.00
File Name                       : 00007171.png
Directory                       : .
File Size                       : 120 kB
File Modification Date/Time     : 2025:03:26 03:58:46+00:00
File Access Date/Time           : 2025:03:26 03:58:46+00:00
File Inode Change Date/Time     : 2025:03:26 03:58:46+00:00
File Permissions                : -rw-r--r--
File Type                       : PNG
File Type Extension             : png
MIME Type                       : image/png
Image Width                     : 200
Image Height                    : 200
Bit Depth                       : 8
Color Type                      : RGB
Compression                     : Deflate/Inflate
Filter                          : Adaptive
Interlace                       : Noninterlaced
Image Size                      : 200x200
Megapixels                      : 0.040
   10 image files read


Used exiftool -b to extract that data chunk:
exiftool -b 00005759.png
Warning: Invalid eXIf chunk - 00005759.png
13.0000005759.png.1204302025:03:26 03:58:46+00:002025:03:26 03:58:46+00:002025:03:26 03:58:46+00:00100644PNGPNGimage/png20020082000Invalid eXIf chunk!SElDQXtFWDFGXzFTX00wUjNfRzAwRH0=200 2000.04

Decoded the base64 string:
SElDQXtFWDFGXzFTX00wUjNfRzAwRH0=

FLag: HICA{EX1F_1S_M0R3_G00D}
