### 3.1.0

 * `bundle` command has a `--force-r90` flag to make it easier to test code to
   handle images rotated 90 degrees.
 * add `rucksack_bundle_open_read_mem` API for reading a rucksack bundle from
   memory.

### 3.0.2

 * build: use mkdir in a way that works with mingw
 * build: detect if glob support is available
 * build: add missing library dependency

### 3.0.1

 * librucksack supports deleting entries
 * add `rm` command to delete entries
 * librucksack is now two libraries: librucksack and librucksackspritesheet.
   librucksack does not depend on FreeImage. Users will typically only need
   to link against librucksack.
 * add `unpack` command
 * `bundle` command deletes entries no longer found in manifest file

### 3.0.0

(redacted)

### 2.3.2

 * add `#define NDEBUG` to tests to make tests build more portably

### 2.3.1

 * avoid `strdup` and `strndup` for better portability

### 2.3.0

 * fix incorrect error value for read-only file not found
 * fix errors leaving bundle file in invalid state
 * `--dep` feature: globbing adds dependency on directory timestamp
 * support path lengths up to 4096 bytes
 * add API to get the length of an entry key: `rucksack_file_name_size`
 * fix joining an empty path with the current working directory
 * add `strip` command to make a bundle as small as possible.
 * fix several bugs that could result in an invalid bundle

### 2.2.0

 * ability to open bundle read-only
 * read-only commands do not create empty bundles when files do not exist

### 2.1.1

 * fix segfault when not using `--deps` option

### 2.1.0

 * `bundle` command takes a new parameter `--deps` to create a .d
   (makefile format) dependencies file

### 2.0.1

 * fix incorrect fixed point length (16384 instead of 10000)

### 2.0.0

 * ability to open a rucksack bundle which is a 0 byte empty file.
 * added a setting which allows preventing rotating images 90 degrees.
 * ability to glob for images in a texture.
 * fix not updating bundle when texture properties or image anchor position
   changed in manifest json
 * fix 2 bugs causing crash when adding or updating file in bundle
 * cat command: generate JSON data for textures
 * library: fix explicit anchor using bogus values
 * bundle command: fix explicit anchor using bogus values
 * use width/height for anchor position right/bottom instead of width-1/height-1
 * (API breaking) rename all `page` functions to `texture`.
 * (API breaking) rucksack_texture_close removed. Use rucksack_texture_destroy
   instead.
 * (API breaking) remove `RuckSackImage` property `name` in favor of `key`,
   `key_size`, and `path`.
 * (format breaking) update bundle format
   - include bundle version number
   - texture header includes UUID to identify it as a texture
   - texture header includes the properties that were used to generate it
   - image header includes anchor position
   - image header uses only 1 byte for the r90 boolean
 * (API breaking) add rucksack_image_create and rucksack_image_destroy.
   RuckSackImage struct size no longer part of ABI.
   - now you can set image->key and ignore image->key_size if you have a null-
     terminated string.
 * (API breaking) key and key_size are passed in via RuckSackTexture struct
   instead of separate arguments to rucksack_file_open_texture
 * (API breaking) all API that deals with keys now has a key_size parameter. All
   keys are arrays of bytes with a length, and keys may have null bytes in them.
 * (API breaking) anchor_x and anchor_y are floats instead of ints

### 1.0.1

 * Update docs and add changelog

### 1.0.0

 * Initial release.
