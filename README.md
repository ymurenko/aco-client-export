## .ACO file export
This code will generate an .aco file on the client, without needing to use a filestream. The .aco format is used by Adobe Creative Cloud products such as Photoshop and Illustrator to store color swatches.

To create an octet-stream, the code uses an array of integers (with all text being converted to UTF-16 and pushed the array). A Uint16Array is created using the stream array, and its data buffer is used as the octet-stream. 

This code assumes the browser is little-endian, so all data needs to be converted to big-endian before pushing to the array. 

### Customizing

The names of each color are "colorN" by default, where N is the color's index in the array. In order to add custom names for each color, the length of the name + 1 must be put in front of the name in the stream (e.g. "red" is length 3, so the number 4 must lead the UTF-16 character codes for "red": 4 72 65 64)
