# Zadanie liczenie efektywności algorytmów

Zadanie dotyczy użycia wzorów na oszacowanie przyspieszenia oraz efektywności programu równoległego przy użyciu danej liczby procesorów.

![](./img_zad/zad2/zad2.1.png)\
*zad 2*

## Wstęp teoretyczny
* prawo Amdahla - jest używane do znajdowania maksymalnego spodziewanego zwiększenia wydajności wraz ze wzrostem ilości uzytych procesorów. Ważne jest rozdzielenie procentowego udziału części sekwencyjnej **s**, oraz równoległej **r** kodu. 

> Rozpatruje się dowolne instancje o stałym rozmiarze.

![](./img_zad/zad2/zad2_wykres.png)
*rys 2.1*

## Wzory
![](./img_zad/zad2/zad2_wzor.png)\
*rys 2.2*

* f(x) - fukcja przyspieszenia
* x - ilość procesorów

### Efektywność liczy się za pomocą wzoru\
**Ep = Sp / p**

Warto zauważyć, że 
* gdy ilość procesorów rośnie do nieskończoności, wpływ części równoległej dąży do zera. Oznacza to, że wraz ze wzrostem procesorów zmniejszają się korzyści płynące z ich użycia. W praktyce występują różnego rodzaju opóźnienia wynikające z komunikacji procesorów - ma to wpływ na czas wykonania programu. Wniosek jest tak, że warto zwiększać ilość procesorów tylko do pewnego momentu, ponieważ te przestają mieć wpływ na przyspieszenie programu. Jest ono ograniczone od góry!
* gdy część równoległa dąży do jedynki, przyspieszenie jest równa **p**. Oznacza to, że występuje idealne zrównoleglenie - wpływ części sekwencyjnej jest pomijalny. Można to interpretować tak, że każdy procesor zajmuje się w całości "swoją częścią" danego zadania (nie czeka na żadne dane, nie ma opóźnień w komunikacji). Ta sytuacja w praktyce raczej nie jest zauważalna, jednakże czysto hipotetycznie możliwa. Efektywność w tej sytuacji jest równa 1 (maksymalna wartość).

> Przyspieszenie możliwe do osiągnięcia jest ograniczone. Nie można w nieskończoność zwiększać przyspieszenia. \ 
Czym większy procent części rónoległej, tym granica przyspieszenia jest później.

* prawo Gustafsona - stanowi, że każdy wystarczająco duży problem może być efektywnie zrównoleglony. W odróżnieniu do prawa Amdahla, to jest skalowalne. Prawo Gustafsona pozwala na analize rosnącej instancji rozważanego problemu. Dobierana jest ilość procesorów w taki sposób, aby przyspieszenie **rosło liniowo** wraz ze wzrostem problemu. 

> Rozpatruje się przetwarzanie szeregu instancji problemu o rosnącym rozmiarze i stałym czasie przetwarzania równoległego.

![](./img_zad/zad2/zad2_wzorGustaw.png)\
*rys 2.3*

---

## Zadanie - prawo Amdahla
Wzory z którego należy skorzystać zostały podane na rysunku 2.1, za ich pomocą należy utworzyć prosty układ równiań.

### Dane
* ilość procesorów = **p** = 5 
* przyśpieszenie = **Sp** = 3

### Obliczenia
* 3 = 1 / (s + (1-s)/5)
* s = 1/6
* r = 5/6

Mając **s** oraz **r** można teraz obliczyć dalszą część, czyli \
a) jakie przyspiszenie zostanie osiągnięte przy użyciu 10 procesorów \
b) ile conajmniej jest potrzebne procesotów do osiągnięcia przyspieszenia Sp = 10.

* Sp = 1 / `(`1/6 + (`(`5/6`)` / 10)`)` = 1 / `(`1/6 + 5/60`)` = 1 / (15/60) = **4**

Odp.: Przy zastosowaniu 10 procesorów przyspieszenie byłoby równe **4**.

* 10 = 1 / `(` 1/6 + (5/6 / x) `)` --> x = **-12.5**

Odp.: Wynik jest ujemny, mamy zatem sprzeczność. Nie jest możliwy taka ilość procesorów, aby przyspieszenie było conajmniej równe **10**.