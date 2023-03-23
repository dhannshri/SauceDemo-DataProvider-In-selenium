# SauceDemo-DataProvider-In-selenium
DataProvider  on website SauceDemo
package ui;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;
import org.testng.annotations.DataProvider;
import org.testng.annotations.Test;

import io.github.bonigarcia.wdm.WebDriverManager;

public class DataProviderTest2 {
	@Test(dataProvider="create")
	public void test(String username, String password)
	{
		ChromeOptions co = new ChromeOptions();
		co.addArguments("--remote-allow-origins=*");
		WebDriverManager.chromedriver().setup();
		WebDriver driver = new ChromeDriver(co);
		driver.get("https://www.saucedemo.com/");
		driver.findElement(By.id("user-name")).sendKeys(username);
		driver.findElement(By.id("password")).sendKeys(password);
		driver.findElement(By.id("login-button")).click();
	}
	//@Test(dataProvider="create")
	//public void test1(String username, String password, String test) {
		//System.out.println(username+"====="+password+"==="+test);
	//}
	@DataProvider(name ="create")
	public Object[][] dataset1()
	{
		return new Object[][] {
			{
				"standard_user","secret_sauce"
			},
			{
				"locked_out_user","secret_sauce"
			},
			{
				"problem_user","secret_sauce"
			},
			{
				"performance_glitch_user","secret_sauce"
			}
		};
	}
	
	@DataProvider
	public Object[][] dataSet() {
		Object[][] dataset = new Object[4][2];
		
		dataset[0][0]="user1";
		dataset[0][1]="pass1";
		
		dataset[1][0]="user2";
		dataset[1][1]="pass2";
		
		dataset[2][0]="user3";
		dataset[2][1]="pass3";
		
		dataset[3][0]="user4";
		dataset[3][1]="pass4";
		
		return dataset;
	}

}

