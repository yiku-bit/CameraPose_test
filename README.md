# CameraPose_test
Test the multi-view camera pose generation.

Conda env: use the same packages as gaussian-splatting.

Put the pretrained chair ply file in this folder:
`output/chair_initial/point_cloud/iteration_30000`

Six-view images generated by Zero123++:
`data/chair_6views/train`

Camera pose file:
`data/chair_6views/transforms_train.json`

To validate the correction of camera pose, finetune pre-trained gaussian:

``python train.py --iterations 5000 -s data/chair_6views -m output/chair_initial --finetuning True``

The output will be in this folder: `output/chair_initial/finetuned`

To render the finetuned gaussian, first move the finetuned model folder (`output/chair_initial/finetuned/iteration_5000`) from `output/chair_initial/finetuned` to `output/chair_initial/output`, then run:

``python render.py -m output/lego_initial --iteration 5000``

To render the initial gaussian, run:

``python render.py -m output/lego_initial --iteration 30000``

Then the render images will be in:
`output/chair_initial/train/ours_5000/renders`
