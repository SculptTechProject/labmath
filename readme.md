## Wejściówka nr 1
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

% Skrypt 2 zad - suma wielokrotności liczby
```matlab
a = 20;       % wartość wielokrotności
n = 2815;     % ilość elementów

v = a * (1:n);
suma = sum(v);

fprintf('Suma: %d\n', suma);
```

% Skrypt 3 zad - Dzielenie dwóch wyrażeń i zaokrąglenie w dół
```matlab
liczba_logarytmu = 5;
mnoznik_log = 11920928955078125;

z = log(5^3 * mnoznik_log) / log(liczba_logarytmu);

kat_stopnie = 89.996;
y = exp(11) + tan(deg2rad(kat_stopnie));

n = floor(y / z);
fprintf('n = %d\n', n);
```
```matlab
% Skrypt 4 zad- obliczanie liczby przedziałów
liczba = 38068692544000000;
M = liczba^(1/6);     % pierwiastek 6. stopnia

v = 10:15:M;          % przedziały co 15 zaczynając od 10

n = floor((M - 10) / 15) + 1;
fprintf('n = %d\n', n);
```
## Wejściówka nr 2
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

## Wejściówka nr 3

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

# Wejściówka nr 4

```matlab
a = -2; b = -4; c = -5; d = 35;
n = [a, b, c];
y = 8;
z = -1;
x = (-(-4*y) - (-5*z) - 35) / (-2);

P1 = [0, 8, -1];             % punkt zaczepienia
P1 = [x, 8, -1];             % punkt zaczepienia
end_n = P1 + n;              % koniec wektora normalnego

fprintf('Zad1:\n');
fprintf('  n = [%d, %d, %d]\n', n);
fprintf('  koniec wektora w P1: [%.1f, %.1f, %.1f]\n\n', end_n);
Zad1:
  n = [-2, -4, -5]
  koniec wektora w P1: [2.0, 4.0, -6.0]

>> 
```

```matlab
%% Zadanie 2
% siatka punktów
[x, y] = meshgrid(-10:1:10, -10:1:10);
% obliczenie z z równania płaszczyzny
z = (-a*x - b*y - d)/c;

figure;
surf(x, y, z);
hold on;
axis equal
xlabel('x'); ylabel('y'); zlabel('z');
title('Płaszczyzna i wektor normalny');

% wybieramy inny punkt na płaszczyźnie, np.
P2 = [5, -3, (-a*5 - b*(-3) - d)/c];
% rysujemy wektor normalny w P2
quiver3(P2(1), P2(2), P2(3), n(1), n(2), n(3), 0.5, 'LineWidth',2);

hold off;
```

```matlab
%% Zadanie 3
v = [9, 0, 3];
P3 = [-6, 5, -3];

end_v = P3 + v;              % koniec wektora
mid_v = (P3 + end_v)/2;      % środek wektora
% gdyby koniec v był w Q=mid_v, to początek:
P_new = mid_v - v;

fprintf('\nZad3:\n');
fprintf('  koniec v przy P3: [%.1f, %.1f, %.1f]\n', end_v);
fprintf('  środek v:           [%.1f, %.1f, %.1f]\n', mid_v);
fprintf('  nowy początek v:    [%.1f, %.1f, %.1f]\n', P_new);
```

# Wejściówka nr 5
```matlab
%% Zadanie 1: 8-ścienna kostka
% P(2)=1/14, P(6)=1/4, pozostałe równo
p = zeros(1,8);
p(2) = 1/14;
p(6) = 1/4;
rem = 1 - (p(2)+p(6));
p([1,3,4,5,7,8]) = rem/6;

x = 1:8;
E4 = sum(x .* p);
fprintf('Zad4:\n');
for k = 1:8
    fprintf('  x=%d  p=%.3f\n', x(k), p(k));
end
fprintf('  E(X)=%.3f\n\n', E4);
```
```matlab
%% Zadanie 2: 6 rzutów kostką 1–9
% P(4) w 4. rzucie
P4 = 1/9;

% rozkład sumy S = X1+…+X6
d = ones(1,9)*(1/9);
for i = 2:6
    d = conv(d, ones(1,9)*(1/9));
end
s = 6:54;  % możliwe sumy

P_gt26 = sum(d(s>26));
P_even_or_gt26 = sum(d(mod(s,2)==0 | s>26));

fprintf('Zad5:\n');
fprintf('  P(4 w 4. rzucie)=%.3f\n', P4);
fprintf('  P(S>26)=%.3f\n', P_gt26);
fprintf('  P(S parzysta lub >26)=%.3f\n\n', P_even_or_gt26);
```
```matlab
%% Zadanie 3: zadany rozkład
x6 = [2.5, 5.5, 8, 10, 13.545];
p6 = [0.269, 0.266, 0.162, 0.02, 0.283];

E6 = sum(x6 .* p6);
Var6 = sum((x6.^2) .* p6) - E6^2;
SD6 = sqrt(Var6);

fprintf('Zad6:\n');
fprintf('  E(X)=%.4f\n', E6);
fprintf('  SD(X)=%.4f\n', SD6);
```
