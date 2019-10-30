**test**
*test*
```nền```

███████████████████████ 
                      █
                      
**Loading a web page in current browser window - Here is a list of possible ways to load web page**

driver.get(java.lang.String)
driver.navigate().to(java.lang.String)
driver.navigate().to(java.net.URL)

**Navigation - Here is a list of possible ways to navigate back or forward**

Driver.Navigate().Back()
Driver.Navigate().Forward()

**Refresh page - refresh() is the only method to refresh page in selenium**

Driver.Navigate().Refresh()

**Window Title - Window title get be obtained using getTitle() method**

driver.getTitle()

**Current URL - Current url can be obtained using method getCurrentUrl()**

driver.getCurrentUrl()

**Page Source - Whole page source be collected using getPageSource() method**

driver.getPageSource()

**Locating web elements
driver.findElement(org.openqa.selenium.By)**
- 0 match -> throws exception
– 1 match -> returns a WebElement instance
– 2+ matches -> returns only the first match from web page
**driver.findElements(org.openqa.selenium.By)**
– 0 match -> returns an empty list
– 1 match -> returns a list with one WebElement
– 2+ matches -> returns list with all matching WebElements

**Inspecting elements in web browsers**
Firefox
– Firebug add-on (Right click -> Inspect element / F12)
– Firefinder add-on (Try out your CSS & Xpath expressions)
Chrome
– Built-in (Right click -> Inspect element / F12)
IE
– Built-in (Tools -> Developer Tools / F12)

**Finding element by id**

driver.findElement(By.id(”some_id”));
- Ideal solution, however…
– Ids don’t always exist
– Their uniqueness is not enforced
– Used by developers as well

**Finding element by Class Name**

driver.findElement(By.className(”some_class_name”)); 

**Finding Element by Linktext**

driver.findElement(By.linkText(”Sign in”));
driver.findElement(By.partiallinkText(”Sign”))

**Finding name by Name**

driver.findElement(By.name(”password”));
<input id=”modCustLoginPassword” name=”password”>

 
**Find element by tagName**

Email address
driver.findElement(By.tagName(”label”));

**Find elment by Support Classes**
Return all that matches each of the locators in sequence

driver.findElements(new ByChained(by1, by2))
Return all that matches any of the locators in sequence

driver.findElements(new ByAll(by1, by2))

**Find element by CSS Selector**

-Absolute path-

driver.findElement(By.cssSelector(”html>body>div>p>input”));
Relative path

driver.findElement(By.cssSelector(”input”));
Attribute selection

driver.findElement(By.cssSelector(”button[name]”));

driver.findElement(By.cssSelector(”button[name=‚cancel’]”));

driver.findElement(By.cssSelector(”img:not[alt]”));

-Id selection-

driver.findElement(By.cssSelector(”#save”));

-Class selection-

driver.findElement(By.cssSelector(”.login”));

-Combined selection-

driver.findElement(By.cssSelector(”button#save”));

driver.findElement(By.cssSelector(”input.login”));

-First matching child of the specified tag-

driver.findElement(By.cssSelector(”div#students:first-child”));

-Nth matching child of the specified tag-

driver.findElement(By.cssSelector(”#loginForm:nth-child(3)”));

-First matching enabled tag-

driver.findElement(By.cssSelector(”button:enabled”));

**Finding element by XPath**
-Absolute path-

driver.findElement(By.xpath(”html/body/p/input”));
-Relative path-

driver.findElement(By.xpath(”//input”));
-Attribute selection-

driver.findElement(By.xpath(”//input[@id=’username’]”));
driver.findElement(By.xpath(”//*[@id=’myId’]”))

**Element interrogation**
element.getText();
element.getAttribute();
element.getTagName();
element.isDisplayed();
element.isEnabled();
element.isSelected(); -> checkbox is selected or not
selectElement.isMultiple(); -> multi select listbox or not
selectElement.getOptions(); -> listbox select options

**Click**
element.click() – Button – Link – Checkbox – Combobox

**Submit**
form.submit() – Form

**Shift + Click**

Actions(driver).keyDown(Keys.SHIFT).click(element).keyUp(Keys.SHIFT).build().perform();

**Special Actions**
Actions(driver).moveToElement(element).build().perform();

Actions(driver).contextClick().build().perform();

Actions(driver).doubleClick().build().perform();

Actions(driver).clickAndHold().build().perform();

Actions(driver).release().build().perform();

**Type text**
element.sendKeys(”string”)
– Input field

**Clear text**
element.clear()

**Listbox Selection**
new Select(element).selectByIndex(elementCount)

**Listbox Manipulating Commands**
select[ByIndex, ByVisibleText, ByValue]
deselect[ByIndex, ByVisibleText, ByValue]
deselectAll()

**Page Load Timeout**

Sets the amount of time to wait for a page load to complete
Global setting of the Webdriver object
Negative value means indefinite wait time
driver.manage().timeouts(). pageLoadTimeout(30, TimeUnit.SECONDS);

**Implicit Wait**
Specifies the waiting time for element not immediately visible
Global setting of the Webdriver object
0 by default
driver.manage().timeouts().implicitlyWait(5, TimeUnit.SECONDS);

**Explicit Wait**

Waiting for a certain condition
Poor alternative
Thread.sleep(1000);

**WebDriverWait class**

WebDriverWait wait = new WebDriverWait(driver, TIME_OUT);
wait.until(ExpectedConditions.method);


**ExpectedConditions methods**

presenceOfElementLocated(By locator)

textToBePresentInElement(WebElement element, java.lang.String text)

titleContains(java.lang.String title)

visibilityOf(WebElement element)

invisibilityOfElementLocated(By locator)

elementToBeSelected(WebElement element)

elementToBeClickable(By locator)

**Window Handling**

Size

driver.manage().window().getSize().getHeight();
driver.manage().window().getSize().getWidth();
driver.manage().window().setSize(Dimension d);
driver.manage().window().maximize();
Position

driver.manage().window().getPosition()..getX();
driver.manage().window().getPosition()..getY();
driver.manage().window().setPosition(Point p);

**Handles**

String windowHandle = driver.getWindowHandle();
Iterator windowIterator = browser.getWindowHandles();

**HandlesSwitch To**

driver.switchTo().window(windowHandle);

**How to take Screenshots in Selenium**

-Advantages-

Keep track of changing UI
Store pages with error

-Example-

File screenshot =((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);

FileUtils.copyFile(screenshot, new File(fileSource));
