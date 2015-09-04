# Class & Struct #

Swift 中Class和Struct有很多共同點。共同處在於：

* 定義屬性用於儲存值
* 定義方法用於提供功能
* 定義附屬腳本用於存取值
* 定義建構器用於生成初始化值
* 通過擴展以增加預設實作的功能
* 符合協定以對某類別提供標準功能

與Struct相比，Class還有如下的附加功能：

* 繼承允許一個類別繼承另一個類別的特征
* 型別轉換允許在執行時檢查和解釋一個類別實例的型別
* 解構器允許一個類別實例釋放任何其所被分配的資源
* 參考計數允許對一個類別的多次參考

## 設定變數的差異 ##

示例：

	struct Resolution {
		var width = 0
    	var heigth = 0
	}
	class VideoMode {
		var resolution = Resolution()
		var interlaced = false
		var frameRate = 0.0
		var name: String?
	}

### Struct ###

	let hd = Resolution(width: 1920, height: 1080)
	var cinema = hd
	
set:

	cinema.width = 2048

println:

	println("cinema is now  \(cinema.width) pixels wide")
	// 輸出 "cinema is now 2048 pixels wide"
	
	println("hd is still \(hd.width    ) pixels wide")
	// 輸出 "hd is still 1920 pixels wide"
	
結果就是兩個完全獨立的實例碰巧包含有相同的數值。由於兩者相互獨立，因此將cinema的width修改為2048並不會影響hd中的寬（width）。

### Class ###

反之，Class則會直接修改原值。

## Class & Struct 使用時機 ##

按照通用的准則，當符合一條或多條以下條件時，請考慮構建結構：

* 結構的主要目的是用來封裝少量相關簡單資料值。
* 有理由預計一個結構實例在賦值或傳遞時，封裝的資料將會被拷貝而不是被參考。
* 任何在結構中儲存的值型別屬性，也將會被拷貝，而不是被參考。
* 結構不需要去繼承另一個已存在型別的屬性或者行為。

合適的結構候選者包括：

* 幾何形狀的大小，封裝一個width屬性和height屬性，兩者均為Double型別。
* 一定範圍內的路徑，封裝一個start屬性和length屬性，兩者均為Int型別。
* 三維坐標系內一點，封裝x，y和z屬性，三者均為Double型別。
 
	
