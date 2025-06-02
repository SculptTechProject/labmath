## Drei

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

# Vier

soon XD
