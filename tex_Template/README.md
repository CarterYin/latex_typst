# 使用方法
## python代码作用
- 执行两次xelatex编译，以使目录正常显示；
- 自动删除生成的中间文件等，仅保留PDF和tex文件。
- 添加了下划线修复功能：自动检测并修复标题中的下划线字符
- 修复.toc文件：在第一次编译后检查并修复目录文件中的下划线问题
- 更智能的文本处理：避免破坏已经正确转义的内容
- 特定问题修复：针对您文档中的具体标题进行修复
## 命令行
```bash
# 方法1：编译默认的allin.tex文件
python3 compile.py

# 方法2：指定要编译的tex文件
python3 compile.py allin.tex

# 方法3：给脚本添加执行权限后直接运行
chmod +x compile.py
./compile.py
```
