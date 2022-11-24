# anydong/url-to-pdf-api

本镜像基于 [url-to-pdf-api](https://github.com/alvarcarto/url-to-pdf-api) 项目构建。

## build

```shell
sudo docker compose build
```

## run

```shell
sudo docker run --rm --name my-app-url-to-pdf-api -p 9527:80 anydong/url-to-pdf-api:0.0.1
```

## use

访问链接以查看效果：

[http://127.0.0.1:9527/api/render?url=https://github.com/anydong/docker-images/tree/main/url-to-pdf-api](http://127.0.0.1:9527/api/render?url=https://github.com/anydong/docker-images/tree/main/url-to-pdf-api)

更多详细设置参数请查看原项目。

## 当前已安装字体
  * [Roboto](https://fonts.google.com/specimen/Roboto)
  * [Noto Sans Simplified Chinese](https://fonts.google.com/noto/specimen/Noto+Sans+SC)
  * [Noto Sans Traditional Chinese](https://fonts.google.com/noto/specimen/Noto+Sans+TC)

font-family 设置

```css
@font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial,
  'Noto Sans', sans-serif, 'Apple Color Emoji', 'Segoe UI Emoji', 'Segoe UI Symbol',
  'Noto Color Emoji';
```
> 参考自：https://ant.design/docs/spec/font-cn