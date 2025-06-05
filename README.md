from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# Launch browser
driver = webdriver.Chrome()

# Navigate to the login page
driver.get("https://practicetestautomation.com/practice-test-login/")

# Enter valid credentials
driver.find_element(By.ID, "username").send_keys("student")
driver.find_element(By.ID, "password").send_keys("Password123")

# Click the login button
driver.find_element(By.ID, "submit").click()

# Assertions
assert "/logged-in-successfully/" in driver.current_url
assert "Congratulations" in driver.page_source
assert driver.find_element(By.LINK_TEXT, "Log out").is_displayed()

print("Positive login test passed successfully.")

# Close the browser
driver.quit()
