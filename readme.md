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
Pierwsze Zadanie Skrypt
```matlab
# A wpisujemy dane x y z, jeżeli nie ma jednych z xyz wpisujemy poprostu 0 w miejsce w którym x lub y lub z
# powinno byc, jeżeli jest sam np x wpisujemy 1 (podmień juz aktualnie wpisane dane)
# B wpisujemy dane po prawej stronie od góry (podmień juz aktualnie wpisane dane)
A = [1 1 -14; 0 1 -5; -1 2 -1];
B = [7; 8; 17];

# Tutaj podajesz odpowiedzi po przecinku (podmieniasz wartości)
odp = [
 -17, 18, 2;
  89, 58, 3;
  17, 18, 2;
 -10, 3, -1;
 -28, -2, -3;
 -1, 8, 0;
 -1, 9, 0;
 -28, -7, -3;
  8, 3, 1;
 89, 58, 10
];

for i = 1:size(odp,1)
    x = odp(i,:)';
    if norm(A*x - B) < 1e-6
        printf("Odpowiedzi z (%d, %d, %d) są rozwiązaniem\n", x(1), x(2), x(3));
    end
end
```
```matlab
Trzecie Zadanie Skrypt
# A wpisujemy dane x y z, jeżeli nie ma jednych z xyz wpisujemy poprostu 0 w miejsce w którym x lub y lub z
# powinno byc, jeżeli jest sam np x wpisujemy 1 (podmień juz aktualnie wpisane dane)
# B wpisujemy dane po prawej stronie od góry (podmień juz aktualnie wpisane dane)
A = [-3 3 -3; 10 33 -3; 37 0 30];
B = [6; 22; 4];
x = A \ B;
fprintf('x = %d, y = %d, z = %d\n', x(1), x(2), x(3));
iloczyn = x(1) * x(2) * x(3);
fprintf('Iloczyn liczb(Wynik): x * y * z = %d\n', iloczyn);
```
