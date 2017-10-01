# image_recognition_transfer_learning 
https://www.youtube.com/watch?v=QfNvhPx5Px8  

1. Install docker  
http://docs.aws.amazon.com/AmazonECS/latest/developerguide/docker-basics.html#install_docker  

docker run -it gcr.io/tensorflow/tensorflow:latest-devel  
docker run -it -v /home/ec2-user/app/image_recognition_transfer_learning/tf_files:/tf_files/ gcr.io/tensorflow/tensorflow:latest-devel  

# retraining  
python tensorflow/examples/image_retraining/retrain.py \  
--bottleneck_dir=/tf_files/bottlenecks \  
--how_many_training_steps 500 \  
--model_dir=/tf_files/inception \  
--output_graph=/tf_files/retrained_graph.pb \  
--output_labels=/tf_files/retrained_labels.txt \  
--image_dir=/tf_files/star_wars

