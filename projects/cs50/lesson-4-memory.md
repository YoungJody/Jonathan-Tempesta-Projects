# Lesson 4: Memory

Part of [CS50x](../cs50.md) · **Language:** C · **Topics:** pointers, dynamic memory, file I/O, binary data

## Volume
Changes the volume of a WAV audio file by a given factor. It copies the file's header unchanged, then scales every 16-bit audio sample.
**Practiced:** reading and writing binary files, fixed-width integer types.

## Filter (more comfortable)
Applies four filters to BMP images: grayscale, reflect, blur, and edge detection with the Sobel operator.
**Practiced:** 2D arrays of pixels, working from a copy of the image, convolution kernels, clamping values.

## Recover
Recovers deleted JPEG photos from a raw memory-card image. It reads the card in 512-byte blocks, detects each JPEG's signature, and writes every image to its own file.
**Practiced:** buffers, file signatures, pointers, generating file names.

---
Code kept private per CS50's academic honesty policy. · [← CS50x overview](../cs50.md)
