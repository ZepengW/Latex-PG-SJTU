# Latex-PG-SJTU
根据上海交通大学研究生院给出的[研究生学位论文写作模版](https://www.gs.sjtu.edu.cn/info/1136/8374.htm)进行修改适配，解决latex模版中的一些错误，以及和word模版不一致问题

## 改动
- [x] 结构化文档，并修复原文档中显示问题，如声明页中的矩形框丢失、部分文字丢失等问题。
- [x] 使用bibtex管理参考文献
- [ ] 不同章节图子序号连续问题，如：图1-1，图1-2，图2-3
- [ ] 盲审版本编译

## 测试环境
> 注：使用XeTex 编译

- [ ] Overleaf

- [ ] LatexSJTU

- [x] MacOS (Vscode + MacTex)， 编译pipeline: xelatex -> biber -> xelatex -> xelatex
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
感谢[SJTUThesis](https://github.com/sjtug/SJTUThesis)开源项目的贡献者们，从个人观感而言，该项目的latex模板无论是从美观、规范、便于上手等角度都是一个很优秀的模板。作为一个latex用户（latex开发小白），很多改动都是从该项目中获得了 学习和启发。

但是鉴于研究生院于21年推出了官方的模板（一堆问题），与SJTUThesis略有差异，而作为一名latex小白，直接在SJTUThesis项目基础上改动为和官方一样效果对我来说有点力不从心。故本项目基于[研究生学位论文写作模版](https://www.gs.sjtu.edu.cn/info/1136/8374.htm)，在保证显示内容一致的情况下，对其中的一些错误、引用导入和增加盲审编译选项等功能做出改进。