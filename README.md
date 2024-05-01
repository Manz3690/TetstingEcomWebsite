# TetstingEcomWebsite
This is a project about Automating an entire e-commerce website from Login to Checkout.

package Day1;

import java.time.Duration;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class Automate {
	public static void main(String[] args) throws InterruptedException {
		
		WebDriver driver = new ChromeDriver();
		driver.get("https://tutorialsninja.com/demo/");
		driver.manage().timeouts().implicitlyWait(Duration.ofSeconds(5));
		driver.manage().window().maximize();
		
		driver.findElement(By.linkText("My Account")).click();
		Thread.sleep(3000);
		driver.findElement(By.linkText("Login")).click();
		driver.findElement(By.xpath("//input[@placeholder='E-Mail Address']")).sendKeys("manish.ks@gmail.com");
		driver.findElement(By.xpath("//input[@placeholder='Password']")).sendKeys("Mks@123");
		Thread.sleep(3000);
		driver.findElement(By.cssSelector("input.btn-primary")).click();
		System.out.println(driver.findElement(By.xpath("//a[text()='Account']")).isDisplayed());
		
		driver.findElement(By.xpath("//input[@placeholder='Search']")).sendKeys("imac");
		driver.findElement(By.cssSelector("button.btn-default")).click();
		
		driver.findElement(By.linkText("iMac")).click();
		WebElement quantity = driver.findElement(By.name("quantity"));
		quantity.clear();
		quantity.sendKeys("2");
		driver.findElement(By.id("button-cart")).click();
		WebElement cartStatus = driver.findElement(By.xpath("//*[@class='alert alert-success alert-dismissible']"));
		System.out.println(cartStatus.getText());
		System.out.println(cartStatus.isDisplayed());
		driver.findElement(By.linkText("Checkout")).click();
		driver.findElement(By.cssSelector("a.btn-primary")).click();
		
	}


}
