# Deep-dreams
"Deep dream" is an image-filtering technique which consists of taking an image classification model, and running gradient ascent over an input image to try to maximize the activations of specific layers (and sometimes, specific units in specific layers) for this input. It produces hallucination-like visuals.
Process:

Load the original image.
Define a number of processing scales ("octaves"), from smallest to largest.
Resize the original image to the smallest scale.
For every scale, starting with the smallest (i.e. current one):
Run gradient ascent
Upscale image to the next scale
Reinject the detail that was lost at upscaling time
Stop when we are back to the original size. To obtain the detail lost during upscaling, we simply take the original image, shrink it down, upscale it, and compare the result to the (resized) original image.
