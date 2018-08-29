# airflow-tutorials

環境 : GCP Ubuntu 1604

---

Clone [Lee 大](https://leemengtaiwan.github.io/a-story-about-airflow-and-data-engineering-using-how-to-use-python-to-catch-up-with-latest-comics-as-an-example.html)的 Code 做為修改

主要是因為在我的環境啟動時跑出現關於 chrome 相關的 Error，所以增加啟動參數

```python
def check_comic_info(**context):
    metadata = context['task_instance'].xcom_pull(task_ids='get_read_history')
    options = webdriver.ChromeOptions()
    options.binary_location = '/opt/google/chrome/google-chrome'
    options.add_argument('--headless')
    options.add_argument('--no-sandbox')
    options.add_argument('--disable-dev-shm-usage')
    driver = webdriver.Chrome('/usr/local/bin/chromedriver',
             chrome_options=options)
    driver.get('https://www.cartoonmad.com/')
    print("Arrived top page.")
```
