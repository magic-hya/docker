# docker

# ./install.sh lite -n 节点ID -m master节点ip端口 -t 令牌
bash install.sh lite -n hjxndwid -m 'http://10.11.58.236:15080' -t VMhJqm8dubAh2nJZxl9dhsIbuZYM6tV8 -s 9080 -p 35080  -k 35082 -g 35083 -q 35181 -P notls

# master节点
[INFO]
    mode:         master     ALL-IN-ONE
    node:         kuscia-system
    secretpad     http      port: 9080
    kuscia        http      port: 15082
    kuscia        grpc      port: 15083
    kuscia        gateway   port: 15080
    kuscia        protocol: tls

# 打包新的包
python3 setup.py bdist_wheel --lite
# dist/secretflow_lite-1.9.0b2-cp310-cp310-manylinux2014_x86_64.whl
# 制作镜像
sh build.sh -v oran

# 更新平台列表组件
./update-sf-components.sh -u root -i secretflow/sf-dev-anolis8:oran
# 重启容器
docker restart root-kuscia-master-secretpad

# 注册组件镜像
./register_app_image.sh -c root-kuscia-master -i docker.io/secretflow/sf-dev-anolis8:oran -f app_image.secretflow.oran.yaml
# 节点导入引擎镜像
./register_app_image.sh -c root-kuscia-lite-hjxndwid -i docker.io/secretflow/sf-dev-anolis8:oran --import
