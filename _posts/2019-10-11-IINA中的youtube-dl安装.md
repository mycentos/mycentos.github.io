IINA中的 youtube-dl

如何使用 youtube-dl
在 偏好设置 > 网络 > youtube-dl 中启用 youtube-dl（默认启用）。
以任意方式打开 URL，如：
菜单中的 文件 > 打开 URL…
将 URL 拖进 IINA 的窗口，或 Dock 图标0.0.10+
使用浏览器插件（从 偏好设置 > 实用工具 下载）

使用你自己的 youtube-dl
Youtube-dl 更新非常迅速。IINA 会在每次发布时更新自带的 youtube-dl，但多数情况下很难跟上它的进度。在自带的 youtube-dl _由于版本太老_无法加载视频时，你可以使用自定义的 youtube-dl 文件。要安装最新的 youtube-dl, 建议使用 homebrew（请确认安装了 homebrew）:https://brew.sh/

/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

Homebrew安装

brew install youtube-dl
安装后，你可以这样找到 youtube-dl 的路径：

which youtube-dl
然后在偏好设置中的 自定义 youtube-dl 路径 中填上含有 youtube-dl 的文件夹。请不要在路径中包含 youtube-dl本身。如果你用 homebrew 的默认安装，你应该填入：

/usr/local/bin/
IINA 仅仅会在运行时将此路径加入PATH 来使 mpv 的 ytdl-hook 搜索到可执行文件，并不会对此路径做任何检查。

如果你发现使用自己的 youtube-dl 时任何视频都无法打开，可能你的 youtube-dl 安装出现了问题。由于运行时你填写的路径会在 PATH 首位，mpv 将优先使用 /usr/local/bin（如果你填写了标准 brew 安装路径）中的 python，所以请确认 homebrew 中装有一个可用的 python。

能否下载视频？
IINA (mpv) 不支持下载。请参考 youtube-dl 的文档，使用它在命令行中直接下载视频。

安装好 youtube-dl 后，我们就可以进行在线视频的下载了，不过有部分视频网站比如 Youtube，高画质的视频和音频是分开的，只使用 youtube-dl 的话会将视频和音频分别下载成两个文件。好在 youtube-dl 也提供了解决方案，我们只需要下载另一个命令行工具 —— ffmpeg 即可，在下载后 youtube-dl 会自动调用 ffmpeg 将视频与音频合成一个文件。ffmpeg 的安装仍然通过 Homebrew 进行，只需要执行下面这个命令即可：

brew install ffmpeg

到此为止，youtube-dl 的安装过程已经完全结束，只需要这样短短三步，不过在开始下载之前，我想首先介绍一下如何对 youtube-dl 进行更新。因为部分视频网站会不定时进行调整，避免被下载视频，因此有时我们需要更新 youtube-dl 以便继续进行视频下载。更新 youtube-dl 我想介绍两种方法，一种是单独更新 youtube-dl，另一种是直接更新 Homebrew 管理的所有软件。单独更新 youtube-dl 的命令如下：

brew upgrade youtube-dl

而假如不指定 youtube-dl，即可更新 Homebrew 管理的所有软件了，命令如下：

brew upgrade