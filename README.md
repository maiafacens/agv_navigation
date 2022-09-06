# agv_navigation

Pacote contendo arquivos necessários para mapeamento e simulação simultânea (SLAM). Projeto AGV.

- **Para fazer a simulação no gazebo aplicando as técnicas de SLAM será necessario criar uma workspace ou utilizar uma existente.**

```sh
$ mkdir -p catkin_ws/src
$ cd catkin_ws/src
```

- **Fazer o clone do repositório que contém o modelo URDF do robo bem como os scripts de inicialização. (obs: Inclua este repositório na workspace também).**

```sh
#Descrição do robô (URDF).
git clone https://github.com/maiafacens/agv_description.git
#Pacote AGV/SLAM
git clone https://github.com/maiafacens/agv_navigation.git
```

- **Compilar workspace.**

```sh
$ cd ..
$ catkin_make
$ source devel/setup.bash
```

- **Abra o gazebo carregando modelo URDF + mundo.**

```sh
$ roslaunch agv_description agv_house.launch 
```

- **Em um outro terminal abra o RVIZ.**

```sh
$ roslaunch agv_description display.launch 
```

- **Agora poderá optar por realizar o mapeamento do mundo utilizando o pacote gmmaping + teleop ou utilizar o mapa já feito que está presente neste repositório. Seguem os passos para mapeamento (OPCIONAL).**

```sh
#caso gmmaping ainda não tenha sido instalado poderá instalar com o seguinte comando 
#sudo apt-get install ros-melodic-slam-gmapping
$ rosrun gmapping slam_gmapping scan:=scan
#Em outro terminal rode o pacote de teleoperação 
#Instalação Teleop $sudo apt-get install ros-melodic-teleop-twist-keyboard
$ rosrun teleop_twist_keyboard teleop_twist_keyboard.py
#Para Salvar o mapa vá para o diretório maps e rode o seguinte comando
$ rosrun map_server map_saver -f house_map
```

- **Com o mapa gerado agora podemos rodar os ultimos comandos para carregar o mapa, se localizar no mapa e por fim navegar por ele**

```sh
$ roslaunch agv_navigation agv_navigation.launch
```

  Agora é com você ! Fique a vontade para navegar de forma totalmente autônoma pelo mapa criado utilizando o botao 2D nav goal. :stuck_out_tongue_closed_eyes::collision:

