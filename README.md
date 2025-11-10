<div align="center">
<h1>Liquid: Language Models are Scalable and Unified <br> Multi-modal Generators</h1>

[**Junfeng Wu**](https://wjf5203.github.io/)<sup>1,2</sup> · [**Yi Jiang**](https://enjoyyi.github.io/)<sup>2&dagger;</sup> · [**Chuofan Ma**](https://machuofan.github.io/)<sup>2,3</sup>
<br>
[**Yuliang Liu**](https://openreview.net/profile?id=~Yuliang_Liu2)<sup>1</sup> · [**Hengshuang Zhao**](https://hszhao.github.io/)<sup>3</sup>
<br>
[**Zehuan Yuan**](https://shallowyuan.github.io/)<sup>2</sup> · [**Song Bai**](https://songbai.site/)<sup>2*</sup> · [**Xiang Bai**](http://vlrlab.aia.hust.edu.cn/)<sup>1*</sup>

<sup>1</sup>HUST&emsp;&emsp;&emsp;<sup>2</sup>ByteDance&emsp;&emsp;&emsp;<sup>3</sup>HKU
<br>
&dagger;project lead&emsp;&emsp;&emsp;*corresponding author

<a href="https://arxiv.org/abs/2412.04332"><img src='https://img.shields.io/badge/arXiv-Liquid-red' alt='Paper PDF'></a>
<a href="https://foundationvision.github.io/Liquid/"><img src='https://img.shields.io/badge/Project_Page-Liquid-green' alt='Project Page'></a>
<a href="https://huggingface.co/Junfeng5/Liquid_V1_7B"><img src='https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Model-blue'></a>
<a href="https://huggingface.co/spaces/Junfeng5/Liquid_demo"><img src='https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-Demo-red'></a>


</div>

<font size="4">This repo implements Liquid, a scalable and unified autoregressive generation paradigm that seamlessly integrates multimodal comprehension and generation.</font>

![teaser](assets/liquid_framework.png)

## 📰 News

**2025-03-25:** Data processing and model pretraining scripts have been updated in [Data.md](./Data.md) and [TRAIN.md](./TRAIN.md).

**2025-03-04:** Text-to-image and visual understanding evaluation scripts for Liquid are released in [EVAL.md](evaluation/EVAL.md).

**2025-02-28:** Paper, demo, model, and [project page](https://foundationvision.github.io/Liquid/) for Liquid are all released.

## 📑 Open-Source Plan
- Liquid-7B-IT (Instruction Tuned Multimodal Model with Instruction Following Ability)
  - [✅] Web Demo
  - [✅] Evaluation 
  - [✅] Checkpoints
  - [✅] Training Codes
- Liquid-0.5B~32B-Pretrain (Multimodal extension models of six different scales ranging from 0.5B to 32B across three model families. )
  - [ ] Checkpoints

# 📽️Inference

Using Liquid for inference or evaluation doesn't require complex environment dependencies. Since it's essentially a HuggingFace format language model, you only need the `transformers` library and some basic components to run it. Refer to [EVAL.md](evaluation/EVAL.md) for recommended versions.

### Run the Gradio Demo locally

If deploying on a GPU with less than 30GB VRAM, you may need to enable `load_in_8bit` in `AutoModelForCausalLM.from_pretrained` in `app.py` for image generation to avoid out-of-memory errors.

```bash
pip install gradio==4.44.1
pip install gradio_client==1.3.0

cd evaluation
python app.py
```

### Single inference

```bash
# Engage in pure language dialogue.

python inference_t2t.py  --model_path Junfeng5/Liquid_V1_7B  --prompt  "Write me a poem about Machine Learning."


# image understanding
python inference_i2t.py --model_path Junfeng5/Liquid_V1_7B  --image_path samples/baklava.png   --prompt 'How to make this pastry?'


# image generation, add --load_8bit for GPU with less than 30GB VRAM
python inference_t2i.py   --model_path Junfeng5/Liquid_V1_7B --prompt "young blue dragon with horn lightning in the style of dd fantasy full body"  
```



## ⚙️ Installation and Training

See [Data.md](./Data.md) and [TRAIN.md](./TRAIN.md).




## 📖 Introduction
* We present Liquid, an auto-regressive generation paradigm that **seamlessly integrates visual comprehension and generation.**

* Unlike previous multimodal large language model (MLLM), Liquid achieves this integration using a single large language model (LLM), eliminating the need for external pretrained visual embeddings such as CLIP. 

* For the first time, Liquid uncovers a **scaling law** that performance drop unavoidably brought by the unified training of visual and language tasks diminishes as the model size increases.

* Furthermore, the unified token space enables visual generation and comprehension tasks to **mutually enhance each other**


## 🔥 Multimodal Generation
* <font size="4">Liquid : Scalable and Versatile Unified Multimodal Generator which supports Visual Understanding, Visual Generation and Multi-modal Generation</font>

![teaser](assets/multimodal_task.png)


* <font size="4">Liquid can generate high-quality, photorealistic images of any aspect ratio by language in an autoregressive paradigm.</font>

![teaser](assets/samples_multiratio.jpg)

## 🔥 Scaling Law for multimodal generation
* <font size="4">Liquid shows clear Scaling Law in multimodal generation across different sizes(0.5B to 32B).</font>

![teaser](assets/multimodal_scaling_law.png)


## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Citation

If you find this project useful, please consider citing:

```bibtex
@article{liquid,
  title={Liquid: Language models are scalable and unified multi-modal generators},
  author={Wu, Junfeng and Jiang, Yi and Ma, Chuofan and Liu, Yuliang and Zhao, Hengshuang and Yuan, Zehuan and Bai, Song and Bai, Xiang},
  journal={International Journal of Computer Vision},
  year={2025}
}

```

