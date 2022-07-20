from bs4 import BeautifulSoup
import requests
import re


cod = "https://www.olx.ro/d/animale-de-companie/?page="

for i in range(1, 26):

    url = cod + str(i)

    html_text = requests.get(url).text
    soup = BeautifulSoup(html_text, 'lxml')
    anunturi = soup.find_all('a', class_ ='css-1bbgabe')  # css-u2ayx9

    for anunt in anunturi:

        link = anunt.get("href")
        link = "https://www.olx.ro" + link
        print(link)

        text = requests.get(link).text
        supa = BeautifulSoup(text, 'lxml')

        titles = supa.find_all('h1', class_ = 'css-r9zjja-Text eu5v0x0')

        for index in range(len(titles)):

            title = titles[index].text
            print(title)

            gasit = re.search("ciobanes(?:c+|ti+)*|labrado(?:r+|ri+)|bicho(?:n+|ni+)|pu(?:i+|sor+|sori+|uti+)|pisi(?:c+|ca+|ci+|cuta+|cute+)|papaga(?:l+|li+)|hamste(?:r+|ri+)|bulldo(?:g+|gi+)|pest(?:e+|i+|sor+|sori+)|por(?:c+|cusor+|ci+|cusori+)", title)
            if(gasit):
                gasit = str(gasit)
                poz1 = gasit.find("\'")
                poz2 = gasit.rfind(("\'"))
                print("Tipul este : " + str(gasit[poz1+1:poz2]))
