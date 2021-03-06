# image_recognition_transfer_learning 
  https://www.youtube.com/watch?v=QfNvhPx5Px8  

1. Install docker  
  http://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html#install_docker  

2. Setup docker  
  `docker run -it gcr.io/tensorflow/tensorflow:latest-devel`  

3. Download images (use Fatkun batch download extension on google)
  Put images in this format: tf_files/star_wars/vader, tf_files/star_wars/darth_maul

3. Connect image files to docker (need at least 2 classes: tf_files/star_wars/vader, tf_files/star_wars/darth_maul)  
  `docker run -it -v /home/ec2-user/app/image_recognition_transfer_learning/tf_files:/tf_files/ gcr.io/tensorflow/tensorflow:latest-devel`  
4. Retraining  
  ```python
  python tensorflow/examples/image_retraining/retrain.py \  
  --bottleneck_dir=/tf_files/bottlenecks \  
  --how_many_training_steps 500 \  
  --model_dir=/tf_files/inception \  
  --output_graph=/tf_files/retrained_graph.pb \  
  --output_labels=/tf_files/retrained_labels.txt \  
  --image_dir=/tf_files/star_wars
  ```
  
5. Create label_image.py (load image and graph to tensorflow, get predictions)  
6. Use `python label_image.py <image_path.jpg>` command to predict image  

