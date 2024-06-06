# Projekt na przedmiot podstawy sztucznej inteligencji

## Cel projektu
Celem jest utworzenie modelu sieci konwolucyjnej mogącej klasyfikować gatunek zwierzęcia obecnego na zdjęciu do jednej z następującej klas:
    - kot
    - pies
    - słoń
    - koń
    - lew

Model zostanie wytrenowany z pomocą pakietów scikit-learn oraz tensorflow (keras).

Zbiór danych który został wykorzystany w tym projekcie można znaleźć pod adresem https://www.kaggle.com/datasets/antobenedetti/animals. Zawiera on pięć klas wymienionych powyżej.
Etykiety klas i przykładowe elementy znajdują się w katalogu inf. 
Dane treningowe znajdują się w katalogu train i są podzielone na odrębne katalogi (np zdjęcia psów w katalogu dog). 
Dane walidacyjne zostały umieszczone w katalogu val.

Zbiór danych został podzielony na dane treningowe i testowe w proporcji 80/20.

Do zbioru danych treningowych zostały dodane dane augmentacyjne wygenerowane z tego właśnie zbioru w celu zwiększenia zbioru danych i poprawienia dokładności modelu. Obrazy są podawane jako np.array o wymiarach (rozmiar obrazu, rozmiar obrazu, kanały rgb pikseli). Wartości kanałów zostały znormalizowane z 1 bytea do wartości float w zakresie [0, 1].

## Opis modelu

Model, który został zastosowany to konwolucyjna sieć neuronowa stworzona przy pomocy pakietu keras. Model składa się z następujących warst:
-warstwa konwolucyjna składająca się z 32 neuronów z filtrem 3x3, aktywacją ELU oraz neutralnym paddingiem.
-warstwa normalizacyjna.
-warstwa maxpoolingu z redukcją x2.
-warstwa dropout z parametrem 0.25.
-warstwa konwolucyjna składająca się z 64 neuronów z filtrem 3x3, aktywacją ELU oraz neutralnym paddingiem.
-warstwa normalizacyjna.
-warstwa maxpoolingu z redukcją x2.
-warstwa dropout z parametrem 0.25.
-warstwa konwolucyjna składająca się z 64 neuronów z filtrem 3x3, aktywacją ELU oraz neutralnym paddingiem.
-warstwa normalizacyjna.
-warstwa maxpoolingu z redukcją x2.
-warstwa dropout z parametrem 0.25.
-warstwa wypłaszczająca
-warstwa fully-connected o rozmiarze 128 neuronów i aktywacją relu.
-warstwa normalizacyjna.
-warstwa dropout z parametrem 0.25.
-warstwa fully-connected o rozmiarze 5 neuronów i aktywacją softmax.

Do problemu została zastosowana sieć konwolucyjna ponieważ ze względu na jej architekturę, która uwzględnia odległość parametrów na płaszczyźnie i posiada strukturę drzewiastą, co umożliwia ekstrację cech danych na różnych poziomach uogólnienia co idealnie się nadaje do rozpoznawania obiektów na zdjęciach i jest jedną z wiodących architektur w tej dziedzinie.

Do trenowania wykorzystano optymizator adam i entropię krzyżową jako funkcję straty.

## Instrukcje uruchomienia i dodatkowe informacje

Zarówno kod projektu jak i raport zostały umieszczone w pliku projekt.ipynb. Jako że projekt był liczony na domowym komputerze z niską mocą obliczeniową, cały kod został umieszczony w pliku jupyter notebook i może być uruchomiony na komputerze o przeciętnej mocy obliczeniowej. Aczkolwiek niektóre konfiguracje mogą wymagać nawet 30GB pamięci podręcznej.
Aby uruchomić projekt należy mieć zainstalowany serwer jupyter notebook i jakiegoś klienta (lub przeglądarkę) oraz jądro ipykernel i środowisko python3 z bibliotekami z pliku requrements.txt.