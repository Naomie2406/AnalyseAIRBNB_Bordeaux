# 🏠 Airbnb Bordeaux — Data Analytics Dashboard (Qlik Sense)

![Qlik Sense](https://img.shields.io/badge/Qlik%20Sense-009845?style=for-the-badge&logo=qlik&logoColor=white)
![Dashboard](https://img.shields.io/badge/Dashboard-2%20views-red?style=for-the-badge)
![Listings](https://img.shields.io/badge/Listings-10%20390-blue?style=for-the-badge)
![Reviews](https://img.shields.io/badge/Reviews-180%20209-orange?style=for-the-badge)

---

## 📋 Project Overview

This project is a **data visualization and analysis** of Airbnb listings in the **Bordeaux metropolitan area**, built with **Qlik Sense**. The goal was to explore the Airbnb market structure, pricing patterns, geographic distribution, and host behavior using real open data.

---

## 📁 Datasets Used

| File | Description | Rows |
|---|---|---|
| `listings.csv` | All Airbnb listings with price, type, location, availability | 10 438 |
| `reviews.csv` | Guest reviews with listing ID and date | 180 209 |
| `neighbourhoods.csv` | Neighbourhood and commune mapping | — |
| `population.xlsx` | Population data by commune | — |

---

## 🛠️ Data Preparation (Qlik Script)

The data was loaded and transformed using a **Qlik Load Script** structured in 3 tabs:

**Tab listing_clean**
- Loaded from `listing_clean.xlsx`
- Created a composite join key: `listing_id & '_' & unique_listing_id_reviews as key_review`
- Created a neighbourhood join key: `neighbourhood_id & '_' & neighbourhood_group_id as key_neighbourhood`
- Generated a geographic point for map visualization: `GeoMakePoint(latitude, longitude) as Location`
- Created a conditional field `listing_name_cart` to exclude zero-revenue listings from the map

**Tab neighbourhoods_clean**
- Built the composite neighbourhood key for joining with listings

**Tab reviews_clean**
- Decomposed dates into `day_reviews`, `month_reviews`, `year_reviews` for time-based filtering

---

## 📊 Key Metrics (KPIs)

| Metric | Value |
|---|---|
| 🏠 Total listings | **10 390** |
| 💶 Average price/night | **85,18 €** |
| ⭐ Average reviews/month | **1,46** |
| 📅 Average availability/year | **113 days** |
| 📈 Occupancy rate | **31,07%** |
| 💰 Average revenue/year | **12 011,24 €** |

---

## 📈 Results & Analysis

### 1. Listing Type Distribution

| Room Type | Count | Share | Avg Price/night |
|---|---|---|---|
| Entire home/apt | 7 895 | **76%** | 96,79 € |
| Private room | 2 420 | 23% | 48,99 € |
| Shared room | 75 | 1% | 33,68 € |

> The vast majority of Airbnb listings in Bordeaux are entire homes/apartments, suggesting a strong short-term rental market that may compete directly with long-term residential housing.

### 2. Top Neighbourhoods by Listings

| Neighbourhood | Listings |
|---|---|
| Centre ville (Bordeaux) | 2 106 |
| Bordeaux Sud | 1 541 |
| Chartrons - Grand Parc | 1 019 |
| Saint Augustin | 616 |
| Bordeaux Maritime | 580 |
| Nansouty - Saint Gens | 553 |

> The city centre alone concentrates over 20% of total supply, consistent with high tourist demand in that area.

### 3. Pricing Analysis

- **Median price/night: 57 €** vs mean of 85 € — a right-skewed distribution driven by luxury outliers (max: 50 000 €)
- **Q1:** 40 € | **Q3:** 90 €
- Most expensive communes: Mérignac (193 €/night avg), Saint-Aubin-de-Médoc (166 €), Bouliac (155 €)
- The boxplot analysis confirms high price dispersion, especially for entire home/apt listings

### 4. Occupancy & Revenue

- Listings are available on average only **113 days/year**, meaning they are occupied or blocked roughly **69% of the time**
- Estimated average annual revenue per listing: **~12 000 €**
- Listings with zero revenue were excluded from the geographic map to avoid visual distortion

### 5. Review Trends (2010–2018)

| Year | Reviews |
|---|---|
| 2014 | 4 098 |
| 2015 | 14 122 |
| 2016 | 35 033 |
| 2017 | 61 085 |
| 2018 | 64 661 |

> The Airbnb market in Bordeaux grew **exponentially** between 2014 and 2018, with reviews nearly doubling each year. This reflects both Airbnb's global growth and Bordeaux's rising tourist appeal (UNESCO World Heritage status, LGV high-speed rail opening in 2017).

### 6. Host Behavior

- **8 798 unique hosts** for 10 390 listings
- **869 hosts** manage more than one listing — signs of professional short-term rental activity
- 87% of hosts manage a single listing, indicating a mixed market of occasional and professional renters

---

## 💡 Key Takeaways

1. **Entire homes dominate (76%)** — raising questions about housing availability for long-term residents
2. **Strong geographic concentration** in the city centre, while some suburban communes show higher average prices
3. **Explosive growth from 2014 to 2018**, likely accelerated by Bordeaux's UNESCO listing and the LGV rail connection
4. **High price dispersion** — the gap between median (57 €) and mean (85 €) signals a small number of premium listings skewing averages upward
5. **Occupancy rate of ~31%** suggests moderate average demand, though central listings likely significantly outperform this average

---

## 🗺️ Dashboards

### Dashboard 1 — Market Overview
![Dashboard 1](DASHBOARD_AIRBNB.PNG)

- KPI bar (total listings, avg price, reviews, availability, occupancy, revenue)
- Bar chart: listing distribution by room type
- Bar chart: listing distribution by neighbourhood
- Line chart: average price/night by neighbourhood
- Boxplot: price distribution by room type and by neighbourhood
- Filter panel: Quartier, Commune, year/month of reviews

### Dashboard 2 — Geographic Map
![Dashboard 2](DASHBOARD_AIRBNB_2.PNG)

- Same KPI bar
- Interactive map of all Airbnb listings (OpenStreetMap)
- Points colored by revenue category
- Filter panel: Quartier, Commune, year/month, host name, room type, listing name

---

## 🔧 Tools & Technologies

- **Qlik Sense** — data modeling, scripting, and dashboard creation
- **Excel** — data cleaning and preparation
- **OpenStreetMap** — base map for geographic visualization

---

<!-- VERSION FRANÇAISE

# 🏠 Airbnb Bordeaux — Dashboard Data Analytics (Qlik Sense)

## 📋 Présentation du projet

Ce projet est une analyse et visualisation de données des logements Airbnb dans la métropole bordelaise, réalisée avec Qlik Sense. L'objectif était d'explorer la structure du marché Airbnb, les tendances tarifaires, la distribution géographique et le comportement des hôtes à partir de données ouvertes réelles.

## 📁 Jeux de données utilisés

| Fichier | Description | Lignes |
|---|---|---|
| listings.csv | Tous les logements Airbnb avec prix, type, localisation, disponibilité | 10 438 |
| reviews.csv | Avis des voyageurs avec ID logement et date | 180 209 |
| neighbourhoods.csv | Correspondance quartiers / communes | — |
| population.xlsx | Données de population par commune | — |

## 🛠️ Préparation des données (Script Qlik)

Les données ont été chargées et transformées via un script de chargement Qlik structuré en 3 onglets :

Onglet listing_clean :
- Chargement depuis listing_clean.xlsx
- Création d'une clé composite : listing_id & '_' & unique_listing_id_reviews as key_review
- Génération d'un point géographique : GeoMakePoint(latitude, longitude) as Location
- Champ conditionnel listing_name_cart pour exclure les logements sans revenu de la carte

Onglet neighbourhoods_clean :
- Construction de la clé composite pour la jointure avec les logements

Onglet reviews_clean :
- Décomposition des dates en day_reviews, month_reviews, year_reviews pour le filtrage temporel

## 📊 Indicateurs clés (KPIs)

| Indicateur | Valeur |
|---|---|
| Nombre total de logements | 10 390 |
| Prix moyen/nuit | 85,18 € |
| Moy. avis/mois | 1,46 |
| Moy. disponibilité/an | 113 jours |
| Taux d'occupation | 31,07% |
| CA moyen/an | 12 011,24 € |

## 📈 Résultats & Analyse

1. Répartition par type de logement
   - Entire home/apt : 7 895 (76%) — 96,79 €/nuit en moyenne
   - Private room : 2 420 (23%) — 48,99 €/nuit
   - Shared room : 75 (1%) — 33,68 €/nuit
   Le marché est dominé par les logements entiers, ce qui peut impacter l'offre de logements pour les résidents permanents.

2. Top quartiers
   Le Centre-ville concentre plus de 20% de l'offre (2 106 logements), suivi de Bordeaux Sud (1 541) et des Chartrons (1 019).

3. Analyse des prix
   - Médiane : 57 €/nuit vs moyenne 85 € — distribution asymétrique avec des valeurs extrêmes (max : 50 000 €)
   - Communes les plus chères : Mérignac (193 €), Saint-Aubin-de-Médoc (166 €), Bouliac (155 €)
   - Les boxplots confirment une forte dispersion des prix

4. Tendance des avis (2014–2018)
   Croissance exponentielle : de 4 098 avis en 2014 à 64 661 en 2018.
   Bordeaux bénéficie de son classement UNESCO et de l'ouverture de la LGV en 2017.

5. Comportement des hôtes
   - 8 798 hôtes uniques pour 10 390 logements
   - 869 hôtes gèrent plusieurs logements (activité professionnelle)
   - 87% des hôtes ne gèrent qu'un seul logement

## 💡 Conclusions principales
1. Les logements entiers dominent (76%) — impact potentiel sur le marché locatif résidentiel
2. Forte concentration géographique au centre-ville
3. Croissance explosive du marché entre 2014 et 2018
4. Forte dispersion des prix : médiane 57 € vs moyenne 85 €
5. Taux d'occupation moyen de 31%, mais les logements centraux surperforment probablement

-->
