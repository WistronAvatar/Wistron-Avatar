---
slideOptions:
  transition: slide
---
# Avatar Java Style Guide
本文件提供 Avatar 在使用 Java™ 程式語言撰寫原始碼時，對程式碼標準的完整定義。當一份 Java 原始檔符合這份文件規範才能被視為 Avatar 風格。
## 1. Introduction<span id="tag1"></span>
如同其他程式風格指南一樣，這份文件所探討的範圍不僅只有格式的問題，還包含了其他類型的公約以及程式碼風格。然而，本文件將著重於通常我們都會依循的必要規則 (hard-and-fast rules)，像那些不那麼明確地需要被執行的部份 (不論是人或工具)，這邊也會避免提供建議。

在文件中的範例程式為非規範性的 (non-normative)。這意思是說，程式碼格式應該是要有選擇性的，而不該把範例視為唯一的風格而將之當作規則強制執行，那只是要呈現出 Avatar設計的程式碼風格。
## 2. Source file basics<span id="tag2"></span>
### 2.1. File name<span id="tag21"></span>
源碼檔名包含其最上層級類別 (top-level class) 並區分大小寫，再加上副檔名 .java。
> Example:
> 
> ![](https://i.imgur.com/uGgSBuq.png)
### 2.2. File encoding: UTF-8<span id="tag22"></span>
源碼檔的編碼格式使用 UTF-8。
> Example:
> 
> ![](https://i.imgur.com/QvslZjd.png)
### 2.3. Special characters<span id="tag23"></span>
#### 2.3.1. Whitespace characters<span id="tag231"></span>
除了每行的結束符號， ASCII 空格符號 (0x20) 是唯一存在於源碼檔案中的空白符號，目的是為了閱讀上的舒適性。這意味著：所有的字串以及符號間皆要使用空白。
> Example:
> 
> ![](https://i.imgur.com/mTntHjp.png)
#### 2.3.2. Special escape sequences<span id="tag232"></span>
所有可搭配跳脫符號的字符 (\b、\t、\n、\f、\r、\”、\’ 以及 \\ ) 都直接使用，而不必要轉換成相應的八進位 (如：\012) 或是 Unicode (如：\u000a) 使用之。
## 3. Source file structure<span id="tag3"></span>
一個源碼檔案裡需要包括 (有順序性)：
1. Package 敘述
2. Import 敘述區
3. 獨立的最高層級類別 (top-level class)

以上各個區段之間要使用一空行 (exactly one blank line) 隔開。
> Example:
> 
> ![](https://i.imgur.com/4Rleapr.png)
### 3.1. Package statement<span id="tag31"></span>
Package 敘述不換行 (not line-wrapped)。 意即每一行的最大字數限制 (請見 [4.4. Column limit: 100](#tag44)) 不適用於此。
### 3.2. Import statements<span id="tag32"></span>
#### 3.2.1. No wildcard imports<span id="tag321"></span>
Import 敘述區裡的每一個 import，皆不要使用萬用符號 () 修飾子。
> Example:
> 
> ![](https://i.imgur.com/SMYsFMn.png)
#### 3.2.2. No line-wrapping<span id="tag322"></span>
Import 敘述區裡的每一個 import 不換行 (not line-wrapped)。 意即每一行的最大字數限制 請見 [4.4. Column limit: 100](#tag44) 不適用於此。
#### 3.2.3. Spacing<span id="tag323"></span>
Import 敘述區如有兩種以上不同的library import，可用一空行做為分群呈現，分群裡每行 import 敘述皆不要再空行隔開。
> Example:
> 
> ![](https://i.imgur.com/kl33kWk.png)
### 3.3. Class declaration<span id="tag33"></span>
#### 3.3.1. Exactly one top-level class<span id="tag331"></span> declaration
每個最上層級類別都應該存在於自己的源碼檔案中。
> Example:
> 
> ![](https://i.imgur.com/icXI8us.png)
#### 3.3.2. Ordering of class contents<span id="tag332"></span>
類別成員的排序對於能否很好的識別有極大的影響 ，但實作上並不存在唯一合適的通則。甚至是在不同的類別裡，其中的成員排序就都不同。

重點在於每個類別的維護者都要能夠按某個邏輯去排序其中的成員，並在被詢問時有辦法解釋之。 舉例來說，在新增一個新的函式，我們就習慣的將之加在該類別的最末處，而這樣是不是就造就了一個「按照時間新增」的排序邏輯了呢。
##### 3.3.2.1. Overloads: never split<span id="tag3321"></span>
當類別中有多個建構式 (constructors) 或是多個同名的函式，就讓他們依序的放在一起，中間就不要再穿插進不同成員來造成干擾。
> Example:
> 
> ![](https://i.imgur.com/6B1o37W.png)
## 4. Formatting<span id="tag4"></span>
術語說明：類別中的建構式 (constructor) 或是函式 (method) 該以區塊結構 (block-like construct) 呈現。特別是像 [4.6.3.1.](#tag4631) 裡陣列的初始值，所有陣列的初始值只要是以區塊結構呈現，並不限制其格式都要一樣。
### 4.1. Braces<span id="tag41"></span>
#### 4.1.1. Braces are used where optional<span id="tag411"></span>
在  if、 else、 for、 do 以及 while 這些敘述裡的程式碼，就算是空的，或是僅有一行，也都要使用大括號。
> Example:
> 
> ![](https://i.imgur.com/9lBS9Kh.png)
#### 4.1.2. Nonempty blocks: K & R style<span id="tag412"></span>
在內容為非空的區塊結構中，大括號使用參照Kernighan and Ritchie 風格 ([Egyptian brackets](http://www.codinghorror.com/blog/2012/07/new-programming-jargon.html))，如下
 左大括號前不要換行
 在左大括號後換行，並在右大括號前換行
 當右大括號是用在一個敘述語法、函式、建構函式或是類別之後，就要換行。若是像其後接續的是 else  或是 catch 就不用。
> Example:
> 
> ![](https://i.imgur.com/DwnyZqX.png)
#### 4.1.3. Empty blocks: may be concise<span id="tag413"></span>
當一個區塊結構為空時，可以將左右括號寫在一起，不需要在其中加入空白或是換行 ({}) 除非他是多區塊敘述語法的其中一部份(如 if/else-if/else 或是 try/catch/finally )。
> Example:
> 
> ![](https://i.imgur.com/4c9WpTp.png)
### 4.2. Block indentation: +1 tab<span id="tag42"></span>
每新增一個區塊結構時，便要在其開始就增加一個tab。當區塊結束時，其縮排則返回到和前一層的縮排一致。而縮排的層級適用於其間的程式碼與註解。
> Example:
> 
> ![](https://i.imgur.com/HcungjQ.png)
### 4.3. One statement per line<span id="tag43"></span>
每行的敘述都要換行。
> Example:
> 
> ![](https://i.imgur.com/aNH2bCy.png)
### 4.4. Column limit: 100<span id="tag44"></span>
每個專案皆可選擇自己要以每列 100 個字元為限制。除非是遇到下述例外，否則每行的字數當達到限制時就需要換行，換行的說明請見 [4.5 Line-wrapping](#tag45)。
> Example:
> 
> ![](https://i.imgur.com/nW6YvkO.png)

例外：
1.	不可能滿足在一列的字數限制的條件 (比方說，在 Javadoc 裡很長 URL)。
2.	package 以及 import 敘述 (請見 [3.1. Package statement](#tag31) 以及 [3.2. Import statements](#tag32))。
3.	註解中，可能會被複製貼上的 shell 指令
### 4.5. Line-wrapping<span id="tag45"></span>
術語說明：當程式碼可能在單行裡超過每列限制，而將之拆開到多行中，這個動作稱之為換行 (Line-wrapping)。

並沒有一種方程式可以完整、明確的告訴我們在所有情況中該如何換行。而有常有多種合理的方式去對同一段程式碼換行。

:::info
Note: 雖然換行的原因是為了避免超出行限制，但即使是實際符合行限制的代碼也可能由作者自行決定是否換行。
:::
:::warning
Tip: 精簡函式或是區域變數名稱長度，也許可以解決這種需要被換行的情形。
:::
#### 4.5.1. Indent continuation lines at least +1 tab<span id="tag451"></span>
每個接續在斷行後的第一行開始，都要比原行加上一個 tab 來縮排。
### 4.6. Specific constructs<span id="tag46"></span>
#### 4.6.1. Enum classes<span id="tag461"></span>
每個逗號皆要跟著列舉的項目，也可斷行。

一個沒有函式以及說明文字在其中的列舉，可以將其格式寫成像陣列的初始化。

既然列舉類別是為類別，則其他格式的規則皆視同於類別。
> Example:
> 
> ![](https://i.imgur.com/GGFilaU.png)
#### 4.6.2. Variable declarations<span id="tag462"></span>
##### 4.6.2.1. One variable per declaration<span id="tag4621"></span>
每個變數在宣告 (屬性 (field) 或是區域變數 (local)) 時，僅宣告一個變數，也就是說不要寫成 int a, b; 。
例外: 多變數在同一行的宣告可用於 for loop。
> Example:
> 
> ![](https://i.imgur.com/Bs8bNO8.png)
##### 4.6.2.2. Declared when needed<span id="tag4622"></span>
區域變數不要習慣在其區塊或是類區塊結構的一開始就全部宣告了。而是要在該區域變數第一次被使用前才宣告，盡量將他的範圍最小化。宣告區域變數時通常就會有初始值，或是在其宣告後立刻被初始化。
#### 4.6.3. Arrays<span id="tag463"></span>
##### 4.6.3.1. Array initializers: can be "block-like"<span id="tag4631"></span>
所有陣列在初始化時，只要格式為「類區塊結構 (block-like construct)」皆可。
> Example:
> 
> ![](https://i.imgur.com/cukTavw.png)
##### 4.6.3.2. No C-style array declarations<span id="tag4632"></span>
中括號是型別的一部份，而非變數的一部份： Srting[] args 而不是 String args[]。
#### 4.6.4. Switch statements<span id="tag464"></span>
術語說明：在 switch 敘述區塊的括號中，有一或多個敘述群組。每個敘述群組包含一個或多個 switch 標籤 (像是  case FOO: 或是  default: )，其後接續著一或多個程式敘述。
##### 4.6.4.1. Indentation<span id="tag4641"></span>
和其他區塊一樣， switch 區塊的內容縮排都是 +1 個 tab。
在 switch 標籤後，每新的一行，若是該區塊的開始，就 +1 個 tab做為縮排層級的增加。並在下一個標籤退回到上一個縮排層級，以表示上一個區塊已經結束。
##### 4.6.4.2. Fall-through: commented<span id="tag4642"></span>
在 switch 區塊中，每個敘述群組都會有個終止點 (像是 break 、 continue 、 return 或是拋出異常)，或是標上註釋以表將會或是可能繼續往下一個敘述群組執行。該註解只要足以表達出 fall-through 即可 (通常都是用 // fall through )。這特殊的註解不需要出現在 switch 區塊中的最後一個敘述。
##### 4.6.4.3. The default case is present<span id="tag4643"></span>
每個 switch 敘述的群組中都一定包含 default ，就算裡面沒有程式碼。
> Example:
> 
> ![](https://i.imgur.com/3AiDWP3.png)
#### 4.6.5. Annotations<span id="tag465"></span>
應用標注 (annotation) 的類別、函式與建構函式緊接於其文件區塊之後，每個標注皆自己獨立於一行 (意即一行一個標注) 。而這幾行的斷行並不需依照換行建議 ([4.5. Line-wrapping](#tag45)，所以，縮排層級並不會增加。例如：
> Example:
> 
> ![](https://i.imgur.com/37Rk7fd.png)

例外： 單個無參數的注解可以和其屬名的第一行放在一起。
> Example:
> 
> ![](https://i.imgur.com/nVO4sb1.png)
#### 4.6.6. Comments<span id="tag466"></span>
本節著重在implementation註解。 Javadoc 會在 [8. Javadoc](#tag8) 中單獨提到。
##### 4.6.6.1. Block comment style<span id="tag4661"></span>
註解區塊的縮排，和其接連的程式碼同一層級。可用 /  ...  / 或 // ... 。若是這種註解風格 /  ...  / 有多行時，其子行的起始必需有 ，而該星號需對齊上一行的  。
> Example:
> 
> ![](https://i.imgur.com/SGoCeBU.png)
#### 4.6.7. Modifiers<span id="tag467"></span>
類別與成員的修飾詞，其呈現順序就依 Java 語言的規範：
```java=
public protected private abstract default static final transient volatile synchronized native strictfp`
```
#### 4.6.8. Numeric literals<span id="tag468"></span>
long 於整數型別後加上後綴大寫字母 L，千萬別用小寫字母 (避免和數字 1 )。例如，3000000000L 而不要寫成  30000000000l。
#### 4.6.9. DSL and SQL command<span id="tag469"></span>
使用 StringBuilder 取代 String 來組成 DSL 和 SQL，在呈現上會更清楚且效能更好。
### 4.7. Write short methods<span id="tag47"></span>
好的函式應該夠短，當一個函式寫到 40 行，就容易造成理解上的困難，如有很長的函式，嘗試將其分成多個部分。

例外: 資料 mapping 的函式允許超過 40 行。
## 5. Naming<span id="tag5"></span>
### 5.1. Rules common to all identifiers<span id="tag51"></span>
名稱定義僅使用ASCII字母和數字，並且在下面提到的少數情況下使用下底線。

在 Avatar Style中，不使用特殊前綴或後綴。 

例如，這些名稱不是 Avatar Style：name，mName，sname 和 kName。
### 5.2. Rules by identifier type<span id="tag52"></span>
#### 5.2.1. Package names<span id="tag521"></span>
Package 名稱全部小寫，連續單字直接寫在一起(不用下底線())。例如， com.example.deepspace ，不要這樣 com.example.deepSpace 或 com.example.deepspace 。


此外 Package 應依照 com.wistron.avatar.{專案名稱}.{子專案名稱 (如果需要)}.{模組或功能名稱}.{責任分類} 命名。
> Example:
> ```java
> com.wistron.avatar.supply.controller
> com.wistron.avatar.supply.function
> com.wistron.avatar.supply.dao
> com.wistron.avatar.supply.vo
> ```
#### 5.2.2. Class names<span id="tag522"></span>
類別名稱採用大寫開始的駝峰命名法 (UpperCamelCase)。
類別名稱為名詞或是名詞片語。例如， Character 或  ImmutableList，介面 (interface) 也使用名詞或是名詞片語 (如： List)，但有時候會用形容詞或是形容詞片語取而代之 (如： Readable)。
測試類別的名稱以他們正在測試的類別名稱開頭，以Test結尾。 例如，HashTest 或 HashIntegrationTest。
#### 5.2.3. Method names<span id="tag523"></span>
函式名稱採用小寫開始的駝峰命名法 (lowerCamelCase)。
函式名稱通常都是動詞或是動詞片語。例如， sendMessage 或是 stop 。
下底線可以做為 JUnit 的測試函式名稱與邏輯元件的分隔。一個典型的模式 test&lt;MethodUnderTest&gt;&lt;state&gt;，範例： testPopemptyStack。這邊並沒有唯一的正確方式去命名測試函式。
> Example:
> 
> ![](https://i.imgur.com/iaytNsM.png)

例外: VO (Value Object) 的 getter 和 setter, 會使用小寫開始的駝峰命名法搭配 Snake case 來命名，原因是現行 Avatar 存取的 ElastricSearch index, Oracle table, Redis 等欄位名稱, 皆使用小寫的 Snake case, 因此便於資料 mapping, VO 對應的 getter 和 setter 函式, 皆使用 Snake case。
> Example:
> 
> ![](https://i.imgur.com/9sIRYK4.png)

#### 5.2.4. Constant names<span id="tag524"></span>
常數名稱採用 CONSTANTCASE ，全部採用大寫字母，使用下底線分隔。但究竟什麼是常數呢？

所以有常數的屬性 (Field) 皆是 static final， 但並非所有 static final 屬性的變數皆為常數。在確定變數是為常數前，需要先考慮他是否真的像一個常數。舉例來說，當所有在實作的觀察階段會改變時，那這個變數幾乎就可以肯定不是一個常數。而通常只是打算永不改變狀態是不夠的。
> Examples:
> 
> ![](https://i.imgur.com/UMoEJxq.png)
#### 5.2.5. Non-constant field names<span id="tag525"></span>
非常數屬性的名稱採用小寫開頭的駝峰命名法 (lowerCamelCase)。
名稱通常為名詞或是名詞片語。

例外: VO (Value Object) 使用 Snake case 來命名，現行 Avatar 存取的 ElastricSearch index, Oracle table, Redis 等欄位名稱, 皆使用小寫的 Snake case, 以便於資料 mapping, VO 的非常數命名, 皆使用 Snake case。

> Example:
> 
> ![](https://i.imgur.com/B1hE6Yg.png)
#### 5.2.6. Local variable names<span id="tag526"></span>
區域變數名稱採用採用小寫開頭的駝峰命名法 (lowerCamelCase)。
，區域變數是不可為常數的，當然，也不該使用常數變數的風格。
> Example:
> 
> ![](https://i.imgur.com/bayvWEZ.png)
### 5.3. Camel case: defined<span id="tag53"></span>
英文詞彙有時並非只有一種合理的駝峰命名表示方式，也有像「IPv6」或是「iOS」這樣的縮寫或是不尋常的表示法。為了改善使其規律，Avatar Style 將使用下方 (幾乎) 確定的方法。
以散文格式 (prose form) 為名稱的開頭：
1.	字詞皆改為 ASCII 碼並移除所有單引號，例如，「Müller’s algorithm」可以改變為「Muellers algorithm」。
2.	依上述步驟的結果，再依其中的空白以及其餘的符號 (通為會連字符號) 做為拆分點，拆成逐一的單字。
     建議：若所有字都已經有其慣用的駝峰命名用法，仍是將其拆開(例：「AdWords」變成「ad words」。注意，像「iOS」這個並不是一個駝峰命名的形式，這個建議就不適用於這樣的例子。
3.	現在，將每個字母全部變成小寫(包含縮寫)，接著，只要將第一個字母改為大寫：
     每個單字都改，為大寫開頭的駝峰 (upper camel case) 命名。
     每個單字除了第一個單字不改，仍用小寫開頭的駝峰 (lower camel case) 命名。
4.	最後，將所有單字連成一個名稱定義。

需要注意的是，這邊的大小寫幾乎是已經無視原來的單字。
> Examples:
> 
> |Prose form|Correct|Incorrect|
> |--------|--------|--------|
> |XML HTTP request|XmlHttpRequest|~~XMLHTTPRequest~~|
> |new customer ID|newCustomerId|~~newCustomerID~~|
> |inner stopwatch|innerStopwatch|~~innerStopWatch~~|
> |supports IPv6 on iOS?|supportsIpv6OnIos|~~supportsIPv6OnIOS~~|
> |YouTube importer|YouTubeImporter|
:::info
Note: 有些字在英語中，有無帶著連字符號都沒有錯，舉例來說「nonempty」以及「non-empty」二者皆對，所以方法若是命名成  checkNonempty 以及 checkNonEmpty 都是正確的。
:::
## 6. Programming practices<span id="tag6"></span>
### 6.1. <font color=gray>@Override</font>: always used<span id="tag61"></span>
當一個被合法的標註了 <font color=gray>@Override</font> 的方法 (method)，他一定是覆寫了其父類別 (superclass) 的方式、實作了介面方法 (interface mthod) 以及介面中重新指定了其父介面 (superinterface) 的方法。

例外： <font color=gray>@Override</font> 當可以被省略時，代表其父類別的方法已被標示為 <font color=gray>@Deprecated</font>。
### 6.2. Caught exceptions: not ignored<span id="tag62"></span>
下面這個異常 (Exception) 描述，他是少數在發生異常時，可以不做回應的異常處理。(以標準的異常回應，是需要記錄下來的。當在 catch 區塊中，確實沒有任何動作的話，便用註解明確的說明其原委。
> Example:
> 
> ![](https://i.imgur.com/5YnMgXt.png)
### 6.3. Static members: qualified using class<span id="tag63"></span>
引用靜態成員必需搭配著類別 (class) 名稱才是適當的用法，不是和一個物件類型或是描述句來使用。
> Example:
> ```java=20
> Foo aFoo = ...;
> Foo.aStaticMethod(); //good
> aFoo.aStaticMethod(); //bad
> ```
### 6.4. Duty of Controller, Function and DAO<span id="tag64"></span> 
1.	Controller，Function 以及 DAO 之間的權責和調用要明確：Controller 只能調用 Function，Function 只能調用其他Function 和自己所屬的 Dao
2.	Controller 負責 Token 驗證和 Request 類型轉換
3.	Function 負責處理業務邏輯和 Exception，不應該包含任何和 Database 相關的代碼
4.	DAO 只負責對 Database 的 CRUD；函式一定簡潔，每一個函式只做一件事；把 Catch exception 留給 Function 處理。

例外: 對於 Common service，如日期轉換或 Alert mail 等，不在此限。
### 6.5. Single class for storage definition<span id="tag65"></span>
Database 如 Elasticsearch index/type name, Oracle table name, System Definition/User Definition 的 mapping type…，以 final static 的方式統一定義到一個class。

> Example:
> 
> ![](https://i.imgur.com/WnAa64J.png)
### 6.6. Redis services<span id="tag66"></span>
每個Redis Key 的邏輯用單獨的Class來處理，包括 set, get, delete 和 set expired time等。

> Example:
> 
> [RedisMpspSciProcessCtrlDao.java](https://github.com/WistronAvatar/Wistron-Avatar/blob/master/RedisMpspSciProcessCtrlDao.java)
### 6.7. Async process for non-biz logic<span id="tag67"></span>
與業務邏輯無關的代碼，如 Write Log 和 Send Mail ，應該採取非同步觸發的方式來實現。因而不會因為這些邏輯有 exception，導致主程式執行不下去或影響效能。
### 6.8. Input parameter limit for method: 4<span id="tag68"></span>
一般情況下，函式的 Parameter 不要超過 5 個，如果超過應定義 Class 來封裝。

### 6.9. Collection Type Must Be Declared (List, Map, Set)<span id="tag69"></span>
永遠都要宣告 collection type，但不要用 Object type，不要讓人去猜 collection要怎麼使用。
> Example:
> 
> ![](https://i.imgur.com/WSnpYj6.png)
### 6.10. Replaced JsonObject with Java VO<span id="tag610"></span>
儘量使用 Java VO 替代 JsonObject。JsonObject 動態添加屬性的功能雖然靈活，但會增加程式閱讀和 tracking issue 的難度。
### 6.11. Extend Data VO<span id="tag611"></span>
如果需要在共用的 Data VO 加入特定 Project 的專屬使用欄位，請繼承該 Data VO 避免影響他人。
### 6.12. Main Flow Log<span id="tag612"></span>
如果程式有主流程函式，請對每個步驟加上對應的 Log (Info level) 並且要記錄處理時間。
> Example:
> 
> ![](https://i.imgur.com/WBXIsUY.png)
> ![](https://i.imgur.com/7R40eO6.png)
## 7. Naming of data storage<span id="tag7"></span>
### 7.1. ElasticSearch index<span id="tag7_1"></span>
使用小寫的 Snake case 來命名。命名依照 {專案名稱}{子專案名稱 (如果需要)}{模組或功能名稱}{版本號}。Alias 命名規則為{專案名稱}{子專案名稱 (如果需要)}{模組或功能名稱}。名稱通常為名詞或是名詞片語。

> Example:
> 
> ![](https://i.imgur.com/SFW3GX5.png)
### 7.2. ElasticSearch column<span id="tag7_2"></span>
使用小寫的 Snake case 來命名。名稱通常為名詞或是名詞片語。
> Example:
> 
> plant, storage_location, part_num, ...
### 7.3. Oracle table### 7.2. ElasticSearch column<span id="tag7_3"></span>
使用小寫的 Snake case 來命名。命名依照 {專案名稱}_{子專案名稱 (如果需要)}_{模組或功能名稱}。名稱通常為名詞或是名詞片語。
> Example:
> 
> ![](https://i.imgur.com/l4ISTZP.png)
### 7.4. Oracle table field<span id="tag7_4"></span>
使用小寫的 Snake case 來命名。名稱通常為名詞或是名詞片語。
> Example:
> 
> ![](https://i.imgur.com/Widofw0.png)
### 7.5 Redis key<span id="tag7_5"></span>
使用小寫的 Snake case 來命名。命名依照 {專案名稱}_{子專案名稱 (如果需要)}_{模組或功能名稱}。名稱通常為名詞或是名詞片語。
#### 7.5.1. Redis map key<span id="tag7_5_1"></span>
使用小寫的 Snake case 來命名。名稱通常為名詞或是名詞片語。
### 7.6. Base data and configuration name<span id="tag7_6"></span>
使用大寫的 Snake case 來命名。命名依照 {專案名稱}_{子專案名稱 (如果需要)}_{Base data 或 Config 名稱}。名稱通常為名詞或是名詞片語。
> Example:
> 
> ![](https://i.imgur.com/b1iQhOH.png)
### 7.7. Base Data and Configuration Head Name<span id="tag7_7"></span>
以 Site IT 在 UI 上看起來清楚明確為主。名稱通常為名詞或是名詞片語。
## Reference<span id="reference"></span>
https://google.github.io/styleguide/javaguide.html
https://docs.oracle.com/javase/8/docs/technotes/tools/windows/javadoc.html
https://blog.mosil.biz/2014/05/java-style-guide/
https://standardjs.com/readme-zhtw.html
https://docs.oracle.com/javase/tutorial/java/data/characters.html
https://blog.codinghorror.com/new-programming-jargon/

## Javadoc (尚待討論)
~~1 Formatting
1.1 General form
基本的 Javadoc 區塊格式如下範例：~~
```java=
/**
 * Multiple lines of Javadoc text are written here,
 * wrapped normally...
 */
 
 public int method(String p1) { ... }
```
~~只有單行的範例：~~
```java=
/** An especially short bit of Javadoc. */
```
~~這是個永遠可以被接受的基本格式。當整個 Javadoc (包含註解) 沒用使用到 @ 子句時，若是可以被容納在一行的話 (未超過100個字)，就採用單行的格式。
1.2 Paragraphs
空行－在段落之間，以星號 (*) 為起始的一行空白。若是每個段落在一開始有 &lt;p&gt; 時，他跟第一個字之間不會有空格。
Example:~~
```java=
/** An especially short bit of Javadoc. */
```
~~1.3 Block tags
當全部的「@子句 」都出現時，其標準的使用順序為 @param 、@return 、 @throws 、 @deprecated ，而這四種類型都不會為空。當一個「@子句」無法以單行描述完畢時，其續行該要以 @ 為基準做一個 tab 的縮排。
2 The summary fragment
每個類別 (class) 以及成員 (member) 的 Javadoc，都先以簡潔的摘要片段做為開始。這個片段非常地重要：在某些狀況下，他會是該類別 (class) 或是 方法 (method) 索引中，唯一出現的文字片段。
Tip: 舉一個 Javadoc 格式中錯用符號為例 ~~
```java=
/** @return the customer ID */
```
~~這需要被修正成~~
```java=
/** Returns the customer ID. */
```
~~3 Where Javadoc is used
在最小的限度下，所有公開類別 (public class) 以及每個類別 (class) 中公開 (public) 或被保護的 (protected) 成員都該寫上 Javadoc，當然也有少數如下列出的例外狀況。
3.1 Exception: self-explanatory methods
有些「簡單、明確」的方法也不一定要寫上 Javadoc，像是  getFoo 這種簡明的案例，好像除了寫上「返回 foo 值」也什麼好寫的。
Important: 當今天是一個必需要讓看的人知道的狀況下，這個例外就不該拿出來做為忽略不寫相關資訊的理由。比方說，有一個方法被命名為 getCanonicalName，這種狀況下，看得人可能並不瞭解「canonical name」這是什麼意思，在這種狀況下就不要忽略它的說明 (包含只寫上「返回 canonical name」)。
3.2 Exception: overrides
在子類別中覆寫的父類別的方法就不一定要寫上 Javadoc。~~

