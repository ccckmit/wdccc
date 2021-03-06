# JavaScript 語言基礎

JavaScript 是目前在瀏覽器上唯一通用的程式語言，這種語言經常遭受到許多誤解，像是 「JavaScript 就是 Java 語言的簡化版」、「JavaScript 語言很難用」、「JavaScript 語言設計很差勁」等等。

然而，這些誤解其實是我們不瞭解 JavaScript 所造成的。如果您用心去瞭解 JavaScript，您會發現這是一個「簡單、輕巧又優美」的語言，其原型導向的設計方式，用很簡單的概念達成了物件導向語言的功能，真的很適合做為瀏覽器上的共通語言。

JavaScript 雖然是一種物件導向語言，但是更精確的說，JavaScript 事實上是一種「原型導向」的語言，其中每個物件的 _prototype 欄位都可以指向他的原型，然後用來 clone (自體繁殖) 出新的物件，您可以用 function 型態宣告一個物件，如此該物件就自動具有建構函數了，這種做法是非常簡單、奇特、但卻又彈性十足的方法。

雖然 JavaScript 語言有許多優點，但是也有不少缺點，例如有些語法的邏輯很奇怪，而且 JavaScript 的物件導向並非像 Java, C#, Ruby 等語言那樣傳統，而是採用原型導向的方式，這讓傳統物件導向的使用者在學習 JavaScript 時會感到困難。不過一但您理解了原型導向的精神之後，就會發現這種方法真的有不少優點了。為了較深入的理解 JavaScript ，讓我們先來看看 JavaScript 的歷史！

Web 技術在 1990 年開始成形，早期網際網路只有文字，沒有圖像、音效，且操作非常繁瑣。當時還是大學生的馬克·安德生（Marc Andreessen）被伊利諾伊大學的電腦應用中心聘為臨時工作人員，馬克·安德生提出設計一種簡單的瀏覽程式想法，能方便的檢索網路資料，於是招聘了幾個程式設計師花了六週的時間開發。於是誕生了 Mosaic 瀏覽器。
Mosaic的出現，算是點燃了後期網際網路熱潮的火種。後來在1994年4月，馬克.安德生和Silicon Graphics公司的創始人吉姆·克拉克（Jim Clark）在美國加州設立了一家公司，進一步改善瀏覽器技術，並且創造出了 Netscape 瀏覽器。

當時瀏覽器只能顯示文字與圖片，無法做出像功能表這樣需要即時互動的網頁，於是 Netscape 公司的Brendan Eich設計出了 LiveScript，這是一種動態、弱型別、基於原型的語言，用來寫一些讓網頁可以動起來的小程式。

由於Netscape在與昇陽（Sun）合作的關係，所以 Netscape 將 LiveScript 改名為JavaScript，後來甲骨文 (Oracle) 公司買下了昇陽，所以 JavaScript是甲骨文公司的註冊商標。為了避免侵犯商標權，於是 Ecma國際（前身為歐洲電腦製造商協會）將其以JavaScript為基礎所制定的語言改稱為 ECMAScript。所以現在我們所說的 JavaScript，其真正意義其實應該是 ECMAScript。

現在、JavaScript 已經成為一種非常重要的程式語言，JavaScript 除了用在瀏覽器之外，也被用在許多其他領域，像是您可以用 node.js 在 Server端撰寫 JavaScript 的程式，也可以在 Unity3D 當中用 JavaScript 撰寫遊戲程式，更可以在 Tatinum 當中用 JavaScript 撰寫手機的 APP 然後放到 iPhone,  iPad 或 Android 上面去執行。

## JavaScript 基本語法

JavaScript 最常被嵌入到 HTML 網頁中，以便讓網頁顯式出一些特別的動態效果，因此含有 JavaScript 的網頁通常也被稱為動態網頁，以下是一個 HTML 內嵌 JavaScript 的簡單範例與顯示結果。

原始碼

```html
<html>
<body>
<script type="text/javascript">
var x =5, y=7;
var s = "Hello! "
t = s + x;
z = x * y;
document.write("<pre>x="+x+"\ny="+y+"\ns="+s+"\nt="+t+"\nz="+z+"</pre>");
</script>
</body>
</html>
```

執行結果

JavaScript 的 if 語法也很簡單，基本上與 C 、Java、C# 等語言都相同，以下是一個簡單的範例。

原始碼

```html
<html>
<body>
<script type="text/javascript">
var score = 61;
if (score >= 60)
  document.write("及格");
else
  document.write("不及格");
</script>
</body>
</html>
```

執行結果


JavaScript 的迴圈語法也是繼承 C 語言的，以下是一個範例：

原始碼

```html
<html>
<body>
<script type="text/javascript">
for (i=1;i<=10;i++) {
  if (i == 3) continue;
  if (i == 8) break;
  document.write("i="+i+"<BR/>");
}
</script>
</body>
</html>
```


在 JavaScript 當中，函數的定義有兩種寫法，一種是正常的函數宣告，另一種是把函數當變數的指定方法。事實上，JavaScript 的函數也是一種基本型態，具有這種特點的語言通常稱為函數式語言。這種特性非常好用，因為在函數式語言當中，函數在也不是次等公民，而是一種基本型態，以下是一個 JavaScript 的函數宣告範例。

原始碼

```html
<html>
<body>
<script type="text/javascript">
// 第一種寫法，將匿名函數指定給變數。
var add = function(a,b) {     
  return a+b;
}
// 第二種寫法，直接宣告函數，該函式是一個函數物件
function sub(a,b) {         
  return a-b;
}
document.write("add(3,5)="+add(3,5) +" sub(7,2)="+sub(7,2));
</script>
</body>
</html>
```

執行結果

在 JavaScript 當中，您若要宣告一個陣列時，可以採用 var a = new Array() 的方法，建立一個陣列物件，然後用 a[i] 這樣的方法，存取陣列中的元素。

原始碼

```html
<html>
<body>
<script type="text/javascript">
var x;
var friends = new Array();
friends[0] = "John";
friends[1] = "Mary";
friends[2] = "George";
for (p in friends) {
  document.write(p + ":"+ friends[p] + "<br/>");
}
</script>
</body>
</html>
```

執行結果

## JavaScript 的物件導向語法

雖然說，JavaScript 也能實作很好的物件導向功能，但是如果我們說 JavaScript 是一種物件導向語言，那麼會很容易造成混淆。因為 JavaScript 的物件導向非常非常的特別，與 Java, C++, C# 等語言的物件導向實作方法有很大的不同。

嚴格的說，JavaScript 是一種原型導向語言，原型導向是一種特別簡單的物件導向實作機制，以下是幾個 JavaScript 的物件範例：

```JavaScript
obj = new Object()
obj.x = 3;        // 為 obj 新增一個欄位 x，其值設定為 3
obj.y = 5;        // 為 obj 新增一個欄位 y，其值設定為 5
obj.z = obj.x + obj.y;    // 為 obj 新增一個欄位 z，其值設定為 x+y
```

對於曾經使用像 Java 這種傳統物件導向語言的人而言，會感覺到上述的程式很奇特，因為 obj 一開始只是一個空物件，並沒有包含任何的欄位，但是我們透過指定的方式，動態的為物件增添了 x, y, z 等欄位。

物件導向基本上有三大特性，1.封裝 2. 繼承 3. 多型，瞭解這三個特性的實作方式，通常就可以學會一種語言的物件導向語法了，以下我們將分別針對 JavaScript 中的這三大特性進行介紹。

### JavaScript 物件的封裝

物件導向中的封裝特性，是指將「資料」與「函數」封入一種稱為「物件」的結構當中，以下是 JavaScript 的一個物件範例，其中 x, y 是資料，而 sum 則是函數，這些成員都被封裝在 obj 這樣一個建構函數當中，因此我們呼叫 var o = new obj() 這個指令時，就會建立一個新的物件，並傳回給 o 變數。

程式範例: object.htm

```html
<html>
<body>

<script type="text/javascript">
function obj() {
  this.x = 3;        // 第一種寫法，為 obj 新增一個欄位 x，其值設定為 3
  this["y"] = 5;     // 第二種寫法，為 obj 新增一個欄位 y，其值設定為 5
  this.sum = function() { return this.x + this.y; } // 為 obj 新增一個欄位 add，其值為一個匿名函數
}

var o = new obj();

document.write("o['x']="+o['x']+" y="+o.y+" sum()="+o.sum());
</script>

</body>
</html>
```

執行結果

![](jsObjectOutput.jpg)

### JavaScript 物件的繼承

物件導向中的繼承特性，是指「子物件」可以繼承「父物件」的資料與函數，並且進行修改，這樣我們就不需要重複的實作父物件已經有的函數，或者定義父物件已經有的資料，以達成程式碼重用的目的。

以下範例中的 Student 物件就繼承了 Person 物件，其方法是在 Student 物件的建構函數中，指定 this.prototype = Person 以達到繼承的目的，然後再呼叫 this.prototype(name, age) 以呼叫父物件的建構函數，建立出 name, age, toStr() 物件內容。

程式範例: inheritance.htm

```html
<html>
<body>

<script type="text/javascript">
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.toStr = function() { 
    return "Person:name="+this.name+" age="+this.age; 
  }
}
var john = new Person("John", 40);

document.write("john.toStr()="+john.toStr()+"<BR/>");

function Student(name, age, grade) {
  this.prototype = Person;
  this.prototype(name, age);
  this.grade = grade;
  this.toStr = function() { 
    return "Student:name="+this.name+" age="+this.age+" grade="+this.grade; 
  }
}

var tony = new Student("Tony", 19, "Freshman");

document.write("tony.toStr()="+tony.toStr()+"<BR/>");
</script>

</body>
</html>
```

執行結果

![](jsInheritanceOutput.jpg)

### JavaScript 物件的多型

物件導向中的多型特性，是指當不同的「子物件」繼承同一個「父物件」時，我們可以透過宣告父物件容器，卻將內容指向子物件的方式，以便呼叫到不同子物件中的對應函數。

以下範例中的 var array = [ john, tony ] 這一行，其中的 john 是 Person 類型的物件，tony 是 Student 類型的物件，但是由於 Student 繼承了 Person，而且兩者都有 toStr() 函數，因此當我們用 for (i in array) ... array[i].toStr() ... 這樣的方式呼叫 array[i].toStr() 時，對 john 物件會呼叫到 Person 的 toStr(), 而對 tony 物件會呼叫到 Student 的 toStr(), 這樣就達到了多型的結果。

程式範例: polymorphism.htm

```html
<html>
<body>
 
<script type="text/javascript">
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.toStr = function() { 
    return "Person:name="+this.name+" age="+this.age; 
  }
}
var john = new Person("John", 40);
 
function Student(name, age, grade) {
  this.prototype = Person;
  this.prototype(name, age);
  this.grade = grade;
  this.toStr = function() { 
    return "Student:name="+this.name+" age="+this.age+" grade="+this.grade; 
  }
}
 
var tony = new Student("Tony", 19, "Freshman");
 
var array = [ john, tony ];
 
for (i in array)
  document.write("array["+i+"].toStr()="+array[i].toStr()+"<BR/>");
</script>
 
</body>
</html>
```

執行結果

![](jsPolymorphismOutput.jpg)


### JavaScript 物件的精簡表示法 -- JSON 物件資料交換格式

如果我們想直接在程式中宣告一個複雜的物件，可以使用 JavaScript 中的 {...} 與 [...] 的語法組合，用簡單的語法建構出整個物件。這種格式也常被用在網頁程式的資料交換當中，因此有一個很特別的名稱叫 JSON （Javascript Object Notation）。

目前網路上最常使用的資料交換格式是 XML，但是 XML 文件很繁瑣且囉嗦，讓使用者撰寫不方便，而且不容易嵌入網頁中進行處理。為了讓網頁上的共通程式語言 JavaScript 可以輕易的交換資料，網頁程式的設計者也常用 JSON 取代 XML 進行資料交換。

以下是一個採用 JSON 格式的朋友資料範例，該範例中有兩個朋友，一個是 John, 22 歲，另一個是 Mary, 28 歲。

```JavaScript
{
  "friends": [
     {"name": "John", "age": 22 }
     {"name": "Mary", "age": 28 }
  ]
}
```

程式範例：json.htm

```html
<html>
<body>

<script type="text/javascript">

var george = {
  "name": "George",
  "age": 25,
  "friends": [
     {"name": "John", "age": 22 },
     {"name": "Mary", "age": 28 }
  ]
};

document.write("george.age="+george.age+"<br/>");
document.write("george.friends:\n<ol>");
var friends = george.friends;
for (i in friends)
  document.write("<li>"+friends[i].name+" is "+friends[i].age+"years old!</li>");
document.write("</ol>");
</script>
 
</body>
</html>
```

執行結果

![](jsJsonOutput.jpg)

以上我們簡單的介紹了 JavaScript 的物件導向功能，這種物件導向的實作方式由於是以原型為核心的，因此筆者喜歡稱 JavaScript 為原型導向 (prototype oriented) 的語言，雖然並不是很多人使用「原型導向」這個用法。

## JavaScript 的特殊技巧 – Closure 與匿名函數

在以下的程式中，我們同時展示了 JavaScript 當中的全域變數、區域變數與匿名函數、Closure 等機制。在本文中，我們會用這個程式逐步解釋一些 JavaScript 語言中重要但詭異的概念。

很多語言都有全域變數與區域變數之分，在 JavaScript 當中看來也是如此，但事實上 JavaScript 的全域變數其實只是最外層領域的區域變數而已，在瀏覽器當中，這個最外層領域就是 window，所以以下程式中最後一部分的 sum 與 windows.sum 都同樣是 8。

程式：closure.htm

```Html
<html>
<body>

<script type="text/javascript">
var sum = 0;
function add(x) {
  sum += x;
  document.write("typeof:x="+typeof x+" y="+typeof y+" z="+typeof z+" sum="+typeof sum+"<br/>");
  var y = 2;
  return function() {
    var z = x+y;
    document.write("value :x="+x+" y="+y+" z="+z+" sum="+sum+"<br/>");
    document.write("typeof:x="+typeof x+" y="+typeof y+" z="+typeof z+" sum="+typeof sum+"<br/><br/>");
  }
}

f = add(3);
f();

add(5)();

document.write("typeof:x="+typeof x+" y="+typeof y+" z="+typeof z+" sum="+typeof sum+"<br/><br/>");

</script>

<script type="text/javascript">
document.write("sum="+sum+" window.sum="+window.sum);
</script>

</body>
</html>
```

因此、JavaScript 可以說沒有全域變數的概念，全域變數的只不過是最外層物件的區域變數罷了。

在 JavaScript 每一層領域當中，都可以定義區域變數，例如在上述範例中，sum 是最外層變數，因此所有的程式區段都可以存取這個變數。

參數也是一種區域變數，像是 add(x) 當中的 x，也有領域慨念，其作用範圍僅適用於 add 裏面。而 add 當中所定義的區域變數 y，則只有在定義之後才會生效，因此其領域範圍是從 `var y=2;` 這行程式開始，一直到 add 函數結束為止。

JavaScript 當中的函數，可以沒有名稱，這種函數稱為匿名函數，像是上述範例的函數 add 中，就傳回了一個匿名函數，如下所示：

```JavaScript
function add(x) {
  sum += x;
  document.write("typeof:x="+typeof x+" y="+typeof y+" z="+typeof z+" sum="+typeof sum+"<br/>");
  var y = 2;
  return function() {
    var z = sum+x+y;
    document.write("value :x="+x+" y="+y+" z="+z+" sum="+sum+"<br/>");
    document.write("typeof:x="+typeof x+" y="+typeof y+" z="+typeof z+" sum="+typeof sum+"<br/><br/>");
  }
}
```

變數 z 是該匿名函數的區域變數，由於設定為 sum+x+y，因此存取了外層的 y、x 與更外層的 sum，領域的存取規則是內層可以存取外層的變數，但是外層卻不能存取內層的變數。

筆者認為，JavaScript 中的一個最特別且強大的特性，莫過於函數既可以塞給一般變數，也可以當參數傳遞。例如以下程式區段就是用 f 去接收 add(x) 函數所傳回來的匿名函數，然後再用 f() 函數去執行這個匿名函數而已。

```JavaScript
f = add(3);
f();

add(5)();
```

上列程式碼的最後一行 `add(5)()`，只不過是將這兩個動作合起來一起作，也就是呼叫 add(5) 後，傳回值是個匿名函數，然後再用「匿名函數()」這樣的方法呼叫函數，去執行該匿名函數而已。(這個功能有點像 C 當中的函數指標)

在上述的 closure.htm 程式中，還有個很特別的地方，就是這些匿名函數被傳回來後，就已經回到了最外層的領域範圍了 (window)，那麼當該匿名函數執行時，照理說由於 x, y 屬於內層 add 函數的區域變數，應該會存取不到才對，但為何程式執行結果卻都還是正常，沒有發生錯誤呢？

這牽涉到 JavaScript 當中一個非常特別的機制，稱為 Closure (閉包)。

閉包與 JavaScript 的領域 (Scope) 特性有關，因為 JavaScript 採用 Lexical Scope，也就是變數作用範圍依照程式定義時的上下文 (Context) 所決定，而不是根據執行時期的上下文所決定的。

因此，上述匿名函數所服從的領域規則，仍然是定義時的領域，也就是 add 函數的子領域，而不是執行時期 window 的子領域，因此仍然可以正確存取 x,y,z 等變數，不會發生錯誤。

## 參考文獻
* Node.js 中文電子書 » JavaScript 與 NodeJS
	* <http://book.nodejs.tw/zh-tw/node_javascript.html#scope-closure>
* [图解] 你不知道的 JavaScript - “this”
	* <http://www.cnblogs.com/ruxpinsp1/archive/2008/04/20/1162463.html>
* Javascript - 淺談this與Closure
	* <http://blog.darkthread.net/post-2009-03-11-js-this-and-closure.aspx>
* The this keyword
	* <http://www.quirksmode.org/js/this.html>
* JavaScript中的closure好難懂，它和匿名函式有什麼不同?
	* <http://ithelp.ithome.com.tw/question/10000477>
