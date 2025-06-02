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

Układ równań (wiele odpowiedzi)

````matlab
A = [1 1 -14; 0 1 -5; -1 2 -1];
B = [7; 8; 17];

% Tutaj podajesz odpowiedzi po przecinku (podmieniasz wartości)
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

for i = 1:size(odp, 1)
    x = odp(i, :)';
    if norm(A * x - B) < 1e-6
        fprintf("Odpowiedzi z (%d, %d, %d) są rozwiązaniem\n", x(1), x(2), x(3));
    end
end
````

Układ równań (wskazać iloczyn wartości z rozwiązania układu)

```matlab
% A wpisujemy dane x y z, jeżeli nie ma jednych z xyz to wpisujemy 0 w miejsce, a jeżeli sam np. x to 1.
% B wpisujemy dane po prawej stronie od góry
A = [-3 3 -3; 10 33 -3; 37 0 30];
B = [6; 22; 4];
x = A \ B; % PAMIETAJ MUSI BYC \   !!!!!!!!!

fprintf('x = %d, y = %d, z = %.2f\n', x(1), x(2), x(3));
iloczyn = x(1) * x(2) * x(3);
fprintf('Iloczyn liczb(Wynik): x * y * z = %.2f\n', iloczyn);
```

Zadanie o macierzy schodkowej pewnego układu równań x y z t u v

Na kartce mozna zrobic, przepisac uklad i podpisac u góry sześć pierwszych kolumn tymi literami a na końcu to są wyniki które się równają.

np jeśli x = 1 i z = 1, i to się równa 21 to jest x + z = 21, czyli wtedy x = 21 - z jak i z = 21 -x. Następnie tak dla wszystkich robisz (wierszy), a potem przelatujesz po pytaniach.
