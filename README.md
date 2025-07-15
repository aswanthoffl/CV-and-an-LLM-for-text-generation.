
# Image Captioning + LLM Response Generator

This project combines image captioning with CLIP Interrogator and large language models (LLMs) to generate meaningful responses based on an image and a user prompt. It uses a two-step pipeline:

1. Describe the image using the CLIP Interrogator.
2. Use a language model to answer a user's query based on that description.

---

## 🔧 Requirements

Install the necessary dependencies using:

```bash
pip install clip_interrogator open_clip_torch gradio transformers
```

---

## 📦 Models Used

* **CLIP Interrogator** (`ViT-L-14/openai`) for extracting semantic image descriptions
* **BLIP Large** as the caption model
* **Falcon-7B Instruct** LLM (`tiiuae/falcon-7b-instruct`) via Hugging Face Transformers for generating responses

---

## 🚀 How It Works

The core function is `generate_response(image, mode, user_prompt)`:

1. Takes an input image.
2. Extracts a caption using one of the CLIP Interrogator modes: `best`, `classic`, `fast`, or `negative`.
3. Constructs a prompt with that caption.
4. Sends it to the Falcon-7B LLM to generate a natural language response.

---

## 🧠 Modes of Captioning

* `best`: Most descriptive caption
* `classic`: Balanced between speed and quality
* `fast`: Quicker, less detailed
* `negative`: Extracts what the image is **not** about

---

## 💡 Example Prompt

```python
image_description, response = generate_response(image, mode="best", user_prompt="What might be happening in this photo?")
print("Caption:", image_description)
print("Response:", response)
```

---

## 📌 Notes

* Make sure your image is in RGB format before passing it.
* Model loading may require a GPU for best performance.
* The Falcon-7B model is large, ensure you have enough memory.


