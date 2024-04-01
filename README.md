# Обнаружение сорняков с помощью YOLOv8
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1EvAM8lyu-398niKv43aeogIHJdH77Zgl#scrollTo=602CvBUyX1x1)

## Описание

Этот код демонстрирует использование YOLOv8 для обнаружения сорняков на изображениях.

## Требования
- Python 3.7+
- pip
- Git
- wget
- ultralytics
- splitfolders

## Инструкции

1. Скачайте код:
    ```sh
    git clone https://github.com/user/repo.git
    cd repo
    ```

2. Скачайте и распакуйте датасет:
    ```python
    !wget "https://s3-ap-southeast-1.amazonaws.com/he-public-data/Weed_Detection5a431d7.zip"
    ``` 
    ```python
    !unzip '/content/Weed_Detection5a431d7.zip'
    ```

3. В вашем редакторе кода:

    ```python
    import zipfile
    # Определите путь к ZIP-файлу и папку назначения
    zip_file_path = r'C:\Users\......Weed_Detection5a431d7.zip'
    destination_folder = r'C:\Users\.... '
    # Распаковка файла
    with zipfile.ZipFile(zip_file_path, 'r') as zip_ref:
        zip_ref.extractall(destination_folder)
    ```

4. Установите необходимые библиотеки:
    ```sh
    !pip install ultralytics
    ```

5. Разделите датасет:
    ```python
    splitfolders.ratio('/content/data', 'output', seed=1337, ratio=(.7, .15, .15), group_prefix=None, move=False)
    ```

6. Обучите модель:
    ```python
    model = YOLO("yolov8n.pt")
    model.train(data=data_path, epochs=3)
    ```

7. Проверьте работу модели:
    ```python
    loaded_model = YOLO(model_path)
    for image in test_images[:3]:
        img_path = os.path.join('/content/output/test/images', image)
        result = loaded_model(img_path)
        result.show()
    ```

## Результаты

Код обучает модель YOLOv8 на датасете изображений сорняков. Обученная модель может затем использоваться для обнаружения сорняков на новых изображениях.

## Дополнительные сведения
- YOLOv8: [GitHub - ultralytics/ultralytics](https://github.com/ultralytics/ultralytics)
- Splitfolders: [PyPI - split-folders](https://pypi.org/project/split-folders/)

## Внимание
Этот код является примером и может быть доработан. Для достижения лучших результатов необходимо настроить параметры модели и обучающего процесса.
