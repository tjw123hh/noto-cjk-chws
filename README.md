# noto-cjk-chws
使用 [chws_tool](https://github.com/googlefonts/chws_tool) 添加了 OpenType `chws`与`vchw` 特性（水平/竖直标点挤压）的 Noto CJK 字体。可通过 AUR 包`noto-fonts-cjk-chws`直接在 Arch Linux 上安装。

使用这些特性可以从字体层面实现标点挤压，如果有自己喜欢的字体也可以用 [chws_tool](https://github.com/googlefonts/chws_tool) 试试。

原仓库虽然有为了符合 Google Fonts 要求而添加 `chws`/`vchw` 的字体（`google-fonts` 目录下），但不全。这里没有更改字体名是因为我没有对字体作任何其他更改，它可以完全替代原本的 Noto Sans CJK 字体。Noto CJK 默认支持`halt`与`vhal`（水平/竖直半角标点替代）特性，因此如果软件支持使用此特性“模拟”标点挤压，无需添加`chws`与`vchw`特性，但目前除了专业排版软件外，几乎只有 Chrome 及 Chromium 内核的软件支持。

[测试说明](https://github.com/googlefonts/chws_tool#visual-test)

## 使用方式

安装后会直接代替原字体，字体名称/字族名没有更改，按原字体相同的方式配置 fontconfig 即可。

如果需要默认开启标点挤压特性，可在 fontconfig 配置中设置`fontfeatures`字段（Qt 尚未支持，参见[QTBUG-78645](https://bugreports.qt.io/browse/QTBUG-78645)）。

示例（`~/.config/fontconfig/fonts.conf`，`<fontconfig>`元素中）：
```xml
    <match target="font">
        <test name="family" compare="contains">
            <string>Noto Sans CJK</string>
        </test>
        <edit binding="strong" name="fontfeatures">
            <string>chws</string>
            <string>vchw</string>
        </edit>
    </match>
    <match target="font">
        <test name="family" compare="contains">
            <string>Noto Serif CJK</string>
        </test>
        <edit binding="strong" name="fontfeatures">
            <string>chws</string>
            <string>vchw</string>
        </edit>
    </match>
```

如果需要更快、更小的下载，或是更改英文字形而不影响中文标点显示，可以尝试[`noto-cjk-chws-patch`](https://github.com/tjw123hh/noto-cjk-chws-patch)，但需要更多 fontconfig 配置且需要软件完整支持。

# Noto CJK fonts

Download individual fonts from the download guides for [Noto Sans CJK](https://github.com/googlefonts/noto-cjk/tree/main/Sans#downloading-noto-sans-cjk) or [Noto Serif CJK](https://github.com/googlefonts/noto-cjk/tree/main/Serif#downloading-noto-serif-cjk) or look in [Releases](https://github.com/googlefonts/noto-cjk/releases)

Release notes and version history are documented separately for [Sans](https://github.com/googlefonts/noto-cjk/blob/main/Sans/NEWS.md#noto-sans-cjk-release-notes) and [Serif](https://github.com/googlefonts/noto-cjk/blob/main/Serif/NEWS.md#noto-serif-cjk-release-notes)

Noto CJK fonts are also available on [Google Fonts](https://fonts.google.com/noto/fonts) but under different names than in this repository. The two letter code here is replaced at Google Fonts as follows:

- *JP* -> *Japanese*
- *KR* -> *Korean*
- *SC* -> *Simplified Chinese*
- *TC* -> *Traditional Chinese*
- *HK* -> *Hong Kong*
