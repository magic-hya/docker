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
