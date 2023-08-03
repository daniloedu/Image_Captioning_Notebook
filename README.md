# H1 Image Captioning Notebook

# H2 Introduction

This notebook contains code to build an image captioning application using the Hugging Face Transformers library. It uses the Salesforce/blip-image-captioning-base model to generate captions for images. The application is built using the Gradio library, which allows us to create a user interface for the application easily.

# H2 Requirements

This application requires the following Python libraries:
1. `os`
2. `io`
3. `IPython.display`
4. `PIL (Pillow)`
5. `base64`
6. `dotenv`
7. `requests`
8. `json`
9. `transformers`
10. `gradio`

In addition to these libraries, you will also need to have a Hugging Face API key, which you can obtain by signing up on the Hugging Face website. This key should be stored in an environment variable named `HF_API_KEY`. Similarly, the endpoint for the Hugging Face API should be stored in an environment variable named `HF_API_ITT_BASE`.

# H2 Code Explanation

The code in this notebook is organized into several helper functions and a main section that sets up the Gradio interface.

# H3 Helper Functions
- `get_completion(inputs, parameters=None, ENDPOINT_URL=os.environ['HF_API_ITT_BASE'])`: This function sends a POST request to the Hugging Face API and returns the response as a Python dictionary. It accepts an inputs argument, which is the base64-encoded string of the image, and an optional parameters argument. The ENDPOINT_URL is retrieved from an environment variable.
- `get_completion = pipeline("image-to-text",model="Salesforce/blip-image-captioning-base")`: This line sets up a Hugging Face pipeline for image-to-text conversion using the Salesforce/blip-image-captioning-base model.
- `summarize(input)`: This function takes an input (a base64-encoded image string), passes it to the get_completion function, and returns the generated caption.
- `image_to_base64_str(pil_image)`: This function takes a PIL image as input and returns a base64-encoded string of the image.
- `captioner(image)`: This function takes a PIL image as input, converts it to a base64-encoded string, and then passes it to the get_completion function to generate a caption.

# H3 Gradio Interface
The main part of the notebook sets up a Gradio interface for the image captioning application. The `gr.Interface` function is used to create the interface. The `fn` argument is the function that is called when the user submits an image, inputs and outputs specify the types of the input and output, and `title` and `description` provide information that is displayed on the interface. The `allow_flagging` argument is set to "never" to disable the flagging feature. Finally, the `examples` argument provides a list of example images that the user can try.

The Gradio interface is launched with the `launch` method. The `share` argument is set to `True` to generate a public URL for the interface, and the `server_port` argument specifies the port to use for the server.
