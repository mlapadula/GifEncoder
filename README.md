GifEncoder
==========

Android Gif Encoder

Given a sequence of bitmaps, encode them as an animated Gif. Based on several open-source libraries. Adapted for Android by Michael Lapadula.

# To Use
* Import the files `GifEncoder.java`, `LzwEncoder.java`, and `NeuQuant.java` into your project

# Example

```
public void encodeGif(List<Bitmap> bitmaps, File outFile) {
    try {
        GifEncoder gifEncoder = new GifEncoder();
        gifEncoder.start(outFile.getCanonicalPath());
        gifEncoder.setDelay(500); // 500ms between frames

        // Grab frames and encode them
        Iterator<Bitmap> iter = bitmaps.iterator();
        while (iter.hasNext()) {
            Bitmap bitmap = iter.next();
            gifEncoder.addFrame(bitmap);
        }

        // Make the gif
        gifEncoder.finish();

        // Add to gallery
        Uri picUri = Uri.fromFile(outFile);
        addToGallery(picUri);

    } catch (IOException err) {

    }
}
```