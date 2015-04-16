# Knowledge Repositories

## Bookmarks

* [Diigo](https://www.diigo.com/)

## Taking notes

目前最流行、方便的文字紀錄是採用 Markdown（有一個後起之秀叫 CommonMark，是由好幾位非常知名的程式開發者共同發起的標準，意在取代 Markdown，但目前還不夠知名。）。Markdown 原生的格式能力非常有限，眾多擴充版中以 GitHub Flavored Markdown 最為通用。

寫 Markdown 時如果有一個能即時預覽的編輯器會大大提高效率。為了能跨平台操作，我主要 survey browser-based 編輯器。目前看起來比較好用的是 [GitBook](https://www.gitbook.com/) 和 [StackEdit](https://stackedit.io/)。GitBook 的功能比較完整。

考慮到彈性、擴充性（如多人文章集體出版等），我認為比較好的架構是（每個人）自行用順手的編輯器撰寫好 Markdown 文件，並放在各自的 public repository，由一個統一的 static site generator 將之生成為一個 site。由於 GitHub 的 repo 支援 webhook/Travis CI 等，這個架構可以很方便地全部透過雲端服務來完成。因為筆記工具也可以是 browser-based，所以整個筆記過程不需要依賴特定電腦裝置或設定特定環境（環境是在雲端，只要第一次設定好就可以一直使用），是一個很方便的方式。