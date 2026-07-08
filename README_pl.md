# Analiza i Prognozowanie Dynamiki Stopy Bezrobocia w Belgii 🇧🇪📉

[English version](README.md)

## 📌 Cel projektu
Głównym celem projektu jest badanie i prognozowanie zmiennych makroekonomicznych kształtujących dynamikę stopy bezrobocia w Belgii[cite: 12]. 

## 📊 Opis danych i zmiennych
Analiza opiera się na 84 obserwacjach kwartalnych obejmujących okres od Q1 2005 do Q4 2025. 
* **Zmienna objaśniana:** `unemp` – stopa bezrobocia.
* **Zmienne objaśniające:** `production` (produkcja w przemyśle), `gdp` (Produkt Krajowy Brutto), `wcost` (jednostkowe koszty pracy) oraz `shock_2020_2022` (zmienna zerojedynkowa dla pandemii Covid-19 i wojny w Ukrainie).

## 🛠️ Metodologia
* Z powodu niestacjonarności danych (potwierdzonej rozszerzonym testem Dickeya-Fullera) oraz braku kointegracji, zastosowano transformacje w postaci logarytmowania i pierwszych różnic.
* Zbudowano model opóźnień rozłożonych (ADL), który doskonale opisuje rozłożone w czasie procesy dostosowawcze rynku pracy.

## 💡 Główne wnioski z analizy
* **Wpływ PKB i Produkcji:** Zgodnie z Prawem Okuna, wzrost tempa PKB oraz produkcji przemysłowej z opóźnieniem 1-3 kwartałów stymuluje popyt na pracę i prowadzi do istotnego spadku dynamiki bezrobocia.
* **Koszty pracy:** Wzrost jednostkowych kosztów pracy (`wcost`) w modelu sygnlizuje rozgrzanie gospodarki i tzw. "rynek pracownika", co przekłada się na redukcję tempa bezrobocia dwa kwartały później.
* **Elastyczność rynku pracy:** Bieżące bezrobocie silnie zależy od swoich przeszłych wartości – wyższe tempo zmian bezrobocia w poprzednim kwartale skutkuje jego obniżeniem w bieżącym, co świadczy o elastyczności rynku.
* **Ciekawostki makroekonomiczne:** 
  * Szok z lat 2008-2009 nie wywołał wzrostu bezrobocia (kryzys zażegnano poprzez skracanie czasu pracy zamiast zwolnień). 
  * Inflacja okazała się zmienną całkowicie nieistotną w modelu, co sugeruje, że współczesne cele inflacyjne państw europejskich osłabiły tradycyjną zależność zwaną Krzywą Phillipsa.

## 📈 Diagnostyka i Prognozowanie
* **Statystyki dopasowania:** Model tłumaczy 59.8% (Skorygowane R-kwadrat) zmienności dynamiki bezrobocia, co jest bardzo satysfakcjonującym wynikiem dla szeregów czasowych na pierwszych różnicach.
* **Testy formalne:** Model pomyślnie przeszedł weryfikację statystyczną (brak autokorelacji wg statystyki Durbina-Watsona i testu LM, homoskedastyczność wg testu White'a, prawidłowa specyfikacja w teście RESET, brak współliniowości w teście VIF oraz normalny rozkład reszt).
* **Jakość prognozy:** Bardzo wysoka jakość prognozy ex-post – średni błąd wynosi zaledwie 0.1%, a błąd prognozy aż w 98% wynika z niemożliwego do przewidzenia szumu losowego (wskaźnik UD). W scenariuszu bazowym prognoza ex-ante wykazuje pożądane właściwości wyciszania (powrót do średniej).
