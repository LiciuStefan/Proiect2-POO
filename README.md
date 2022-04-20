# Proiect2-POO
Al doilea proiect realizat in cadrul cursului de OOP, anul I, Facultatea de Matemetica si Informatica, Universitatea din Bucuresti
Programul simuleaza formarea unor forme geometrice si formule trigonometrice.
Clase: Punct, Forma_Geometrica, Patrat, Dreptunghi, Romb, Triunghi, Cerc.

Clasa Punct:
Contine doua date membre, abscisa punctului (x) si ordonata punctului (y) pentru a retine pozitia unui punct intr-un sistem de coordonate xOy.

Clasa Forma_Geometrica:
Clasa abstracta, nu se pot defini obiecte de tipul sau. Functii virtuale pentru suprascrierea in mostenire, data membra statica pentru a pastra numarul de obiecte derivate create. Foloseste encapsularea, avand o data membra alocata dinamic de tipul Punct, reprezentand punctul din stanga jos al formei geometrice. Contine metode virtuale pure pentru calculul ariei si al volumului.

Clasa Patrat:
Clasa mostenita din clasa Forma_Geometrica, contine in plus ca data membra de tipul float latura patratului. Sunt suprascrise metodele virtuale din clasa parinte si operatorii de citire, scriere si operatorul =.


Clasa Dreptunghi:
Clasa mostenita din clasa Patrat, contine in plus ca data membra de tipul float a doua latura a dreptunghiului. 

Clasa Romb:
Clasa mostenita din clasa Patrat, contine in plus ca data membra de tipul Punct, alocata dinamic, coordonatele punctului din dreapta sus (colt opus).
Pentru a calcula aria, obiectul de tip romb trebuie sa aiba doua laturi paralele cu axa Ox.

Clasa Triunghi:
Clasa mostenita din clasa Forma_Geometrica.
In cazul acestei clase, data punct_stanga_jos va reprezenta primul punct al triunghiului. Celelalte doua date membre de tip Punct reprezinta celelalte doua puncte ale triunghiului si sunt alocate dinamic. Contine metode pentru calculul lungimilor laturilor si al medianelor din fiecare colt in parte.

Clasa Cerc:
Clasa mostenita din clasa Forma_Geometrica
In cazul acestei clase, data punct_stanga_jos va reprezenta centrul cercului. Contine in plus ca date membre raza de tipul float si data statica pi.

Toti operatorii de citire suprascrisi verifica cazurile de exceptie, care apoi sunt tratate in main folosind try...catch.
```C++
//Ex clasa Patrat
istream& operator>>(istream& stream, Patrat& P)
{
	Forma_Geometrica* F = &P;
	cin >> *F;
	stream >> P.latura;
	if (!stream.good() || P.latura <= 0)
	{
		stream.clear();
		stream.ignore(INT_MAX, '\n');
		P.inaltime = 0.0;
		P.punct_stanga_jos = new Punct(0.0, 0.0);
		throw invalid_argument("Argument invalid! Datele trebuie sa fie de tipul: float, float, float, float, iar latura trebuie sa fie pozitiva\n");
	}

	return stream;
}
//In main:
cout << "Introduceti: asbscisa punctului stanga jos(float), ordonata punctului stanga jos(float), inaltimea(float) si lungimea laturii(float)\n";
		label_Patrat:
			try {
				cin >> P;
			}
			catch (invalid_argument arg)
			{
				cout << arg.what() << '\n';
				goto label_Patrat;
			}
			Forma_Geometrica* B = new Patrat(P); //upcast
			cout << *B << '\n';
			Forme.push_back(make_pair(B, "Patrat"));
```
Operatorii de afisare folosesc functii virtuale mostenite pentru afisare.
```
void  Patrat::afisare(ostream& stream)
{
	Forma_Geometrica::afisare(stream);
	cout << ' ' << this->latura;
}
ostream& operator<<(ostream& stream, Patrat& P)
{
	P.afisare(stream);
	return stream;
}
```
Programul contine si un meniu interactiv in source.cpp pentru a ilustra conceptele aplicate. Acesta trateaza exceptiile pentru input invalid.
**Ex:**
---------------------------------------------------Meniu-----------------------------------------------</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
fqljfqopfj o qfopqjifp qj qfoqjfqpf</br>
Input invalid!</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>

**Ex input pentru adaugare forma geometrica:**</br>
1</br>
Da</br>
2</br>
1<br>
0.1 0.1 2.34 5.56</br>

**Output:**</br>
---------------------------------------------------Meniu-----------------------------------------------</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
1</br>
Triunghi 0 1 10 2 2 3 1</br>
Cerc 10 0 20 100</br>
Doriti o alta actiune?</br>
Da</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
2</br>
Alegeti natura formei geometrice:</br>
1. Patrat</br>
2. Dreptunghi</br>
3. Romb</br>
4. Triunghi</br>
5. Cerc</br>
1</br>
Introduceti: asbscisa punctului stanga jos(float), ordonata punctului stanga jos(float), inaltimea(float) si lungimea laturii(float)</br>
0.1 0.1 2.34 5.56</br>
Doriti o alta actiune?</br>
da</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
1</br>
Triunghi 0 1 10 2 2 3 1</br>
Cerc 10 0 20 100</br>
Patrat 0.1 0.1 2.34 5.56</br>
Doriti o alta actiune?</br>
**Ex stergere element:**</br>
**Input:**</br>
1</br>
da</br>
3</br>
1</br>
da</br>
1</br>

****Output:**
Introduceti cifra corespunzatoare actiunii dorite:</br>
1</br>
Triunghi 0 1 10 2 2 3 1</br>
Cerc 10 0 20 100</br>
Patrat 0.1 0.1 2.34 5.56</br>
Doriti o alta actiune?</br>
Da</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
3</br>
Triunghi 0 1 10 2 2 3 1</br>
Cerc 10 0 20 100</br>
Patrat 0.1 0.1 2.34 5.56</br>
Introduceti pozitia corespunzatoare obiectului pe care doriti sa il stergeti:</br>
1</br>
Elementul a fost sters</br>
Doriti o alta actiune?</br>
da</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
1</br>
Triunghi 0 1 10 2 2 3 1</br>
Patrat 0.1 0.1 2.34 5.56</br>
**Ex input calcul arie:**</br>
4</br>
1</br>

**Output:**</br>
0.Exit</br>
1.Vezi forme geometrice</br>
2.Adauga forma geometrica</br>
3.Sterge forma geometrica</br>
4.Calcul arie forma geometrica</br>
5.Calcul volum forma geometrica</br>
6.Calculeaza lungime laturi triunghi</br>
7.Centru de greutate triunghi</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
4</br>
Triunghi 0 1 10 2 2 3 1</br>
Patrat 0.1 0.1 2.34 5.56</br>
Introduceti pozitia corespunzatoare obiectului a carui arie se calculeaza:</br>
1</br>
30.9136</br>
Doriti o alta actiune?</br>

**Ex calcul volum:**</br>
**input:**</br>
5</br>
1</br>

**Output:**</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
5</br>
Triunghi 0 1 10 2 2 3 1</br>
Patrat 0.1 0.1 2.34 5.56</br>
Introduceti pozitia corespunzatoare obiectului a carui volum se calculeaza:</br>
1</br>
72.3378</br>
Doriti o alta actiune?</br>

**Ex calcul lungimi laturi triunghi dat de la tastatura:**</br>
**Input:**</br>
6</br>
2</br>
0 0 2.314 5.231 7.241 10.41 -3.24</br>

**Output:**</br>
Introduceti cifra corespunzatoare actiunii dorite:</br>
6</br>
Alegeti una din optiuni:</br>
1. Element deja existent in vector</br>
2. Element nou</br>
2</br>
Introduceti: abscisa primului punct(float), ordonata primului punct(float), inaltimea(float), abscisa punctului 2(float), ordonata punctului 2(float), abscisa punctului 3(float), ordonata punctului 3(float)</br>
0 0 2.314 5.231 7.241 10.41 -3.24</br>
Lungimea laturii AB este:</br>
8.93283</br>
Lungimea laturii AC este:</br>
10.9026</br>
Lungimea laturii BC este:</br>
11.6907</br>
Doriti o alta actiune?</br>

**Ex calcul coordonate centru de greutate triunghi:**</br>
**Input:**</br>
7</br>
2</br>
-1.1 3.21 4 4.66 -2.45 8.99 7.65</br>

**Output:**</br>
7</br>
Alegeti una din optiuni:</br>
1. Element deja existent in vector</br>
2. Element nou</br>
2</br>
Introduceti: abscisa primului punct(float), ordonata primului punct(float), inaltimea(float), abscisa punctului 2(float), ordonata punctului 2(float), abscisa punctului 3(float), ordonata punctului 3(float)</br>
-1.1 3.21 4 4.66 -2.45 8.99 7.65</br>
Centrul de greutate al triunghiului are coordonatele:</br>
4.18333 2.80333</br>
Doriti o alta actiune?</br>
