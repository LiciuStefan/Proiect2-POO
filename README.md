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
'''C++
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
'''
Operatorii de afisare folosesc functii virtuale mostenite pentru afisare.
