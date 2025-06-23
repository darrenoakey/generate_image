![](banner.jpg)

# Image Generator

## Purpose

This script generates images using the GPT-4o native image generation model via the OpenAI API. It allows you to specify a text prompt, and optionally, the desired output filename, width, and height of the image.  If you specify a width and height, the script will request the closest supported aspect ratio from the API, and then resize and crop the image to your exact specified dimensions.

## Installation

1.  **Install Python:** Ensure you have Python 3 installed on your system.
2.  **Install Dependencies:**
    ```bash
    pip install openai keyring Pillow requests
    ```
3.  **Set OpenAI API Key:** Store your OpenAI API key securely using `keyring`:
    ```bash
    keyring set openai api-key
    ```
    You will be prompted to enter your API key.  This only needs to be done once.

## Usage

```bash
python image_generator.py <prompt> [options]
```

*   `<prompt>`: The text description of the image you want to generate. This should be enclosed in quotes if it contains spaces.
*   `[options]`: Optional arguments to customize the image generation.

### Options

*   `-f, --filename`:  Specify the output filename. If not provided, a default filename `generated_image_{number}.png` will be used.
*   `-w, --width`: Specify the target width of the image.
*   `--height`: Specify the target height of the image. 

    *Note: Both width and height must be specified together if you want to resize the image. GPT-4o supports specific sizes (1024x1024, 1024x1536, 1536x1024) which are mapped to your desired aspect ratio, then cropped to exact dimensions if specified.*


## Examples

1.  **Generate an image with a simple prompt:**

    ```bash
    python image_generator.py "a cat sitting on a table"
    ```

2.  **Generate an image with specified width and height:**

    ```bash
    python image_generator.py "sunset over mountains" --width 1920 --height 1080
    ```

3.  **Generate an image and save it with a custom filename:**

    ```bash
    python image_generator.py "abstract art" --filename my_art.png
    ```

4.  **Generate a portrait of a robot with specific dimensions and filename:**

    ```bash
    python image_generator.py "portrait of a robot" -w 800 --height 1200 -f robot.png
    ```

5.  **Generate a business logo design:**

    ```bash
    python image_generator.py "business logo design" --width 512 --height 512
    ```

## Transparency

Images may have transparency and are saved as PNG by default. Use a `.jpg` or `.jpeg` extension to force conversion to RGB with a white background.
