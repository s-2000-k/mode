  1. Клонировать и распаковать папку "mode" с проектом
2. установить библиотеки:
- установка pip-менеджера и виртуальной среды:
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
sudo apt update
sudo apt install python3-dev python3-pip
pip install --upgrade pip
sudo pip3 install -U virtualenv

- установка библиотек:
sudo apt-get install python-imageio
pip install imageio

sudo apt-get install python-matplotlib
pip install matplotlib

pip install scipy==1.1.0

3) запустить виртуальную среду:

source ./venv/bin/activate

4) Установить Tensorflow 1.1 и CUDA 10.2
- Tensorflow:
sudo pip3 install tensorflow==1.1

-CUDA 10.2: информация об установке по ссылке: https://developer.nvidia.com/cuda-downloads

5) Создаём в папке проекта папку "models"

6) Скачиваем предобученную модель:

sh ./utils/get_model.sh *** models
где *** - название модели (см. ниже)

7) Запускаем распознавание изображения в папке проекта:

python monodepth_simple.py --image_path *.jpg --checkpoint_path ./models/***
где * - название изображения; *** - название модели.
Список моделей:
model_kitti (Our main model trained on the **kitti** split)
model_eigen (Our main model trained on the **eigen** split)
model_cityscapes (Our main model trained on **cityscapes**)
model_city2kitti (`model_cityscapes` fine-tuned on **kitti**)
model_city2eigen (`model_cityscapes` fine-tuned on **eigen**)
model_kitti_stereo (Our stereo model trained on the **kitti** split for 12 epochs, make sure to use `--do_stereo` when using it)

