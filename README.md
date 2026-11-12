# XD Export Image Collector

A free, browser-based utility for collecting images from multiple Adobe XD export ZIP files and grouping them into **one downloadable ZIP archive**.

When assets are exported from Adobe XD, each asset may arrive in its own ZIP archive and may include multiple image variants. Instead of opening every archive and saving images one by one, add the ZIP files to this tool. It collects the `@2x` image files, shows you what it found, and packages the collected images into one folder inside a new ZIP file.

## What it does

- Accepts multiple ZIP files at once using drag-and-drop or the file picker.
- Searches inside nested ZIP files.
- Collects image files with `@2x` in the filename.
- If an archive has no `@2x` image, selects its largest image and clearly marks it for review.
- Shows image previews, source archive names, output filenames, and collection status.
- Prevents files with duplicate names from overwriting one another by adding suffixes such as `(2)` and `(3)`.
- Lets you remove individual results or clear the full list before downloading.
- Packages all collected images into a single ZIP containing your chosen output folder.
- Preserves the original image data; it does not resize, recompress, or convert images.
- Runs locally in your browser. The selected files are not uploaded to a server.

## How to use

1. Download or clone this repository.
2. Open `index.html` in a modern browser such as Chrome or Edge. No installation or build step is required.
3. Drag multiple Adobe XD export ZIP files onto the page, or click the upload area and select them.
4. Review the previews and status labels. Pay attention to any item marked **check**: it was selected as the largest image because no `@2x` filename was found.
5. Optionally change the output folder name.
6. Click **Download folder (.zip)**.
7. Extract the downloaded ZIP to access all collected images together.

## Output and file selection

- The tool selects every image in an input archive whose filename contains `@2x` (for example, `banner@2x.png`). If more than one matching image exists in an archive, all matching images are collected.
- If no `@2x` image exists, the largest image by file size is selected and marked for manual checking. This is a fallback, not a guarantee that the selected image is the correct high-resolution asset.
- If two collected images have the same filename, the tool adds a numbered suffix to keep both files.
- Results are sorted by source ZIP filename and then image filename.
- Supported image extensions: PNG, JPG/JPEG, GIF, SVG, and WebP.
- macOS metadata files such as `.DS_Store`, `._*`, and `__MACOSX` entries are ignored.

## Privacy

All processing happens in the browser using the files you select. This project does not contain an upload feature or send your images to a remote server. If you publish it using GitHub Pages, the page is hosted as a static website; image processing still takes place in each visitor's browser.

## Technology

- HTML, CSS, and JavaScript
- [JSZip 3.10.1](https://stuk.github.io/jszip/) for reading source ZIP files and creating the output ZIP
- JSZip is included in `index.html` so the tool can run without a separate dependency installation.

## Publish with GitHub Pages

1. Create a public GitHub repository named `xd-export-image-collector`.
2. Add `index.html`, `README.md`, `LICENSE`, and `THIRD_PARTY_NOTICES.md` to the repository root.
3. Open **Settings → Pages** in the repository.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Select the `main` branch and `/ (root)` folder, then save.
6. Wait for GitHub Pages to publish the site. The URL will appear in the Pages settings.

You can also use the tool locally by opening `index.html`; GitHub Pages is optional.

## License

The original project code is released under the MIT License. See [LICENSE](LICENSE).

Third-party libraries bundled in `index.html` retain their own licenses and notices. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

## Contributions and feedback

Issues and improvements are welcome. If you find an archive that the tool does not handle correctly, open an issue and include a description of the ZIP structure. Do not upload confidential or client-owned assets in a public issue.
