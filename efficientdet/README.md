# EfficientDet

```zsh
#Clone EfficientDet git repo
git clone https://github.com/google/automl.git
cd ~/automl/efficientdet

#Install all the EfficientDet requirements
pip install -r requirements.txt

#Download the pretrained weights. Bold d0 represent the model version and can be in the range d0-d7.
wget https://storage.googleapis.com/cloud-tpu-checkpoints/efficientdet/coco/efficientdet-d0.tar.gz
tar zxf efficientdet-d0.tar.gz
mkdir -p ./savedmodels/efficientdet-d0

# Export saved model.
python model_inspect.py --runmode=saved_model --model_name=efficientdet-d0 --ckpt_path=./efficientdet-d0 --hparams="image_size=1920x1280" --saved_model_dir=./savedmodels/efficientdet-d0

#Make output dir and do inferencing with the saved model
mkdir -p outdir
python model_inspect.py --runmode=saved_model_infer --model_name=efficientdet-d0 --saved_model_dir=./savedmodels/efficientdet-d0 --input_image=../Images/railway_crossing_8.jpg --output_image_dir=./output --min_score_thresh=0.55
```