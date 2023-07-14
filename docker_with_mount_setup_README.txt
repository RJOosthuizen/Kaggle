How to:
first pull tensorflow image from docker:
docker pull tensorflow/tensorflow:INSERT_VERSION_TAG_HERE-gpu-jupyter

create empty mount in docker and map to directory in your hard drive:
docker volume create VOLUME_NAME --opt device=HARD_DRIVE_LOCATION(no quotes) --opt type=none --opt o=bind --driver local
docker volume ls # check if volume created
docker volume inspect VOLUME_NAME # device property should be populated with your hard drive location
docker rm VOLUME_NAME # if you want to delete your volume

run docker image
docker run -it -v VOLUME_NAME:/tf -p 8888:8888 tensorflow/tensorflow:INSERT_VERSION_TAG_HERE-gpu-jupyter

verify
docker inspect INSTANCE # this is different from the image name
should see the created volume in the Mounts section
click on cli in dockerhub of the instance + click on browser link of the instance
use the token to log into jupyter (once off)
verify that a tensorflow-tutorials folder has been created in your local hard drive location
also if you add files either locally or in jupyter the other one should pick it up

create repo!