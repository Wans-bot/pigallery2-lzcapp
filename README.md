# pigallery2-lzcapp

懒猫微服 (LazyCat MicroServer) 版 PiGallery2 —— 把微服里的照片目录变成可浏览的时间线相册。

- 上游：https://github.com/bpatrik/pigallery2 （MIT）
- 版本：3.5.2
- 镜像：`registry.lazycat.cloud/wans/bpatrik/pigallery2:714efccda897e235`（上游 `bpatrik/pigallery2:3.5.2` 复制而来）

## 打包

```bash
lzc-cli project release -o dist/pigallery2.lpk
lzc-cli lpk install dist/pigallery2.lpk
```

## 实现要点

- `document.private` 声明后平台自动把应用文稿挂到 `/lzcapp/documents`，
  `setup_script` 把 pigallery2 默认扫描的 `/app/data/images` 软链过去，
  用户往「文件」里的应用文档目录放照片即可。
- 配置与索引（config.json / sqlite）持久化在 `/lzcapp/var/pigallery2/{config,db}`。
- 界面自带简体中文（`src/frontend/translate/messages.cn.xlf`）。
