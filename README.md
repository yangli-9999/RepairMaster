# RepairMaster

This repository provides an implementation of the method proposed in the paper **“Enhancing Automated Program Repair with Cross-fragment Information Fusion and Historical Fix RAG”**. For more information on data preprocessing, experimental design, and analysis of results, please refer to the relevant chapters in the paper for a more comprehensive understanding of the background and technical details of this research.


## Resources

* In the replication, we provide:
  * the scripts we used to:
    * `train.sh`: train models.
    * `infer.sh`:  inference models.
  * the source code we used to:
    * `train_model.py`: the main code for training/validating.
    * `test_model.py`: the main code for testing.
    * `src/`: the utils, model, data preprocessing, KG Construction etc.
    * `checkpoint_final`: Storing Results.
    * `CodeBert`: Storing CodeBert models downloaded from [huggingface](https://huggingface.co/).
    * `CodeT5`: Storing CodeT5 models downloaded from [huggingface](https://huggingface.co/).
    * `evaluator`: Toolkit for model evaluation.
    * `finetune`: the main code for structured domain fine-tuning.
    * `vulfix_data`: datasets and the main code for data processing.n. 
* `requirements.txt` contains the dependencies needed.
* If you meet OutOfMemoryError: please note that you typically need around 40GB GPU memory to run RepairMaster.
* [Here](https://drive.google.com/drive/folders/1GOCR4EvPp0AAipNJ0Zu_ggyTlnjyYyLB) is the full trained model, if you need to use it directly for inference. Please download it and place it in the '. /checkpoint_final/final_model/checkpoint/best_dev/' directory.
* [Here](https://drive.google.com/drive/folders/1tTr4z8oO40Vw_aIDTUSLanlU3W4PXz2T) is the fine-tuned CodeT5 model. Please download it and rename it to '. /finetune_with_ast/pytorch_model.bin' and put it in the root folder。
* [Here](https://drive.google.com/drive/folders/1dr4fcafpJH5vx3hLsTkwI2Zpoba1zqYJ) is the dataset megavul used to build the Knowledge Graph. please download it and place it in the '. /vulfix_data/KGKB/' directory.


## Install dependencies

 Please install them first.
```
unzip RepairMaster.zip
cd RepairMaster
conda create -n RepairMaster python=3.8 
conda activate RepairMaster
pip install -r requirements.txt
```
## Train and Test 

To replicate RepairMaster, ensure that `c_dataset/` is in the root path of this project. 

Training:
```
bash train.sh 
```

Testing:
```
bash test.sh
```

Compute metrics:

```
python calculate_metrics_all_models
```

## Pyhton scripts for creating knowledge graphs via noe4j
```
python src/noe4j_history_case.py
```

## Pyhton Scripts code for performing structured fine-tuning

```
python finetune/finetune.py
```

