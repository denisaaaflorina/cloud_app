# cloud_app
proiect cloud computing

Domeniul web a evoluat foarte mult in ultimii ani, iar acum ne aflam in plina ascensiune a platformelor complexe, a serviciilor cloud si a API-urilor care furnizeaza non-stop date, fata de acum 10-15 ani cand web-ul era dominat de website-uri simple.

Termenul de API este acronimul de la Application Programing Interface si reprezinta un set de functii si proceduri care permit crearea de aplicatii care acceseaza caracteristicile sau datele unui sistem de operare, aplicatie sau alt serviciu.

API-urile sunt instrumente vitale mai ales pentru companiile din toate industriile. Acestea permit unui program sa fie utilizat de catre altul. Sunt un mijloc prin care doua programe diferite sunt capabile sa comunice. API-urile permit companiilor sa isi dezvolte afacerile mai repede decat oricand. La fel ca Web-ul API-urile conduc un nou val de inovatie axat pe partajarea serviciilor. 

Representational State Transfer (REST) este un stil arhitectural modern care defineste modul in care interactioneaza serviciile web. Acesta se bazeaza pe cereri HTTP (e.g.: GET, POST, PUT, DELETE) pentru a manipula informatia si pe media-types (e.g.: JSON) pentru a stabili cum arata informatia transferata.

Un API de tip REST este un serviciu Web care permite interactiunea prin mecanisme REST.

In cadrul acestui proiect am realizat o aplicatie care foloseste 2 API-uri Rest.

Aceasta aplicatie ofera posibilitatea de a obtine retete de mancare in functie de un ingredient introdus, precum si un cocktail generat aleatoriu pentru cei care nu au inspiratie si vor sa incerce ceva nou.

API-urile Rest folosite:
-	TheMealDB API
-	TheCocktailDB API

API-ul TheMealDB este o baza de date open source care ofera retete cu fotografii din intreaga lume. Este un API JSON simplu, care include componente PNG transparente de inalta calitate, descarcari de imagini alimentare si navigare in flux alimentar. TheMealDB ofera o sursa de date online API gratuita, preluata de pe forumurile Kodi, ca o modalitate de a cauta retete populare.

API-ul TheCocktailDB este la fel ca si API-ul TheMealDB, fiind o baza de date open source gratuita cu o multime de bauturi si cocktail-uri. Cu ajutorul acestui API se pot obtine fotografii cu bauturi, ingrediente acestora, precum si retetele necesare.

I.	TheMealDB API

HTML

![image](https://user-images.githubusercontent.com/74535379/117855018-ba918380-b292-11eb-82f2-810f4a8b0971.png)

Cele mai importane parti din HTML sunt
-	Butonul #search-btn
-	Div #meal
-	Butonul #recipe-close-btn
-	Div #meal-details-content

JavaScript

Vom folosi butonul #search-btn pentru a face o cerere catre API, care va trimite inapoi cateva date pe care le vom introduce in div-ul #meal, care in acest caz actioneaza ca un container.

![image](https://user-images.githubusercontent.com/74535379/117855084-cd0bbd00-b292-11eb-924c-f55f1b73f84d.png)

![image](https://user-images.githubusercontent.com/74535379/117855106-d39a3480-b292-11eb-99be-597158cd5412.png)


Inainte de a continua codul JavaScript analizam putin API-ul. API-ul ofera posibilitatea de a filtra retele in functie de ingredientul dorit, iar daca analizam URL-ul de pe site www.themealdb.com/api/json/v1/1/filter.php?i=chicken_breast  putem observa ca ne expune toate retele care au ingredientul “chicken breast”:

![image](https://user-images.githubusercontent.com/74535379/117855158-e3b21400-b292-11eb-8722-aaa7e59566f3.png)

Aceste date ne ofera informatii pe care vrem sa le prezentam in aplicatie:
Numele retetei -> strMeal 
Fotografia preparatului -> strMealThumb
Id-ul retetei -> idMeal

![image](https://user-images.githubusercontent.com/74535379/117855212-ef053f80-b292-11eb-9121-26d299fa5ac6.png)


Am folosit Fetch API care automat face request HTTP pe GET. Se foloseste URL-ul API-ului catre care dorim sa facem solicitarea GET, urmata in final de un raspuns JSON (response/res).

API-ul Fetch ofera o metodă fetch () pe care o putem utiliza pentru a efectua cereri. Aceasta metoda returneaza o promisiune pe care o utilizam pentru a prelua raspunsul(response) cererii/solicitarii (request).

Pentru a putea obtine reteta in functie de ingredient vom analiza URL-ul oferit de SITE www.themealdb.com/api/json/v1/1/lookup.php?i=52772 din care putem prelua urmatoarele date:
Numele retetei -> strMeal
Categoria retetei ->  strCategory
Fotografia preparatului -> strMealThumb
Videoclip al retetei pe Youtube -> strYoutube
Ingredientele si masurile -> strIngredientsX & strMeasureX (X reprezentand al n-lea ingredient si masura sa)

![image](https://user-images.githubusercontent.com/74535379/117855279-fe848880-b292-11eb-81ba-513e52b61b17.png)

![image](https://user-images.githubusercontent.com/74535379/117855296-047a6980-b293-11eb-93fa-184579adde0f.png)

La fel ca mai devreme am folosit Fetch API pentru a face request HTTP pe GET pentru a obtine retetele. Acestea fiind afisate intr-un modal (popup window)

II.	TheCocktailDB API

HTML

![image](https://user-images.githubusercontent.com/74535379/117855352-122fef00-b293-11eb-99d2-8d250fd86cc8.png)

Cele mai importane parti din HTML sunt:
-	Butonul #get_cocktail
-	Div #cocktail

JavaScript

Vom folosi butonul pentru a face o cerere catre API, care va trimite inapoi date pe care le vom introduce in div-ul #cocktail care, si-n acest caz, actioneaza ca un container.

![image](https://user-images.githubusercontent.com/74535379/117855404-2116a180-b293-11eb-896c-51b729eefa2f.png)

Inainte de a continua codul JavaScript analizam putin API-ul. Dupa cum se poate observa din URL https://www.thecocktaildb.com/api/json/v1/1/random.php primim un cocktail aleatoriu (daca facem refresh la browser vom primi mereu un alt cocktail). Cand facem o solicitare GET catre acel punct final, acesta trimite inapoi un raspuns JSON, pe care il putem analiza pentru a prelua datele dorite.

Practic primim o serie de cocktail-uri, dar cu un singur articol - cel generat aleatoriu. Si acest articol contine toate datele pe care vrem sa le prezentam aplicatie:

-	Numele cocktailului ->  strDrink
-	categoria cocktailului -> strCategory
-	imagine cocktail -> strDrinkThumb
-	ingredientele si masurile -> strIngredientX si strMeasureX - X reprezentand al n-lea ingredient si masura sa

![image](https://user-images.githubusercontent.com/74535379/117855454-2ecc2700-b293-11eb-8851-96d6217ad726.png)

Acum ca avem butonul, vom adauga un event listener pentru evenimentul de clic si in interior vom face o cerere catre API:

![image](https://user-images.githubusercontent.com/74535379/117855621-53280380-b293-11eb-95b7-b7b35924b52f.png)

Folosim Fetch API pentru a face request. Se foloseste adresa URL a API-ului catre care dorim sa facem o solicitare GET si vom primi inapoi o promisiune. La final vom avea un raspuns JSON (res). 

Dupa cum am mentionat mai sus, API returneaza matricea de cocktail-uri, dar numai cu un element in ea, asa ca vom trece acel articol (la index 0) in functia noastra createCocktail, pe care o vom defini in continuare.

![image](https://user-images.githubusercontent.com/74535379/117855665-5fac5c00-b293-11eb-91a0-54147c3505e4.png)

Practic, scopul intregii functii este de a obtine raspunsul JSON, de a-l analiza si de a-l transforma intr-o componenta HTML.

Am creat o bucla for care merge de la 1 la 20 si verifica daca bautura/cocktail-ul are perechea corespunzatoare ingredient-masura. Daca da, il introducem in gama de ingredient, aaca nu mai exista ingrediente, bucla for se opreste cu break.

![image](https://user-images.githubusercontent.com/74535379/117855746-7357c280-b293-11eb-9ba6-93e2c9530f62.png)

Apoi, cream newInnerHTML care va detine intregul HTML. In el analizam proprietatile ramase pe care dorim sa le afisam.
Setam intregul newInnerHTML ca si innerHTML-ul al containerului cocktail -> acest lucru va completa div-ul cu toate informatiile.
Intregul proces se va repeta de fiecare data cand este apasat butonul #get_cocktail.
In final se face deploy la aplicatie pe https://www.heroku.com , aplicatia aratand astfel:

![image](https://user-images.githubusercontent.com/74535379/117856869-cf6f1680-b294-11eb-8d5d-e98176e69ef6.png)

Se observa faptul ca una dintre optiunile oferite de aplicatie este cea de a ne introduce un ingredient, urmand ca aplicatia sa ne ofere mai multe retete din care putem sa alegem. Avem la dispozitie atat reteta preparatului, cat si un videoclip pe care putem sa-l urmarim pentru realizarea retetei.

![image](https://user-images.githubusercontent.com/74535379/117856898-da29ab80-b294-11eb-9f6b-896caa30f140.png)

Cea de-a doua optiune oferita de aplicatie este obtinerea unui cocktail random de fiecare data cand apasam pe butonul “Get cocktail”.

![image](https://user-images.githubusercontent.com/74535379/117857047-080ef000-b295-11eb-867f-32c0238179fe.png)

Aceasta aplicatie  este utila atunci cand nu ai inspiratie si vrei sa incerci ceva nou, atat din punct de vedere al mancarii, cat si din punct de vedere al bauturii.

Referinte:
https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

https://developers.google.com/web/updates/2015/03/introduction-to-fetch

https://www.redhat.com/en/topics/api/what-is-a-rest-api

