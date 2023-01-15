# About

Zero-shot image classification and semantic image search using CLIP and Unsplash images.

# Setup

```
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

# Unsplash Dataset
`1k-compressed` (~42M) is included in this repo. `1k` (~8.45G) and `5k-compressed` (~213M) will be shared on Kaggle.

- use `unsplash-downloader.ipynb` to download ~ 9000 images
- use `unsplash-1k-5k.ipynb` to select 1k and 5k images
- use `unsplash-img-compression.ipynb` to resize and compress the images (~200 times smaller after resizing and compression: 1K 8.45G --> 42M, 5K 43.38G --> 213M)

# MPS vs. CPU

I did some tests with CLIP encoding 1k original unsplash images. MPS is actually slower than CPU. See related discussions [here](https://github.com/pytorch/pytorch/issues/77799)

For 1k:
- batch 100: 5m 12.2s with m1 mps vs. 4m 51.4s cpu
- batch 500: 4m 54.5s with m1 mps vs. 4m 51.7s cpu
- batch 1000: 4m 54.1s with m1 mps vs. 4m 57.1s cpu

For 5k:
- batch 1000: 4m 54.1s with m1 mps vs. 4m 57.1s cpu now

# References

- https://medium.com/@JettChenT/image-classification-with-openai-clip-3ab5f1c23e35
- https://towardsdatascience.com/clip-the-most-influential-ai-model-from-openai-and-how-to-use-it-f8ee408958b1
- https://github.com/haltakov/natural-language-image-search
- https://huggingface.co/docs/transformers/model_doc/clip 