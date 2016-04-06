Для сборки перейти в директорию mcr-v81
Скачать в эту директорию MCR_R2013a_glnxa64_installer.zip с оффициального сайта.
Выполнить команду docker build -t tgregory:mcr-v81 .

Перейти в директорию ../kamchatka-service
Скачать в эту директорию viirs-bin.tgz [Архив должен содержать одноимённую директорию в бинарниками viirs_detect, viirs_fit) 
Выполнить команду docker build -t tgregory:kamchatka-service .

Для запуска контейнер перейти в рабочую директорию
Создать директории output и watcher если они не существуют.
В директорию watcher переместить бинарный файл viirs-watcher
Выполнить команду:
docker run --restart=always -d -v $(pwd)/output:/output -v $(pwd)/watcher:/watcher -v /абсолютный/путь/до/директории/с/данными:/data tgregory:kamchatka-service

