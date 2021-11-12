# web-scraping
indeed data 

code



import requests
from bs4 import BeautifulSoup

url = requests.get("https://in.indeed.com/jobs?q=Data+Analyst&l=&ts=1631182787757&rq=1&rsIdx=1&fromage=last&newcount=4446")
soup = BeautifulSoup(url.content, 'html.parser')
results = soup.find_all('div',class_='job_seen_beacon')

for result in results:
    location = result.find('div',class_="companyLocation")
    company = result.find('span',class_="companyName")
    salary = result.find('div',class_="salary-snippet")
    print(f"position: {location.text}")
    print(f"company: {company.text}")

    if salary:
        print(f"salary:{salary.text}",end='\n'*2)
    else:
        print("salary not mention",end='\n'*2)



