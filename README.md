# Lf config

#### 介绍
Lf 文件管理器的配置文件

将文件复制到，`~/.config/lf`目录下的

```bash
├── cleaner
├── lfrc
├── scope
└── shortcutrc
```

将`lfub`复制到`~/.local/bin`目录下。

同时需要安装`ueberzug`，运行`lfub`才可以预览图片。

安装方法：

```bash
pip3 install ueberzug
```

配置中还需要安装的软件有：

1. fzf  # 模糊搜索工具
2. trash-cli # 删除到回收站
3. dragon-drop # 文件拖动
4. sxiv # 图片查看器

如果你需要按`q`退出后，能切换工作目录，需要在`.bashrc`中添加代码：

```bash
l () {
    tmp="$(mktemp)"
    lf -last-dir-path="$tmp" "$@"
    if [ -f "$tmp" ]; then
        dir="$(cat "$tmp")"
        rm -f "$tmp"
        if [ -d "$dir" ]; then
            if [ "$dir" != "$(pwd)" ]; then
                cd "$dir"
            fi
        fi
    fi
}
```

这样可以在终端中输入`l`启动lf。（注：如果需要预览图片，需要将上面代码中的`lf`改成`lfub`)

#### 显示图标

在`lfrc`配置文件中添加：

```bash
set icons
```
同时在`~/.profile`文件中添加环境变量`LF_ICONS`:
```bash
export LF_ICONS="di=📁:\
fi=📃:\
tw=🤝:\
ow=📂:\
ln=⛓:\
or=❌:\
ex=🎯:\
*.txt=✍:\
*.mom=✍:\
*.me=✍:\
*.ms=✍:\
*.png=🖼:\
*.webp=🖼:\
*.ico=🖼:\
*.jpg=📸:\
*.jpe=📸:\
*.jpeg=📸:\
*.gif=🖼:\
*.svg=🗺:\
*.tif=🖼:\
*.tiff=🖼:\
*.xcf=🖌:\
*.html=🌎:\
*.xml=📰:\
*.gpg=🔒:\
*.css=🎨:\
*.pdf=📚:\
*.djvu=📚:\
*.epub=📚:\
*.csv=🍍:\
*.xlsx=🍍:\
*.tex=📜:\
*.md=📘:\
*.r=📊:\
*.R=📊:\
*.rmd=📊:\
*.Rmd=📊:\
*.m=📊:\
*.mp3=🎵:\
*.opus=🎵:\
*.ogg=🎵:\
*.m4a=🎵:\
*.flac=🎼:\
*.wav=🎼:\
*.mkv=🎥:\
*.mp4=🎥:\
*.webm=🎥:\
*.mpeg=🎥:\
*.avi=🎥:\
*.mov=🎥:\
*.mpg=🎥:\
*.wmv=🎥:\
*.m4b=🎥:\
*.flv=🎥:\
*.zip=📦:\
*.rar=📦:\
*.7z=📦:\
*.tar.gz=📦:\
*.z64=🎮:\
*.v64=🎮:\
*.n64=🎮:\
*.gba=🎮:\
*.nes=🎮:\
*.gdi=🎮:\
*.1=ℹ:\
*.nfo=ℹ:\
*.info=ℹ:\
*.log=📙:\
*.iso=📀:\
*.img=📀:\
*.bib=🎓:\
*.ged=👪:\
*.part=💔:\
*.torrent=🔽:\
*.jar=♨:\
*.java=♨:\
"
```
