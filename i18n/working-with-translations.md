# Working with translations

嗨😉, 老铁, 我们的游戏使用 PO (gettext) 文件来支持 i18n(internationalization).

做翻译的老哥们经常用这个PO (gettext) 文件格式🍭, Godot 也原生支持这个文件格式.

我们将翻译文件保存在单独的存储库中。 <br/>
我想, 既然你点开了这 markdown 文件, 或许也想贡献游戏翻译? <br/>
欢迎随时点开 [learn-gdscript-translations](https://github.com/GDQuest/learn-gdscript-translations) 来参与翻译工作🍻



## How translations work in Godot and the app

Godot 引擎会自动翻译 UI 节点，而我们需要在调用 `tr()` 函数时 wrap 字符串文字。

一般来说, 在 Godot 项目设置中, 都会开启预加载翻译资源。

>Instead, this app loads translations dynamically because we separate localization resources into several files per supported language. 
>This applies to both POT files (translation templates) and translated PO files.
相反, 本游戏会动态加载翻译, 这适用于 POT 文件 (翻译模板) 和翻译后的 PO 文件。


### Updating translation templates

gettext翻译格式有两个文件扩展名：POT是翻译模板文件，PO是特定语言的翻译文件。

PO文件源自POT文件，这使我们可以精细追踪在不同版本之间发生变化的字符串。

要更新POT文件，您需要在Python中安装babel和babel-godot，请按照 [Godot 官方文档](https://docs.godotengine.org/en/stable/tutorials/i18n/localization_using_gettext.html#creating-the-po-template-pot-using-pybabel) 中的建议进行操作。

我们使用 Python 脚本来提取文档字符串。像这样从项目的根目录执行：

```
python ./i18n/extract.py
```

接下来，您需要将POT文件复制到[learn-gdscript-translations](https://github.com/GDQuest/learn-gdscript-translations)代码库，我们会在那里进行内容翻译。

### Adding a new language to the app

To add a new language to the app, you need to:
嗨, 如果你想为本游戏添加新的语言支持🥠(比如火星文😆), 你可以参考以下流程:


1. 在 `i18n/` 目录下创建一个以您的语言的两个字母代码命名的新子目录。例如，对于西班牙语，使用`es/`，对于俄语，使用`ru/`，对于中文，使用`zh/`。
2. 对于 `i18n/` 目录中的每个POT文件，在您的新子目录中创建一个派生的PO翻译文件。您可以使用程序 [Poedit](https://poedit.net/)  来完成这项工作。
3. 打开脚本 `TranslationManager.gd`，并将您的新语言代码添加到常量 `SUPPORTED_LOCALES` 中。`SUPPORTED_LOCALES` 中语言的顺序决定了它们在设置菜单中的显示顺序。

该应用程序可能不支持您语言的字符。如果是这种情况，可以开一个[issue](https://github.com/GDQuest/learn-gdscript/issues)来询问，以添加缺失的字体文件和字体切换代码。





