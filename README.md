# City
import java.util.concurrent.TimeUnit;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.testng.annotations.Test;
import java.io.IOException;
import org.testng.Assert;
import java.util.List;
import java.util.regex.Matcher;
import java.util.regex.Pattern;



public class TestChicago {
	
	
	@Test
	public static void main(String[] args) throws IOException {

		System.setProperty("webdriver.firefox.bin", "D:\\NewProgram\\Mozilla\\firefox.exe");
		
	    WebDriver driver = new FirefoxDriver();
	    
		System.setProperty("webdriver.ie.driver", "C:\\selenium-2.51.0\\IEDriverServer.exe");
		 
		String appUrl = "http://www.remax1stclass.com/homes-for-sale/chicago/";
		
		 driver.get(appUrl);
		 
	//	 driver.manage().window().maximize();
	     
		 driver.manage().timeouts().implicitlyWait(10, TimeUnit.SECONDS);
		 
	     
	    WebElement SignInButton0 = driver.findElement(By.className("zipListingsNum"));
	     
	    String AllCityNum_str = driver.findElement(By.className("zipListingsNum")).getText();
	    
	    String AllCityNum_str2 = driver.findElement(By.className("zipNameBox")).getText();
	    
	    AllCityNum_str = AllCityNum_str.replaceAll("\\p{P}","");
	    
	    int AllCityNum_int = Integer.parseInt(AllCityNum_str);
	    
	    SignInButton0.click();
	       
	  //  System.out.println(AllCityNum_int);
	    
	      
	     List<WebElement> drop = driver.findElements(By.className("zipListingsNum"));
	     java.util.Iterator<WebElement> i = drop.iterator();
	     
	     int AllCityNumByZip_int = 0;
	     
	     while(i.hasNext()) {
	    	 
	     WebElement row = i.next();	  
	           
	     String AllCityNumByZip_str = row.getText().replaceAll("\\p{P}","");
	              
	     AllCityNumByZip_int = Integer.parseInt(AllCityNumByZip_str) + AllCityNumByZip_int;
	           
	    // System.out.println(AllCityNumByZip_int);
	     
	     }
	   
	if (AllCityNumByZip_int == AllCityNum_int)	{
		System.out.println("Compare counts city: chicago type: sale test: "+AllCityNum_str2+" passed");
		} else {
		System.out.println("Compare counts city: chicago type: sale test: "+AllCityNum_str2+" failed");

		}
