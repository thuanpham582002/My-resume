# My Resume

This repository contains my professional resume in Markdown format with CSS styling.

## TL;DR

```bash
pandoc resume.md -s -c resume.css -o resume.html && wkhtmltopdf --enable-local-file-access --margin-top 10mm --margin-bottom 10mm --margin-left 10mm --margin-right 10mm --page-size A4 resume.html resume.pdf
```

## How to Export Resume to PDF

There are several methods to export the resume to PDF while preserving CSS styling:

### Method 1: Using wkhtmltopdf (Recommended)

This method provides the best CSS support and rendering quality.

1. **Install wkhtmltopdf**
   ```bash
   # On macOS
   brew install wkhtmltopdf

   # On Ubuntu/Debian
   sudo apt-get install wkhtmltopdf

   # On Windows
   # Download installer from https://wkhtmltopdf.org/downloads.html
   ```

2. **Convert Markdown to HTML with CSS**
   ```bash
   pandoc resume.md -s -c resume.css -o resume.html
   ```

3. **Convert HTML to PDF**
   ```bash
   wkhtmltopdf --enable-local-file-access resume.html resume.pdf
   ```

4. **One-line command combining steps 2 and 3**
   ```bash
   pandoc resume.md -s -c resume.css -o resume.html && wkhtmltopdf --enable-local-file-access resume.html resume.pdf
   ```

#### Additional wkhtmltopdf Options

You can customize the PDF output with various options:
```bash
wkhtmltopdf \
  --enable-local-file-access \
  --margin-top 10mm \
  --margin-bottom 10mm \
  --margin-left 10mm \
  --margin-right 10mm \
  --page-size A4 \
  resume.html resume.pdf
```

### Method 2: Using Pandoc with LaTeX

This method is an alternative if wkhtmltopdf is not available, but CSS support might be limited.

```bash
pandoc resume.md -c resume.css -s -o resume.pdf --pdf-engine=xelatex -V mainfont="Arial Unicode MS" -V geometry:margin=1in
```

### Method 3: Using Browser

1. Open `resume.html` in a web browser
2. Press `Cmd/Ctrl + P` to open Print dialog
3. Select "Save as PDF"
4. Adjust margins and other settings as needed

### Quick Build Command

One-line command to build the resume with proper formatting:
```bash
pandoc resume.md -s -c resume.css -o resume.html && wkhtmltopdf --enable-local-file-access --margin-top 10mm --margin-bottom 10mm --margin-left 10mm --margin-right 10mm --page-size A4 resume.html resume.pdf
```

To make it easier to use, you can add an alias to your shell config (`.zshrc` or `.bashrc`):
```bash
alias build-resume='pandoc resume.md -s -c resume.css -o resume.html && wkhtmltopdf --enable-local-file-access --margin-top 10mm --margin-bottom 10mm --margin-left 10mm --margin-right 10mm --page-size A4 resume.html resume.pdf'
```

Then simply run:
```bash
build-resume
```

## File Structure

- `resume.md` - Resume content in Markdown format
- `resume.css` - CSS styling for the resume
- `resume.html` - Generated HTML file (intermediate)
- `resume.pdf` - Final PDF output

## Customization

- Edit `resume.md` to update the content
- Modify `resume.css` to change the styling
- Use the export methods above to generate updated PDF

## Notes

- The CSS file includes both screen and print media styles
- wkhtmltopdf method provides the best support for CSS features
- Make sure to have all required fonts installed when using the LaTeX method
