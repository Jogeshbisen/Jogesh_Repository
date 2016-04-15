# Jogesh_Repository
Repository for ISentia website testing

//Regression scripts for capturing first 3 defects found in ISentia website are mentioned below :-


var assert = require('assert'),
test = require ('selenium-webdriver/testing'),
webdriver = require ('selenium-webdriver');

test.describe ('ISentia' function () {
var driver = new webdriver.Builder ().
withCapabilities (webdriver.Capabilities.chrome()).
build();

//Below command is for opening ISentia website

driver.get('http://www.isentia.com");

//Below commands are for clicking on OUR CLIENTS link and verifying if "Clients" page is opened by checking <body> tag id attribute and verifying using browser url

var element = driver.findElement(selenium.By.linkText('OUR CLIENTS'));
element.click();
driver.getCurrentUrl().then(function(value) {
expect(value).toContain('/clients');
});
var element = driver.findElement(selenium.By.tagName('body'));
element.getAttribute('id').then(function(id) {
expect(id).toBe('Clients');
});


//Below commands are for clicking on BLOG link, verify BLOG page id opened and selecting some other country (Singapore) to verify the navigation from BLOG page


var element = driver.findElement(selenium.By.linkText('BLOG'));
element.click();
var element = driver.findElement(selenium.By.tagName('body1'));
element.getAttribute('id').then(function(id) {
expect(id).toBe('BLOG');
driver.Select(driver.findElement(webdriver.By.id("Singapore"))).selectByValue("3");
});
var element = driver.findElement(selenium.By.tagName('body2'));
element.getAttribute('id').then(function(id) {
expect(id).toBe('Singapore');
});


// Below commands are for navigating to "Contact" page, selecting value as "other" in country dropdown and verify a new field called "Specify Country Name" is created upon selecting "other" in country dropdown


var element = driver.findElement(selenium.By.linkText('CONTACT US'));
element.click();
driver.Select(driver.findElement(webdriver.By.id("Other"))).selectByValue("11");
var element = driver.findElement(selenium.By.tagName('body3'));
element.getAttribute('id').then(function(id) {
expect(id).toBe('Specify Country Name');
done();
});
driver.quit();
});

