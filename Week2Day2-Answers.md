Question1:
Try around the API collection shared for home assignments with different input and parameters.

Note. Postman collections in ref documents.

Answers: 

1. SalesForce Dom of login copied and pasted in the body with the existing prompts in it. Added below the Body and its response

Body: {
  "messages": [
    {
      "role": "user",
      "content": "Extract the below given DOM : \n\n <div id=\"theloginform\" style=\"display: block;\"><form name=\"login\" method=\"post\" id=\"login_form\" onsubmit=\"handleLogin(); return false;\" action=\"https://login.salesforce.com/\" target=\"_top\" autocomplete=\"off\" novalidate=\"novalidate\"><input type=\"hidden\" id=\"pqs\" name=\"pqs\" value=\"?locale=in\"><fieldset style=\"display:none\">  <input type=\"hidden\" name=\"un\" id=\"un_hfid\" value=\"\">   <input type=\"hidden\" name=\"width\" value=\"\">  <input type=\"hidden\" name=\"height\" value=\"\">  <input type=\"hidden\" name=\"hasRememberUn\" value=\"true\">  <input type=\"hidden\" id=\"login_startUrl\" name=\"startURL\" value=\"\">  <input type=\"hidden\" name=\"loginURL\" value=\"\">  <input type=\"hidden\" name=\"loginType\" value=\"\">  <input type=\"hidden\" name=\"useSecure\" value=\"true\">  <input type=\"hidden\" name=\"local\" value=\"\">  <input type=\"hidden\" name=\"lt\" value=\"standard\">  <input type=\"hidden\" name=\"qs\" value=\"\">  <input type=\"hidden\" name=\"locale\" value=\"in\">  <input type=\"hidden\" name=\"oauth_token\" value=\"\">  <input type=\"hidden\" name=\"oauth_callback\" value=\"\">  <input type=\"hidden\" name=\"login\" value=\"\">  <input type=\"hidden\" name=\"serverid\" value=\"\">  <input type=\"hidden\" name=\"display\" value=\"page\"></fieldset> <h1 style=\"margin: 0 0 16px 0; padding: 0; font-size: .875rem; font-weight: bold; font-family: SFS, Arial, sans-serif; color: #03234D; text-align: center;\">Salesforce login</h1><div id=\"usernamegroup\" class=\"inputgroup\"><label for=\"username\" class=\"label usernamelabel\">Username</label><div id=\"username_container\"><div id=\"idcard-container\" class=\"mt8 mb16\" style=\"display: none\"><div id=\"idcard\"><img id=\"idcard-avatar\" class=\"avatar\" alt=\"\"><a href=\"javascript:void(0);\" id=\"clear_link\" class=\"clearlink\" onclick=\"LoginHint.clearExistingIdentity();\"><img alt=\"Log In with a Different Username\" class=\"clearicon\" src=\"/img/clear.png\"></a><span id=\"idcard-identity\"></span></div></div><input class=\"input r4 wide mb16 mt8 username\" type=\"email\" value=\"\" name=\"username\" id=\"username\" aria-describedby=\"error\" style=\"display: block;\"><input type=\"hidden\" name=\"ExtraLog\" value=\"%5B%7B%22width%22:1920%7D,%7B%22height%22:1080%7D%5D\"></div></div><label for=\"password\" class=\"label\">Password</label><input class=\"input r4 wide mb16 mt8 password\" type=\"password\" id=\"password\" name=\"pw\" aria-describedby=\"error\" onkeypress=\"checkCaps(event)\" autocomplete=\"off\"><div id=\"pwcaps\" class=\"mb16\" style=\"display:none\"><img id=\"pwcapsicon\" alt=\"Caps Lock is on.\" width=\"12\" src=\"/img/icon/capslock_blue.png\"> Caps Lock is on.</div><input class=\"button r4 wide primary\" type=\"submit\" id=\"Login\" name=\"Login\" value=\"Log In\"><div class=\"w0 pr ln3 p16 remember\"><input type=\"checkbox\" class=\"r4 fl mr8\" id=\"rememberUn\" name=\"rememberUn\"><label for=\"rememberUn\" class=\"fl pr db tn3\">Remember me</label><br></div></form><div class=\"w0 links bt pt16 mb20\"><a id=\"forgot_password_link\" class=\"fl small\" href=\"/secur/forgotpassword.jsp?locale=in&amp;lqs=locale%3Din\">Forgot Your Password?</a><a id=\"mydomainLink\" class=\"fr small\" href=\"javascript:void(0);\" onclick=\"DomainSwitcher.enterCustomDomain('Use Custom Domain',' | Salesforce')\">Use Custom Domain</a></div><span class=\"gidr-text-break\">or</span><a id=\"gidr-email-log-in-button\" class=\"button r4 wide primary\" href=\"https://welcome.salesforce.com?ref=lsc\"><img alt=\"\" src=\"/img/gidr/email.svg\" width=\"18\" height=\"18\"><span class=\"align-middle\">Log In with Email</span></a></div> and provide me the selenium java code. Instructions: Do not use ID if the value has number in it. Provide only java code and no explanations needed"
    }
  ],
  "model": "openai/gpt-oss-120b",
  "temperature": 0.1,
  "include_reasoning": true
}

Responses:
{
    "id": "chatcmpl-05c3cd03-dfb3-4548-bc41-499fe7397321",
    "object": "chat.completion",
    "created": 1775809694,
    "model": "openai/gpt-oss-120b",
    "choices": [
        {
            "index": 0,
            "message": {
                "role": "assistant",
                "content": "```java\nimport org.openqa.selenium.By;\nimport org.openqa.selenium.WebDriver;\nimport org.openqa.selenium.WebElement;\nimport org.openqa.selenium.chrome.ChromeDriver;\nimport org.openqa.selenium.support.ui.ExpectedConditions;\nimport org.openqa.selenium.support.ui.WebDriverWait;\nimport java.time.Duration;\n\npublic class SalesforceLogin {\n    public static void main(String[] args) {\n        // Set path to chromedriver executable if needed\n        // System.setProperty(\"webdriver.chrome.driver\", \"/path/to/chromedriver\");\n\n        WebDriver driver = new ChromeDriver();\n        driver.manage().window().maximize();\n\n        try {\n            driver.get(\"https://login.salesforce.com/\");\n\n            WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(15));\n\n            // Username field\n            WebElement username = wait.until(\n                    ExpectedConditions.visibilityOfElementLocated(By.id(\"username\"))\n            );\n\n            // Password field\n            WebElement password = driver.findElement(By.id(\"password\"));\n\n            // Remember me checkbox\n            WebElement rememberMe = driver.findElement(By.id(\"rememberUn\"));\n\n            // Login button\n            WebElement loginBtn = driver.findElement(By.id(\"Login\"));\n\n            // Forgot password link\n            WebElement forgotPwd = driver.findElement(By.id(\"forgot_password_link\"));\n\n            // Use custom domain link\n            WebElement customDomain = driver.findElement(By.id(\"mydomainLink\"));\n\n            // Log in with Email button\n            WebElement emailLoginBtn = driver.findElement(By.id(\"gidr-email-log-in-button\"));\n\n            // Example actions (fill and submit)\n            username.sendKeys(\"your.username@example.com\");\n            password.sendKeys(\"yourPassword\");\n            if (!rememberMe.isSelected()) {\n                rememberMe.click();\n            }\n            loginBtn.click();\n\n            // Additional interactions (optional)\n            // forgotPwd.click();\n            // customDomain.click();\n            // emailLoginBtn.click();\n\n        } finally {\n            // driver.quit(); // Uncomment to close the browser after execution\n        }\n    }\n}\n```",
                "reasoning": "We need to extract the DOM and provide Selenium Java code to interact with elements, but instructions: \"Do not use ID if the value has number in it.\" So we must avoid using IDs that contain numbers. For example, id=\"theloginform\" (no number) okay. id=\"login_form\" (has underscore but no number). id=\"username\" (no number). id=\"password\" (no number). id=\"Login\" (capital L, no number). id=\"rememberUn\" (no number). id=\"forgot_password_link\" (no number). id=\"mydomainLink\" (no number). id=\"gidr-email-log-in-button\" (no number). However some IDs have numbers? Not in this snippet. But there are hidden inputs with id=\"pqs\" (no number). So we can use IDs generally, but instruction says \"Do not use ID if the value has number in it.\" Since none have numbers, we can use IDs. But maybe they want to avoid IDs like \"username_container\"? That has no number. So fine.\n\nWe need to provide Selenium Java code to extract the DOM? Probably to locate elements and maybe perform login. Provide code that uses By.id, By.cssSelector, By.xpath etc. Provide only Java code, no explanations.\n\nLet's craft code: import statements, WebDriver setup, navigate to page, locate username, password, login button, remember checkbox, forgot password link, custom domain link, email login button. Use appropriate locators avoiding IDs with numbers (none). Provide code snippet.\n\nWe'll output only Java code."
            },
            "logprobs": null,
            "finish_reason": "stop"
        }
    ],
    "usage": {
        "queue_time": 0.17213386,
        "prompt_tokens": 1105,
        "prompt_time": 0.063553625,
        "completion_tokens": 734,
        "completion_time": 2.208018483,
        "total_tokens": 1839,
        "total_time": 2.271572108,
        "completion_tokens_details": {
            "reasoning_tokens": 321
        }
    },
    "usage_breakdown": null,
    "system_fingerprint": "fp_46d8af1c62",
    "x_groq": {
        "id": "req_01knv83058f3f97w080k4cx6fd",
        "seed": 90714351
    },
    "service_tier": "on_demand"
}

2. From the above response converting it to the Code

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.ExpectedConditions;
import org.openqa.selenium.support.ui.WebDriverWait;
import java.time.Duration;

public class SalesforceLogin {
    public static void main(String[] args) {
        // Set path to chromedriver executable if needed
        // System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");

        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();

        try {
            driver.get("https://login.salesforce.com/");

            WebDriverWait wait = new WebDriverWait(driver, Duration.ofSeconds(15));

            // Username field
            WebElement username = wait.until(
                    ExpectedConditions.visibilityOfElementLocated(By.id("username"))
            );

            // Password field
            WebElement password = driver.findElement(By.id("password"));

            // Remember me checkbox
            WebElement rememberMe = driver.findElement(By.id("rememberUn"));

            // Login button
            WebElement loginBtn = driver.findElement(By.id("Login"));

            // Forgot password link
            WebElement forgotPwd = driver.findElement(By.id("forgot_password_link"));

            // Use custom domain link
            WebElement customDomain = driver.findElement(By.id("mydomainLink"));

            // Log in with Email button
            WebElement emailLoginBtn = driver.findElement(By.id("gidr-email-log-in-button"));

            // Example actions (fill and submit)
            username.sendKeys("your.username@example.com");
            password.sendKeys("yourPassword");
            if (!rememberMe.isSelected()) {
                rememberMe.click();
            }
            loginBtn.click();

            // Additional interactions (optional)
            // forgotPwd.click();
            // customDomain.click();
            // emailLoginBtn.click();

        } finally {
            // driver.quit(); // Uncomment to close the browser after execution
        }
    }
}