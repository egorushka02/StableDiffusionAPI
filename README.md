# Stable Diffusion LitAPI

This project implements a simple API for generating images using the Stable Diffusion model, wrapped in a LitAPI framework. The API allows you to send a text prompt and receive a generated image in response.

## Table of Contents

- [Overview](#overview)
- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Example](#example)
- [Dependencies](#dependencies)
- [License](#license)

## Overview

The `StableDiffusionLitAPI` class is a subclass of `LitAPI` and provides the following functionalities:

1. **Model Setup**: Loads the Stable Diffusion model and moves it to the specified device (e.g., GPU or CPU).
2. **Request Decoding**: Extracts the text prompt from the incoming request.
3. **Image Generation**: Uses the Stable Diffusion model to generate an image based on the provided prompt.
4. **Response Encoding**: Converts the generated image to a Base64-encoded string and returns it in the response.

## Installation

To set up the project, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. **Install the required dependencies**:
   ```bash
   pip install torch diffusers litserve
   ```

3. **Download the Stable Diffusion model**:
   The model is automatically downloaded when you run the script for the first time. Ensure you have the necessary permissions and internet access.

## Usage

To start the server, run the following command:

```bash
python stable_diffusion_litapi.py
```

By default, the server will run on port `8000`. You can change the port by modifying the `server.run(port=8000)` line in the script.

## API Endpoints

The API exposes a single endpoint that accepts a JSON request with the following structure:

```json
{
    "prompt": "A futuristic cityscape at sunset"
}
```

The server will respond with a JSON object containing the generated image encoded as a Base64 string:

```json
{
    "image": "iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO9TXL0Y4OHwAAAABJRU5ErkJggg=="
}
```

## Example

Here is an example of how to interact with the API using `curl`:

```bash
curl -X POST http://localhost:8000/predict -H "Content-Type: application/json" -d '{"prompt": "A futuristic cityscape at sunset"}'
```

The response will contain the Base64-encoded image.

## Dependencies

- **PyTorch**: For tensor operations and GPU acceleration.
- **Diffusers**: Provides the Stable Diffusion model pipeline.
- **LitServe**: A lightweight API framework used to serve the model.
- **Base64**: For encoding the image data.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

Feel free to modify and extend this project according to your needs. If you encounter any issues or have suggestions for improvements, please open an issue or submit a pull request.