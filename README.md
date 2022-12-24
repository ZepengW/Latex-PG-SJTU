# Latex-PG-SJTU
> latex template of postgraduate for SJTU

根据上海交通大学研究生院给出的[研究生学位论文写作模版](https://www.gs.sjtu.edu.cn/info/1136/8374.htm)进行修改适配，解决latex模版中的一些错误，以及和word模版不一致问题

## 改动
- [x] 结构化文档，并修复原文档中显示问题，如声明页中的矩形框丢失、部分文字丢失等问题。
- [x] 使用bibtex管理参考文献
- [x] 图标中英双标题问题，以及不同章节图子序号连续问题，如：图1-1，图1-2，图2-3
- [x] 盲审版本编译：去除作者名/学号/导师，声明页，致谢，使用盲审版本成果页

## 测试环境
> 注：使用XeTex 编译

- [x] [Overleaf (get template quickly)](https://www.overleaf.com/latex/templates/latex-pg-sjtu/gxhnkrqrywsp)

- [x] [LatexSJTU](https://latex.sjtu.edu.cn/)

- [x] MacOS (Vscode + MacTex)， 编译pipeline: xelatex -> **biber** -> xelatex -> xelatex
<details>
<summary>vscode 配置文件</summary>

```
"latex-workshop.latex.tools": [
        {
            "name": "xelatex",
            "command": "xelatex",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
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
                "%DOCFILE%"
            ]
        },
        {
            "name": "bibtex",
            "command": "bibtex",
            "args": [
                "%DOCFILE%"
            ]
        },
        {
            "name": "biber",
            "command": "biber",
            "args": [
                "%DOCFILE%"
            ]
        }
    ],
  // 编译命令
    "latex-workshop.latex.recipes": [
        {
            "name": "xelatex",
            "tools": [
                "xelatex"
            ],
        },
        {
            "name": "xelatex*2",
            "tools": [
                "xelatex",
                "xelatex"
            ],
        },
        {
            "name": "bibtex",
            "tools": [
                "bibtex"
            ],
        },
        {
            "name": "pdflatex",
            "tools": [
                "pdflatex"
            ]
        },
        {
            "name": "xe->bib->xe->xe",
            "tools": [
                "xelatex",
                "bibtex",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "xe->biber->xe->xe",
            "tools": [
                "xelatex",
                "biber",
                "xelatex",
                "xelatex"
            ]
        },
        {
            "name": "pdf->bib->pdf->pdf",
            "tools": [
                "pdflatex",
                "bibtex",
                "pdflatex",
                "pdflatex"
            ]
        }
    ],
```

</details>




## 致谢
非常感谢[SJTUThesis](https://github.com/sjtug/SJTUThesis)的开发者们，作为一个纯latex用户（即latex开发小白），本项目中的很多改动都是从该项目中得到参考和借鉴。

鉴于SJTU研究生院于21年推出了官方的模板（一堆问题）与SJTUThesis在样式上存在差异，而作为一名latex小白，直接在SJTUThesis项目基础上改动为官方给出的样式有些力不从心。

故本项目基于[研究生学位论文写作模版](https://www.gs.sjtu.edu.cn/info/1136/8374.htm)，在保证显示内容（基本？）一致的情况下，对原始latex模板的一些错误和难用之处进行改进和优化。
