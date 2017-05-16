--- 
category: blog
layout: post
author: telemachus
title: Write a Report with Markdown & LaTex
tags: markdown LaTex
--- 



# Markdown과 LaTex 조합으로 간단한 문서 만들기

거의 모든 글을 markdown 형식으로 씁니다. PlainText의 유연함을 최대한 활용하면서도 다양한 형식으로 최종 사용처를 정할 수 있기 때문입니다. 토막글은 어느 에디터에서든 plaintex로 쓰고 Dropbox에 저장합니다. 이후 글을 보낼 곳이 있다면 [Scrivener](https://www.literatureandlatte.com/scrivener.php) 에서 다듬고, [Marked2](http://marked2app.com) 에서 적당한 탬플릿을 골라서 HTML이나 PDF 로 내보냅니다. 흐름이 자연스럽고 결과물은 유려합니다.

다만 마크다운이 웹을 전제로 하기 때문에 특정 문서 형식, 특히 **보고서**나 조금 더 형식적인 **문건** 을 만들 때는 불가피하게 워드 프로세서를 꺼내야합니다. Scrivener는 다행히 다양한 compile 옵션[^1]이 있습니다만, 역시 번거롭습니다. 그래서 생각한 것이 LaTex입니다.

LaTex는 보통 논문 작성에 많이 사용합니다. 자세한 내용은 저도 잘 몰라서 설명하기 어렵습니다만, Markdown과 마찬가지의 마크업 언어라고 이해할 수 있었습니다. 물론 훨씬 더 오래됐고, 복잡합니다. 과거엔 한글 사용 환경을 만들기 위해 어려운 설치 과정이 있어야 했습니다. 저도 몇번 시도하다가 포기했던 기억이 있습니다. 최근엔 여러 분들의 수고에 힘입어 매우 간단해졌다고 합니다… 만 역시 진입 장벽이 높은 편입니다. 하지만 최근 [Overleaf](http://overleaf.com) 나 [shareLatex](http://sharelatex.com) 같은 온라인 서비스가 등장하면서 문턱이 많이 낮아졌습니다.

Overleaf라는 서비스를 둘러보다가 Markdown 문서를 간단한 보고서로 만들어 보고자 했습니다. 
우선, 저는 Latex를 **전혀** 모르며, 이 글도 그 기준에 맞춰서 썼다는 점을 미리 밝힙니다.

## 준비물
- 텍스트 에디터
- Overleaf 계정 (무료)
- 로고용 이미지 (JPG)


## 보고서 작성

문서를 작성합니다. Markdown의 특성상 어떤 에디터나 상관이 없습니다. nvalt, Scrivener, 메모장 다 좋습니다. 다만 확장자는 `*.md`로 합니다. 주의 사항이 있습니다. 일부 특수 문자는 사용이 불가능합니다. 이는 markdown에서도 마찬가지지요. 역시 LaTex에디터 내에서 `\`를 다는 방식으로 사용할 수 있습니다만 제한이 있어 보입니다. 


## Overleaf Template 고르기
Markdown을 HTML로 변환할 때 특정 CSS를 이용하는 것과 똑같습니다. Latex의 최종 결과물은 PDF로 출력되는 데 이 양식을 우선 만들어야합니다. 저는 아무것도 모르기 때문에 이번에도 역시 기존에 만들어진 훌륭한 작품을 골라서 복사했습니다. 템플릿은 다양하지만 대부분은 LaTex의 특성상 학술 저널, 과학 논문입니다. 일반적으로 쓸 보고서의 형식이라면 Memo나 formal Letter가 적당하다 싶습니다. 

![탬플릿 이미지](http://telemachus.d.pr/vYL8L+)

이 템플릿 중 자신이 쓸 것을 골라 `OPEN AS TEMPATE` 메뉴로 자신의 프로젝트에 복사하면 됩니다. 제가 고른 템플릿은 [✍Memo Template](https://www.overleaf.com/latex/templates/memo-template/xfgfwnxzcgkf#.WRpS5lKB2Rs) 입니다.



## Markdown 환경 설정 및 틀 잡기
이제 MD문서를 Latex가 이해할 수 있도록 환경을 설정해 주어야합니다. Latex에서는 preamble이라고 문서의 서두에 이런 저런 환경을 설정합니다. 기본 설정은 아래와 같습니다. 

`%\title{Overleaf Memo Template}`  
`% Using the texMemo package by Rob Oakes`  
`\documentclass[a4paper,11pt]{texMemo}`  
`\usepackage[english]{babel}`  

템플릿에 대한 설명이 있고, 문서 형식을 규정해 놓았습니다. 글자 크기를 11로 하는 texMemo라는 문서 형식이군요. 좋습니다.  

이제 한글을 쓸 수 있도록…

`\usepackage{kotex}`  

를 추가하고, 마크다운 문법을 사용할 수 있도록  

`\usepackage{markdown}`  

패키지를 추가합니다. 이때 각주 등을 사용하려면 마크다운 패키지에 옵션을 주어야합니다. 

`\usepackage[inlineFootnotes,definitionLists,hashEnumerators,smartEllipses,hybrid]{markdown}`  

어떤 옵션들인지 대충 감이 옵니다. `hybrid` 옵션은 마크다운 문서내에서 Latex 문법도 함께 사용할 수 있도록 하는 옵션입니다. markdown에서도 최종 출력물을 뽑을 때 종종 HTML 태그를 쓰니까 일단 포함시켜 놓았습니다.  아래 링크를 보시면 자세한 설명이 나와 있습니다.[^2]


[✍Overleaf 블로그](https://www.overleaf.com/blog/501-markdown-into-latex-with-style#.WRljF1KB2Rs)

저는 여기에 몇몇을 추가했습니다. 기본 세팅으로 PDF를 출력했더니 헤더에 숫자 형식의 머릿말이 붙습니다. H1은 1, H2는 1.1, 1.2. H3는 1.2.3 이렇게 됩니다.  글의 구조가 복잡한 논문이라면 모를까 거추장스럽습니다. 검색해보니 당연하게도 옵션이 있습니다. 

`\usepackage[compact]{titlesec}`  
`\setcounter{secnumdepth}{-4}`  

H4까지는 숫자를 넣지 말라는 옵션입니다. 이제 거의 다 왔습니다. 문단이나 장, 절 별로 간격을 주고 싶었습니다.  또 검색합니다. 

`\titlespacing{\section}{0pt}{8pt}{16pt}`  
`\titlespacing{\subsection}{3pt}{12pt}{0pt}`  
`\titlespacing{\subsubsection}{18pt}{8pt}{0pt}`  

section은 H1, subsection은 H2 인 듯 합니다. 첫 번째 숫자는 들여쓰기, 두 번째 숫자는 윗 문단과 간격, 세 번째는 아랫 문단과 간격인 듯 합니다. 적당히 조절합니다. 


## Latex 문서 작성-출력하기
이제 문서의 틀은 잡았습니다. 이제 Latex 문서를 작성하고 출력하면 됩니다. 방법은 두 가지가 있습니다. 

`\begin{document}`  
`\begin{markdown}`  
`%여기에 내용을 씁니다.`  
`\end{markdown}`  
`\end{document}`  

마크다운으로 문서를 시작하겠다는 명령을 주고 내용을 적은 뒤 다시 문을 닫아주는 방식입니다. 에디터에서 복사해서 중간에 붙이면 되겠지요. 다른 방법은 *.md 파일을 Overleaf 디렉토리에 업로드 한 뒤 글을 내용을 쓰는 자리에 아래와 같이 명령해 주면 됩니다. 

`\markdownInput{파일 이름.md}`

다 되었습니다. main.tex 파일의 앞 부분에 있는 보내는 이, 받는 이, 제목 등을 입력해 줍니다. 우측 상단에 들어갈 로고도 업로드 해야겠습니다. 청와대 로고를 `blue.jpg`로 업로드했습니다.  overleaf 사이트에서 보이는 최종 화면은 아래와 같습니다. 3분할하여 맨 왼쪽엔 파일 판넬이 있고, 가운데는 에디터, 오른쪽은 결과물인 PDF의 preview가 있습니다.  상단에 있는 `PDF` 메뉴를 누르면 브라우저에서 파일을 다운로드 합니다. 

`# 미세먼지 저감 대책 보고`  
`## 노후 화력 발전소 중단`  
`- 10년 이상 노후 화력 발전소 가동 중단`  
`## 추가 화력 발전소 설치 억제`  
`- 공정률 10\% 이하 발전소 백지화`  

이런 내용을 담아 dust.md로 업로드했습니다. %앞에 붙은 백슬래시가 `%`를 명령이 아닌 문자로 쓰라는 표시입니다. 자, PDF 결과물은 아래와 같습니다. 혹시 몰라서 `이 문서는 \LaTeX 테스트를 위해 작성된 예시 문서입니다. `라고 삽입했습니다. 깔끔합니다. 

![overleaf screen](http://telemachus.d.pr/sscz4+)

## 결론  

간혹 격식을 갖추어 보고할 문서가 있고, HTML 보다는 A4에 출력을 해서 들고 가야할 일이 있습니다. Pages나 Word에서 적당한 양식을 만들어 놓고 사용해도 됩니다. \LaTex도 그런 툴의 하나일 뿐이다. 각각 장점이 있습니다. markdown을 많이 쓰는 분이라면 LaTex가 가진 장점이나 철학을 쉽게 이해할 수 있을 것이라 생각합니다.

## 참고문서
- [Using Markdown in LaTeX documents - LaTeX Example on Overleaf](https://www.overleaf.com/latex/examples/using-markdown-in-latex-documents/whdrnpcpnwrm#.WRpUDFKB2Rs)
- [Markdown into LaTeX with Style - Overleaf Blog](https://www.overleaf.com/blog/501-markdown-into-latex-with-style#.WRpUGVKB2Rs)
- [How to Write Using Rich Text Format and Markdown in LaTeX and Overleaf - Article Published on Overleaf](https://www.overleaf.com/articles/how-to-write-using-rich-text-format-and-markdown-in-latex-and-overleaf/dbqrxvftzskw#.WRpUIFKB2Rs)
- [How to use Overleaf to Write your papers: Part III: How to use Markdown with Overleaf with help…](https://medium.com/thoughts-philosophy-writing/how-to-use-overleaf-to-write-your-papers-part-iii-how-to-use-markdown-with-overleaf-with-help-80f1e27a65a)
- [sectioning - Reducing spacing after headings - TeX - LaTeX Stack Exchange](https://tex.stackexchange.com/questions/53338/reducing-spacing-after-headings)



[^1]: Scrivener에는 markdown문서를 LaTex 문서로 컴파일 하는 옵션도 있습니다
[^2]: 옵션을 쓰기 위해서는 해당 문서 폴더내에 몇몇 파일을 복사해 넣어야합니다.(링크된 블로그 참조) 다만 각주 기능은 제대로 작동하지 않았습니다. 
