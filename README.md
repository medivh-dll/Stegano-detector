# Steganography Detector

A web-based tool for analyzing images to detect potential steganographic data (hidden information embedded within images). This tool runs entirely in your browser with no data sent to any server.

## Overview

Steganography is the practice of hiding data within other data—most commonly, hiding text, files, or other images within image files. This detector uses multiple analytical techniques to identify statistical indicators that suggest an image may contain hidden data.

## Features

### Image Analysis
- **LSB (Least Significant Bit) Analysis**: Examines the least significant bits of image pixels to detect non-random patterns that may indicate hidden data
- **Entropy Calculation**: Measures the randomness and information density of pixel data
- **Color Distribution Analysis**: Analyzes the balance of RGB color channels to detect anomalies
- **Suspicious Pattern Detection**: Identifies non-random and repetitive patterns in LSB sequences
- **Hidden Data Capacity Estimation**: Calculates the theoretical maximum amount of data that could be hidden in the image

### Risk Assessment
The tool provides a risk level classification:
- **Low Risk**: Image appears natural with expected statistical properties
- **Medium Risk**: Detected some indicators of possible hidden data
- **High Risk**: Strong statistical indicators suggest the presence of hidden data

## How It Works

### Technical Analysis Methods

1. **LSB Percentage Analysis**
   - Counts the number of pixels where the least significant bit is set to 1
   - Compares against expected distribution (~50% for random images)
   - High deviation indicates potential data embedding

2. **Entropy Calculation**
   - Computes Shannon entropy of pixel byte values
   - Random images typically have entropy around 6.5-7.0
   - Elevated entropy (>7.5) suggests non-natural data distribution

3. **Color Balance Assessment**
   - Analyzes average values of R, G, and B channels
   - Calculates maximum difference between channels
   - Significant imbalances can indicate data modification

4. **Pattern Detection**
   - Examines LSB sequences for non-random distribution
   - Flags distributions outside 40-60% range for ones/zeros
   - Identifies repetitive bit patterns that suggest encoded data

## Installation & Usage

### Quick Start
Simply open `steganography_detector.html` in any modern web browser.

### Using the Tool
1. Click "Choose Image" to select an image file
2. The image preview will appear on the left
3. Click the "Analyze" button to begin analysis
4. Results will display on the right panel showing all metrics

### Browser Requirements
- Modern browser with HTML5 Canvas support
- Works with Chrome, Firefox, Safari, Edge
- No plugins or extensions required

## Interpreting Results

### Metrics Explained

**Dimensions**: Width and height of the image in pixels

**File Size**: Total size of the image file in kilobytes

**LSB Activity %**: Percentage of pixels with LSBs set to 1
- Natural images: ~50%
- >60% or <40%: Suspicious

**Entropy**: Shannon entropy value (0-8)
- Natural images: 6.5-7.0
- >7.5: Highly suspicious

**Color Balance**: Whether RGB channels have similar average values
- Balanced: <20 difference
- Unbalanced: ≥20 difference

**Suspicious Patterns**: Detected anomalies in LSB distribution
- None detected: Clean
- Non-random distribution: Flagged
- Repetitive patterns: Concerning

**Hidden Data Capacity**: Maximum bytes that could theoretically be hidden
- Calculated as: (width × height × 3 channels) / 8 bytes

**Risk Assessment**: Overall risk level based on all metrics

## Limitations

This tool provides statistical indicators only and cannot definitively prove the presence of steganographic data. Understanding these limitations is important:

- **Not All Hidden Data Uses LSB**: Other steganographic methods exist (DCT coefficients, spatial transformations, etc.)
- **Statistical Nature**: The analysis is probabilistic. Some natural images may show suspicious patterns
- **Format Dependent**: Analysis works best with uncompressed or lightly compressed images
- **JPEG Compression**: Highly compressed images may show higher entropy naturally
- **Natural Variation**: Some images naturally have non-uniform LSB distributions
- **Cannot Decrypt**: This tool cannot recover or decrypt hidden data, only indicate its likely presence

## Use Cases

- Security research and forensic analysis
- Detecting potential data exfiltration in organizational networks
- Academic research on steganography
- Network monitoring and threat detection
- Educational purposes for understanding image analysis

## Privacy & Security

- All processing occurs locally in your browser
- No image data is uploaded to any servers
- No cookies or tracking used
- Results are not stored or logged
- Safe to use with sensitive images

## Technical Details

### Supported Image Formats
- JPEG
- PNG
- GIF
- WebP
- BMP
- All formats supported by the HTML5 Canvas API

### Performance
- Analysis is performed on the full image resolution
- Processing time depends on image size
- Typically complete within seconds for standard images
- No external dependencies or libraries required

### Algorithm Complexity
- LSB Analysis: O(pixels)
- Entropy Calculation: O(bytes)
- Color Distribution: O(pixels)
- Pattern Detection: O(sample size, typically first 1000 bytes)

## Disclaimer

This tool is provided for educational and authorized security research purposes only. Users are responsible for complying with applicable laws regarding the use of this tool. Unauthorized access to computer systems is illegal.

## About Steganography

Steganography differs from cryptography:
- **Cryptography**: Makes data unreadable (uses encryption)
- **Steganography**: Hides data's existence (concealment)

Common steganographic methods:
- LSB (Least Significant Bit) embedding in images
- DCT (Discrete Cosine Transform) coefficient modification
- Spatial domain techniques
- Frequency domain techniques
- Microdots and other analog methods

## Future Enhancements

Potential additions for future versions:
- Support for additional steganographic detection methods
- Batch image processing
- Export analysis results
- Advanced pattern recognition
- Support for video file analysis
- Integration with forensic tools

## Contributing

Found a bug or have a suggestion? Feedback is welcome to improve detection accuracy and expand capabilities.

## License

This tool is provided as-is for educational and authorized security research purposes.

---

**Last Updated**: 2024
**Version**: 1.0
