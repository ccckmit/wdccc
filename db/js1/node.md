# Node.js 命令列 - 讓 JavaScript 作為一般程式執行

Node.js 通常被用來當成與 PHP、Ruby on Rail 或 ASP.NET 類似的平台，用來撰寫 Web 的網站程式，
但是這種觀點主要是使用 node.js 的 Web 函式庫功能，直接從 Web 程式的實作開始，而非從基礎的 JavaScript 
開始，我們認為這樣的方式並不好，因為入門瓶頸太高，很容易會造成讀者的學習障礙。

事實上、Node.js 當中包含了一個由 Google Chrome 計畫中所釋出的 JavaScript 編譯引擎 -- V8，這是一個
速度很快的 JavaScript 執行工具，在本章中，我們將從命令列基本操作開始，將 node.js 單純當作一個 JavaScript 
解譯器使用，以便透過 node.js 進一步學習 JavaScript 的語法與基本函式庫的用法。

## Node.js 的安裝

本文使用 node.js 0.10.0 版示範，您可以從 node.js 官網上下載到最新的版本，以下是 node.js 的網址。

* <http://nodejs.org/>

node.js 0.10 之後的版本，在 windows 當中的安裝非常容易，只要一直點選下一步，就能完全安裝完畢。

## Node.js 的互動操作環境

安裝完 Node.js 之後，您就可以啟動 Node.js 的互動操作環境，然後開始輸入一些基本的 JavaScript 程式，以便學習 JavaScript 的語法，以下是筆者的一個操作畫面。

![圖、Node.js 的操作畫面](node_shell.jpg)

```javascript
> x = 3
3
> y = 5
5
> z = x+y
8
> w = x*y
15
> x, y, z, w
15
> eval("x+y+z+w")
31
> s = "Hello!"
'Hello!'
> t = x+s
'3Hello!'
> s+t
'Hello!3Hello!'
> score = 80
80
> add = function(a,b) { return a+b; }
[Function]
> add(3,5)
8
> add(374, 567)
941
> sum = function(n) {
... s = 0;
... for (i=1; i<=n; i++)
...   s += i;
... return s
... }
[Function]
> sum(10)
55
> sum(100)
5050
> max = function(a,b) {
... if (a>b)
...   return a;
... else
...   return b;
... }
[Function]
> max(3,5)
5
> max(9,2)
9
```

從以上的操作中，您可以看到我們不只可以進行基本的運算操作，也可以直接在裏面定義函數，以及呼叫這些函數。

當然、您也可以將 JavaScript 的程式存檔，然後用 node.js 去執行，

## Node.js 的命令列工具

雖然互動操作環境感覺很方便，但是要撰寫真正的程式時，就不太好用了，此時您可以使用 Node 的
命令列工具 -- Node.js command prompt 來執行程式。舉例而言，我們可以先撰寫了一個 hello.js 的程式，
如下所示：

檔案：hello.js

```javascript
console.log("Hello!");
```

然後啟動 Node.js command prompt 去執行該程式，以下是我們的執行 hello.js 與下述 sum.js 程式的結果：

![圖、用 Node.js command prompt 執行程式](NodeCommandRunHelloSum.jpg)

檔案：sum.js

```javascript
function sum(n) {
  var s = 0;
  for (i=1; i<=n; i++)
    s+=i;
  return s;
}

console.log("sum(10)="+sum(10));

console.log("sum(100)="+sum(100));
```

於是、透過 Node.js 的開發環境，我們可以將原本只能在瀏覽器中測試的 JavaScript 程式，
放到 Node.js 當中執行，這樣就能更方便的學習 JavaScript 的語法與函式庫，大大的提高了
我們學習 JavaScript 的方便程度。

目前、筆者在撰寫 JavaScript 程式時，通常會先用 Node.js 進行測試，沒有問題之後，在放到
瀏覽器當中去執行，也就是將 Node.js 當作單元測試的工具，這對筆者的幫助很大。

接著、讓我們透過 Node.js 平台，來學習一些 JavaScript 基本函式庫的用法，首先讓我們來看看
動態解譯函數 eval()。

## Eval 函數

Eval 函數可以用來執行任何 JavaScript 程式碼，這是解譯式語言特有的函數，以下是一個使用 eval() 函數的程式範例。

檔案：eval.js

```javascript
x = 3;
y = 5;
console.log("eval('x+y')="+eval('x+y'));

function max(x,y) { 
    return (x>y)?x:y; 
}

console.log("eval('max')="+eval('max'));

console.log("eval('max(x,y)')="+eval('max(x,y)'));

console.log("eval('max(2*x,y)')="+eval('max(2*x,y)'));

```

執行結果：

```
D:\code\node>node eval.js
eval('x+y')=8
eval('max')=function max(x,y) {
    return (x>y)?x:y;
}
eval('max(x,y)')=5
eval('max(2*x,y)')=6

```

雖然 eval() 通常是在解釋環境之下才具備的功能，但是在 Node.js 這種動態編譯環境之下，
卻也能夠順利的執行，這對那些開發 C/C++, Java, C# 等語言的程式人員而言，勢必會感到
非常的羨慕才對。

註：如果您曾經在資料結構的課程上，嘗試去寫運算式處理的中序轉前序程式，只是為了計算
運算式的值，就會知道這樣的功能在那些編譯式語言當中是多麼的難寫，而要寫一個支援任意
運算式執行的程式，基本上就是重新撰寫一個語言解譯器，那就相當於重新建造了整套開發工具，
這是非常非常困難的。

接著、讓我們來看看 Node.js 當中的一些重要的函式庫與觀念，包含「輸出入、檔案、以及模組的定義與引用等」。

### 讀取檔案

程式：readfile.js

```javascript
var fs = require('fs'); // 引用檔案物件
var file = fs.readFileSync(process.argv[2], "utf8"); // 讀取檔案
console.log(file); // 顯示在螢幕上
```

執行結果

```
D:\code\node>node readfile.js readfile.js
var fs = require('fs'); // 引用檔案物件
var file = fs.readFileSync(process.argv[2], "utf8"); // 讀取檔案
console.log(file); // 顯示在螢幕上
```

## 寫入檔案

我們用複製檔案的程式來示範寫入檔案的功能。

程式：copyfile.js

```javascript
var fs = require('fs');
var file = fs.readFileSync(process.argv[2]);
console.log(file);
fs.writeFileSync(process.argv[3], file);
```

執行結果：

```
D:\code\node>node copyfile.js copyfile.js copyfile.js.bak
<Buffer 76 61 72 20 66 73 20 3d 20 72 65 71 75 69 72 65 28 27 66 73 27 29 3b 0a
76 61 72 20 66 69 6c 65 20 3d 20 66 73 2e 72 65 61 64 46 69 6c 65 53 79 6e 63 28
 ...>
```

## 從鍵盤讀取輸入

* 參考 -- <http://nodejs.org/api/readline.html>

檔案：readline.js (讀取一行)

```
var readline = require('readline');

var rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});

rl.question("What do you think of node.js? ", function(answer) {
  // TODO: Log the answer in a database
  console.log("Thank you for your valuable feedback:", answer);

  rl.close();
});
```

檔案：readloop.js (讀取很多行)

```
var readline = require('readline');
var rl = readline.createInterface(process.stdin, process.stdout);

rl.setPrompt('OHAI> ');
rl.prompt();

rl.on('line', function(line) {
  switch(line.trim()) {
    case 'hello':
      console.log('world!');
      break;
    default:
      console.log('Say what? I might have heard `' + line.trim() + '`');
      break;
  }
  rl.prompt();
}).on('close', function() {
  console.log('Have a great day!');
  process.exit(0);
});
```

## 參考文獻
* Node.js 台灣社群協作電子書 -- <http://book.nodejs.tw/>
* Node入門 -- <http://www.nodebeginner.org/index-zh-tw.html>
* 深入浅出Node.js相关的内容 -- <http://www.infoq.com/cn/master-nodejs>
    * 深入浅出Node.js（一）：什么是Node.js -- <http://www.infoq.com/cn/articles/what-is-nodejs>
    * 深入浅出Node.js（三）：深入Node.js的模块机制 -- <http://www.infoq.com/cn/articles/nodejs-module-mechanism>
* node.js 檔案讀取 -- http://book.nodejs.tw/zh-tw/node_basic.html#id2
* <http://stackoverflow.com/questions/2496710/nodejs-write-to-file>
* Node.js, Require and Exports
    * <http://openmymind.net/2012/2/3/Node-Require-and-Exports/>
* Node.js v0.8.5 Manual & Documentation/Modules
    * <http://nodejs.org/api/modules.html#modules_modules>
* Understanding Node.js' "require"
    * <http://jherdman.github.com/2010-04-05/understanding-nodejs-require.html>
