## Uno
zadanie 1
#Funkcje trygonometryczne (sin, cos, tan, cot)

```matlab
% Sinus kąta w radianach
sin(0.5)
% => ans = 0.4794

% Cosinus kąta w radianach
cos(1)
% => ans = 0.5403

% Tangens kąta w radianach
tan(-78)
% => ans = 0.5992

% Cotangens kąta w radianach (cot(x) = 1 / tan(x))
1 / tan(0.8)
% => ans = 1.1918
```

#Odwrotne funkcje trygonometryczne (asin, acos, atan, acot)
```matlab
% arcsin z 0.5 (daje kąt w radianach)
asin(0.5)
% => ans = 0.5236 (czyli π/6)

% arccos z 0.88992
acos(0.88992)
% => ans = 0.4736 rad

% arctan z π
atan(pi)
% => ans = 1.2626 rad

% arcctg z 1 (czyli acot(1))
atan(1)  % bo acot(1) = atan(1)
% => ans = 0.7854 (czyli π/4)
```

#Zamiana jednostek: stopnie ↔ radiany
```matlab
% Zamiana 85 stopni na radiany
deg2rad(85)
% => ans = 1.4835 rad


% Zamiana radianów na stopnie (np. atan(pi))
rad2deg(atan(pi))
% => ans = 72.3432 stopnia
```

#Połączone przykłady (bardziej złożone)
```matlab
% Oblicz cosinus 85 stopni
kat = deg2rad(85);
cos(kat)
% => ans = 0.0872


% Oblicz kąt (w stopniach), którego tangens wynosi π
kat_rad = atan(pi);
kat_deg = rad2deg(kat_rad)
% => ans = 72.3432


% Oblicz cotangens kąta 45 stopni
cot_kat = 1 / tan(deg2rad(45))
% => ans = 1
```



## Dos
Zadanie 1 – pierwiastki równania x^2 + 11x + 9 = 0
```matlab
a = 1; b = 11; c = 9;
d = b.^2 - 4*a*c;
r1 = (-b + sqrt(d)) / (2*a);
r2 = (-b - sqrt(d)) / (2*a);
minRoot = min([r1, r2]);
minRoot4 = round(minRoot*1e4)/1e4;    % zaokrąglij do 4 miejsc
fprintf('Mniejszy pierwiastek: %.4f\n', minRoot4);
```

Zadanie 2 – wektor od -50 do 130, operacje i suma na pozycjach nieparzystych
```matlab
v = -50:130;           % wektor podstawowy
v = sin(abs(v));       % sinus wartości bezwzględnych
v = v * 7;             % mnożenie przez 7
v = v + 19;            % dodanie 19
sumOdd = sum(v(1:2:end));
sumOdd4 = round(sumOdd*1e4)/1e4;  % zaokrąglenie
fprintf('Suma elementów na nieparzystych pozycjach: %.4f\n', sumOdd4);
```

Zadanie 3 – dowolna liczba z [13,30] i v z 185 kolejnych wielokrotności
```matlab
n = 17;                % tu wybierz swoją liczbę z przedziału [13,30]
v3 = n * (1:185);      % wektor 185 kolejnych wielokrotności
r = mod(v3, 37);       
mask = (r < 9) | (r > 21);
count = sum(mask);
fprintf('Ilość elementów z resztą <9 lub >21: %d\n', count);
```

## Tres

Generowanie wektora złożonego z liczb parzystych.

```matlab
% Sprawdzenie liczby elementów wektora (w przedziale 14-98 co drugi)
length(14:2:98)
```

Tworzenie wektora który zawiera punkty podziału odcinka [-4;40] na 440 równych części oraz obliczenie sumy elementów które są mniejsze od zera lub zawierają się w przedziale domkniętym [0.2;5].

```matlab
% Wektora zawierający punkty podziału odcinka [-40;40] na 440 równych części (do 440 trzeba zawsze dodać 1)
w = linspace(-4,40,441);

% Elementy wektora mniejsze od zera lub zawierają się w przedziale domkniętym [0.2;5]
e = w(w < 0 | (w >= 0.2 & w <= 5));

% Obliczamy sume
sum(e)
```

Trójkąt pascala

```matlab
% Literce a przypisujemy macierz stopnia 10 zawierającą trójkąt Pascala.
n = 10;
a = pascal(n);

% Usuwamy kolumny: piątą, ósmą i dziesiątą
kolumny_usun = [5,8,10];
a(:,kolumny_usun) = [];

% Usuwamy 3 ostatnie wiersze
a(end-2:end, :) = [];

% Dodajemy wiersz na końcu: liczba 5.4 powtórzona odpowiednią liczbę razy
liczba_kolumny = 5.4;
kolumna = repmat(liczba_kolumny, size(a,1), 1);
a = [a, kolumna];

% Dodajemy wiersz na końcu: liczba -1.0 powtórzona odpowiednią liczbę razy
liczba_wiersza = -1.0;
wiersz = repmat(liczba_wiersza, 1, size(a,2));
a = [a; wiersz];

% Zmieniamy ostatni element macierzy na 0
a(end,end) = 0;

% Obliczamy wyznacznik i podajemy z dokładnością do 1 miejsca po przecinku
d = det(a);

fprintf("%.2f\n", d);

```

# Cuatro

soon XD

# Cinco
Prawdopodobieństwo empiryczne

Zadanie 1
Wylosuj liczbe 0 lub 1 z takim samym prawdopodobieństwem (randi rand)

Zadanie 2
rzucamy sześcienną kostką 5 razy

1
Wylosuj 1 zestaw rzutów.
2
wylosuj 5 takich rzutów

Zadanie 3
oblicz sume oczek ze wszystkich 5 rzy\utów
k
3 wylosuj 10^6 zestawówó rzutów

Zadanie 4
rzucamy kostką 5 razy, oblicz prawdopodobieństwo empiryczne że suma oczek będzie mniejsza niż 15


Zadanie 5

oblicz prawdowieńsfwo mpiryczne że wypadnie 1 lub 2

Zadanie 6

oblicz prawdopodobieństwo żę trójka wypadnie 2 razy

Zadanie 7
czym się różni polecenia 
(r) round(10*rand)

(f) floor(10*rand)

prawdopodobieństwo 0-9 jest wyższe w (f)

Zadanie 8
Oblicz wartość oczekiwaną rzutu kostką sześcienną

Zadanie 9
Oblicz wartość oczewiwane zmiennych r oraz f.

(r) round(10*rand)
(f) floor(10*rand)

Zadanie 10 Oblicz wariacje dla zmiennych:
a)rzut kostką sześcienną

to były zadania na matmie i można coś ugotować z nich co?
