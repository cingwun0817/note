# Css Selector #
see [http://slides.com/enterme3q/css-selector](http://slides.com/enterme3q/css-selector) ...

practice [http://flukeout.github.io/](http://flukeout.github.io/) ...

* Class Selector
* ID Selector
* Type Selector
* Universal Selector
* Attribute Selector
* Grouping Selector
* Descendant Selector
* Child Selector
* Adjacent Sibling Selector
* General Sibling Selector
* Pseudo-classes Selectors 
* Pseudo-elemtent Selectors

## Class Selector ##
css

	.css {
		...
	}

html

	<dev class="css">aaa</dev>
	
## Attribute Selector ##
根據屬性條件，去選取元素

css

	element[attr]
	element[attr="val"]  /* val 全中 */
	element[attr*="val"] /* val於內容中有中 */
	element[attr^="val"] /* 中開頭 */
	element[attr$="val"] /* 中結尾 */
	
## Grouping Selector ##

css 
	
	 elementA, elementB, elementC{
	 	...
	 }
	 
## Descendant Selector ##

css

	elementA elementB{
		...
	}
	
## Child Selector ##

css 

	elementA > elementB{
		...
	}
	
## Adjacent Sibling Selector ##

css
	
	elemtentA + elemtentB{
		...
	}

## General Sibling Selector ##

css

	elemtentA ~ elemtentB{
		...
	}
	
## Pseudo-classes Selectors ##
	
css 
	
	/* IE6+ */
	element:link 
	element:visited
	element:bover
	element:active
	element:focus
	element:not(selector)
	/* IE9+ */
	element:first-child / last-child
	element:nth-of-child(n/odd/even)
	element:first-of-type / last-of-type
	element:nth-of-type(n)
	
## Pseudo-elemtent Selectors ##

css

	/* IE9+ */
	elemtent:first-line
	elemtent:first-letter
	/* IE6+ */
	elemtent::after
	elemtent::before

	

