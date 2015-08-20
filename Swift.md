#Swift Note
This is leowang swift note.

##Home
xcode iphome 模擬器

	command + shift + h
	
##Add Navigation Controller

	功能列表 > View > Editor > Embed > Navigation Controller
	
##Show Alert
[See Code] (https://github.com/cingwun0817/Swift/tree/master/ShowAlertView)
###宣告 alertController 物件

	let alertController = UIAlertController(title: "", massage: "",preferredStyle: UIAlertControllerStyle.Alert)

*note: Alert(顯示於中央),  ActionSheet(由下方跳出)*

###加入動作按鈕

	alertController.addAction(UIAlertAction(title: "", style: UIAlertStyle.Default, handler: nil))

*note: Default(預設按鈕), Destructive(取消按鈕)*

####加入Text框

	alertController.addTextFieldWithConfigurationHandler { (testField : UITextField!) -> Void in}

*note: testField 填入框物件*

###輸出

	self.presentViewController(alertController, animated: true, completion: nil)

*note: alertController 為宣告Alert物件*

##Core Data

###First

	import CodeData

###宣告 Managed Object
	
	var notes = [NSManagedObject]()

###Use CodeData

	let appDelegate = UIApplication.sharedApplication().delegate as! AppDelegate
    let managedContext = appDelegate.managedObjectContext

###Get Entity

	let entity = NSEntityDescription.entityForName("Notes", inManagedObjectContext: managedContext!)

*note: Notes is codeData entity* 

###Set Value
Get title field

	let title = NSManagedObject(entity: entity!, insertIntoManagedObjectContext: managedContext)

Set title value

	title.setValue(data, forKey: "title")

*note: data 資料內容*

###Append to managedObject

	notes.append(title)
	
##Transition
[See Code] (https://github.com/cingwun0817/Swift/tree/master/ViewTransition)

* Cover Vertical
* Cross Dissoive
* Flip Horzontal
* Partial Curl

###set storyBoard

	let storyboard: UIStoryboard = UIStoryboard(name: "Main", bundle: nil)

###set detailview

	let detailView = storyboard.instantiateViewControllerWithIdentifier("Detail") as! UIViewController
	
###set transition style

	detailView.modalTransitionStyle = UIModalTransitionStyle.CoverVertical

*note: CoverVertical, CrossDissoive, FlipHorxontal, PartialCurl transition style*

###輸出

	self.presentViewController(detailView, animated: true, completion: nil)
	
###視圖返回上一頁

	dismissViewControllerAnimated(true, completion: nil)


