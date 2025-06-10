# Image Generator

![Banner Image](banner.jpg)

## Purpose

This script generates images from text prompts using the GPT-4o model. It provides a command-line interface for specifying prompts, output filenames, and target dimensions.

## Installation

Before using the script, ensure you have the following:

1.  **Python 3.6 or higher:** If you don't have it, download and install it from the official Python website.
2.  **Required Python Packages:** Install the necessary packages using pip:

    ```bash
    pip install openai keyring Pillow requests
    ```
3.  **OpenAI API Key:** You need an OpenAI API key to use this script. If you don't have one, create an account on the OpenAI platform and generate an API key.
4.  **Store your API key:** Store your OpenAI API key securely using the `keyring` library:

    ```bash
    keyring set openai api-key
    ```
    You will be prompted to enter your API key.

## How to Use

The script is executed from the command line with the following general syntax:

```bash
python image_generator.py "your image prompt" [options]
```

### Arguments

*   `prompt` (required): The text prompt for generating the image. Enclose the prompt in double quotes.

### Options

*   `-f` or `--filename`: Output filename. If not specified, the script will generate a default filename in the format `generated_image_{number}.png`.
*   `-w` or `--width`: Target width of the final image in pixels. Must be used together with `--height`.
*   `-H` or `--height`: Target height of the final image in pixels. Must be used together with `--width`.

## Examples

1.  **Generate an image with a simple prompt:**

    ```bash
    python image_generator.py "a cat sitting on a table"
    ```

    This will generate an image based on the prompt and save it with a default filename.

2.  **Specify width and height:**

    ```bash
    python image_generator.py "sunset over mountains" --width 1920 --height 1080
    ```

    This generates an image with the specified dimensions. The script will map the requested dimensions to the closest supported size, generate the image, and then resize and crop to the exact dimensions.

3.  **Specify an output filename:**

    ```bash
    python image_generator.py "abstract art" --filename my_art.png
    ```

    This generates an image and saves it as `my_art.png`.

4.  **Use short options for width, height, and filename:**

    ```bash
    python image_generator.py "portrait of a robot" -w 800 -H 1200 -f robot.png
    ```

    This generates a portrait of a robot, resizes and crops to 800x1200, and saves the image as `robot.png`.

5.  **Generate a business logo design:**

    ```bash
    python image_generator.py "business logo design" --width 512 --height 512
    ```

    This generates a square image suitable for a logo.
