# deepstream-jetson
for gstreamer launch

gst-launch-1.0 filesrc location=~/sample_720p.mp4 ! decodebin !  queue ! nvvidconv ! nvcaffegie model-path="/home/nvidia/Model/ResNet_18/ResNet_18_threeClass_VGA_pruned.caffemodel" protofile-path="/home/nvidia/Model/ResNet_18/ResNet_18_threeClass_VGA_deploy_pruned.prototxt" model-cache="/home/nvidia/Model/ResNet_18/ResNet_18_threeClass_VGA_pruned.caffemodel_b2_fp16.cache" labelfile-path="/home/nvidia/Model/ResNet_18/labels.txt" net-stride=16 batch-size=2 roi-top-offset="0,0:1,0:2,0:" roi-bottom-offset="0,0:1,0:2,0:" detected-min-w-h="0,0,0:1,0,0:2,0,0" detected-max-w-h="0,1920,1080:1,100,1080:2,1920,1080:" interval=1 parse-func=4 net-scale-factor=0.0039215697906911373 class-thresh-params="0,0.200000,0.100000,3,0:1,0.200000,0.100000,3,0:2,0.200000,0.100000,3,0:" output-bbox-layer-name=Layer11_bbox output-coverage-layer-names=Layer11_cov ! queue ! nvtracker ! queue ! nvosd x-clock-offset=800 y-clock-offset=820 hw-blend-color-attr="3,1.000000,1.000000,0.000000:" ! queue ! nvoverlaysink sync=false enable-last-sample=false


https://developer.ridgerun.com/wiki/index.php?title=GstInference_and_NVIDIA_Deepstream_1.5_nvcaffegie#Building_the_demo
