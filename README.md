##Update on 2019.1.23
In-Ship Clothes Retrieval dataset and pretrained model are released!. The rank-1 result is 89.5 which is a litter bit higher than paper reported.

##Prepare dataset
    
    Create a directory to store reid datasets under this repo via
    ```bash
    cd reid
    mkdir data
    ```
    
    For market1501 dataset, 
    1. Download Market1501 dataset to `data/` from http://www.liangzheng.org/Project/project_reid.html
    2. Extract dataset and rename to `market1501`. The data structure would like:
    ```
    market1501/
        bounding_box_test/
        bounding_box_train/
        query/
    ```
    
    For CUHK03 dataset,
    1. Download CUHK03-NP dataset from https://github.com/zhunzhong07/person-re-ranking/tree/master/CUHK03-NP 
    2. Extract dataset and rename folers inside it to cuhk-detect and cuhk-label.

    For In-Shop Clothes dataset,
    1. Downlaod clothes dataset from http://virutalbuy-public.oss-cn-hangzhou.aliyuncs.com/share/bfe_models/clothes.tar
    2. Extract dataset and put it to `data/` folder.

## Evaluate Market1501
```bash
python3 main_reid.py train --save_dir='./pytorch-ckpt/market_bfe' --model_name=bfe --train_batch=32 --test_batch=32 --dataset=market1501 --pretrained_model='./pytorch-ckpt/market_bfe/944.pth.tar' --evaluate
```
## Evaluate CUHK03-Label
```bash
python3 main_reid.py train --save_dir='./pytorch-ckpt/cuhk_label_bfe' --model_name=bfe --train_batch=32 --test_batch=32 --dataset=cuhk-label  --pretrained_model='./pytorch-ckpt/cuhk_label_bfe/750.pth.tar' --evaluate
```
## Evaluate In-Shop clothes
```bash
python main_reid.py train --save_dir='./pytorch-ckpt/clothes_bfe' --model_name=bfe --pretrained_model='./pytorch-ckpt/clothes_bfe/clothes_895.pth.tar' --test_batch=32 --dataset=clothes --evaluate
```