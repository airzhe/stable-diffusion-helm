### 镜像来源 https://github.com/kalaspuff/stable-diffusion-webui-controlnet-docker


### 首次部署时需要手动操作生成模型缓存文件

挂载
```yaml
volumeMounts:
    - mountPath: /app/stable-diffusion-webui/models1
        name: data
        subPath: models 
    - mountPath: /app/stable-diffusion-webui/extensions1
        name: data
        subPath: extensions
```
启动命令
```yaml
command: ["/bin/bash","-c","tail -f /dev/null"]
```


进入容器执行
```shell
/opt/venv/bin/python run.py --listen --ui-config-file ui-config.json --ui-settings-file config.json --disable-console-progressbars --cors-allow-origins huggingface.co,hf.space --no-progressbar-hiding --enable-console-prompts --no-download-sd-model --api --skip-version-check
```

control + c 停止服务后把 models、extensions 目录下的文件移动到 models1 extensions1 下


再次按helm包配置部署就可以