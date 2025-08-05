Some self used LaTeX and Typst templates，including some usage examples.
# Tex
## 相关网站
- https://www.latex-tables.com/
- https://github.com/UweZiegenhagen/LaTeX-Beamer-Theme-Overview  一个beamer模板的GitHub仓库
 
 <!-- ============================== -->
 ## Introduction
 Here are some of my initial LaTeX application files. The source links for LaTeX related configurations in VS Code that I used are as follows:
 - [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)
 - [latex-utilities]https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile
 - [latex-utilities]https://github.com/James-Yu/LaTeX-Workshop/wiki/Compile#latex-workshoplatexbuildforcerecipeusage
 - [CSDN]https://blog.csdn.net/qq_44089921/article/details/107719981
 - [Overleaf]https://cn.overleaf.com/latex/templates?
 
 <!-- = -->
 ## Code
 The following is the configuration I used(It includes some other configurations, but they are irrelevant)
 ```json
 {
    //---------LaTeX Workshop 配置开始-----------
 // 设置是否自动编译,可选："never", "onSave", "onFileChange"
 "latex-workshop.latex.autoBuild.run":"onSave",
 //文件输出路径，会自动创建temp文件
 //"latex-workshop.latex.outDir": "./temp",
    //右键菜单
    "latex-workshop.showContextMenu":true,
    //从使用的包中自动补全命令和环境
    "latex-workshop.intellisense.package.enabled": true,
    //编译出错时设置是否弹出气泡设置
    "latex-workshop.message.error.show": false,
    "latex-workshop.message.warning.show": false,
    // 关闭linter
   "latex.linter.enabled": false,
    // 编译工具和命令
    "latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                //"-output-directory=temp", //自定义辅助文件输出路径
                //"-outdir=%OUTDIR%", //辅助文件输出路径
                "%DOCFILE%"
            ]
        },
        {
            "name": "pdflatex",
            "command": "pdflatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                //"-output-directory=temp", //自定义辅助文件输出路径
                //"-outdir=%OUTDIR%", //辅助文件输出路径
                "%DOCFILE%"
            ]
        },
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
    // 用于配置编译链
    "latex-workshop.latex.recipes": [
        {
            "name": "XeLaTeX",
            "tools": [
                "xelatex"
            ]
        },
        {
            "name": "XeLaTeX*2",
            "tools": [
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "PDFLaTeX",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "PDFLaTeX*2",
            "tools": [
                "pdflatex",
                "pdflatex"
            ]
        },
        {
            "name": "BibTeX",
            "tools": [
                "bibtex"
            ]
        },
        {
            "name": "LaTeXmk",
            "tools": [
                "latexmk"
            ]
        },
        {
            "name": "xelatex -> bibtex -> xelatex*2",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdflatex -> bibtex -> pdflatex*2",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
    //文件清理。此属性必须是字符串数组
    "latex-workshop.latex.clean.fileTypes": [
        "*.aux",
        "*.bbl",
        "*.blg",
        "*.idx",
        "*.ind",
        "*.lof",
        "*.lot",
        "*.out",
        "*.toc",
        "*.acn",
        "*.acr",
        "*.alg",
        "*.glg",
        "*.glo",
        "*.gls",
        "*.ist",
        "*.fls",
        "*.log",
        "*.fdb_latexmk"
    ],
    //设置为onFaild 在构建失败后清除辅助文件
    "latex-workshop.latex.autoClean.run": "onFailed",
    // 使用上次的recipe编译组合
    "latex-workshop.latex.recipe.default": "lastUsed",
    // 用于反向同步的内部查看器的键绑定。ctrl/cmd +点击(默认)或双击
    "latex-workshop.view.pdf.internal.synctex.keybinding": "double-click",
 //设置查看PDF的工具，可选"browser","tab","external"
 "latex-workshop.view.pdf.viewer": "tab",
 "security.workspace.trust.untrustedFiles": "open",
 "go.toolsManagement.autoUpdate": true,
 "terminal.integrated.env.windows": {
     "LANG": "en_US.UTF-8"
 },
 "cmake.showOptionsMovedNotification": false,
 "explorer.confirmDelete": false,
 "workbench.startupEditor": "none",
 "editor.suggest.showStatusBar": true,
 "explorer.confirmDragAndDrop": false,
 "files.autoGuessEncoding": true,
 "workbench.settings.applyToAllProfiles": [
 
 ],
 "[latex]": {
     "editor.defaultFormatter": "mathematic.vscode-latex"
 },
 
 "settingsSync.ignoredExtensions": [
     
 ],
 "json.schemas": [
 
     
 ],
 "chat.editing.alwaysSaveWithGeneratedChanges": true,
 "editor.codeActionsOnSave": {},
 "editor.fontVariations": false,
 "terminal.integrated.enableMultiLinePasteWarning": false,
 "files.associations": {
     "*.rmd": "markdown",
     "4.C": "cpp",
     "locale.h": "c"
 },
 "gitlens.views.commitDetails.files.layout": "list",
 "gitlens.graph.minimap.additionalTypes": [
     "localBranches",
     "stashes",
     "pullRequests",
     "remoteBranches",
     "tags"
 ],
 "git.openRepositoryInParentFolders": "always",
 "redhat.telemetry.enabled": true,
 "[java]": {
 
     "editor.suggest.snippetsPreventQuickSuggestions": false
 },
 "fittencode.languagePreference.displayPreference": "zh-cn",
 "fittencode.languagePreference.commentPreference": "zh-cn",
 
 "latex-workshop.intellisense.biblatexJSON.replace": {
 
 }
 }
 //---------LaTeX Workshop 配置结束-
 ```

# Typst
## 相关网站
- https://www.svgrepo.com/collections/blue/  一些typst可能会用到的icon
- https://www.flaticon.com/free-icons/interest  一些typst可能会用到的icon
- https://typst.app/docs/guides/guide-for-latex-users/  一个给latex用户的typst导引
- https://typst.app/universe/search/  模版
- https://typst-doc-cn.github.io/docs/tutorial/writing-in-typst/  中文typst文档

