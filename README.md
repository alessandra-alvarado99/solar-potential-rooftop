# Rooftop Solar Potential in Houston - Data-Driven Assessment

## Project Overview:
This project evaluates the potential for photovoltaic (PV) solar energy generation across rooftops in Houston, Texas.
Using **building footprint data** from the [Open Energy Data Initiative (OEDI) Data Lake] and the **PVGIS API** for solar irradiation, the workflow estimates:

- Rooftop usable area (m²)
- Installable solar capacity (kWp)
- Expectd annual energy generation (kWh)
- CO₂ emissions avoided (tons/year)
- Potential cost savings (USD/year)

## Methodology
1. **Data acquisition**  
   - Rooftop footprints from OEDI PV Rooftop dataset (Houston, 2010).  
   - Coordinates and geometry processed with **GeoPandas**.  

2. **Geospatial processing**  
   - Projection to Texas Albers Equal Area for surface calculations.  
   - Centroid extraction for each rooftop polygon (lat/lon).  

3. **Solar irradiation**  
   - Annual yield (E<sub>y</sub>) retrieved via **PVGIS API** for cluster centroids to minimize API calls.  

4. **PV potential estimation**  
   - Installed capacity = usable area / 7 m² per kWp.  
   - Annual energy = installed capacity × E<sub>y</sub>.  
   - CO₂ savings = annual energy × 0.0004 tons/kWh.  
   - Cost savings = annual energy × $0.15/kWh.
  
## Results (Houston Sample)
- **Average rooftop capacity:** ~39 kWp  
- **Average annual generation:** ~52,000 kWh  
- **CO₂ savings per rooftop:** ~20.9 tons/year  
- **Potential cost savings per rooftop:** ~$7,800/year  

---

## Tech Stack
- Python (pandas, geopandas, shapely, sklearn, requests)  
- AWS S3 (OEDI Data Lake access)  
- PVGIS API (solar irradiation)  

---

## Business Impact
This framework allows city planners, utility companies, and sustainability teams to:
- Quantify the **solar potential** at scale.  
- Estimate **environmental benefits** (CO₂ reduction).  
- Evaluate **economic returns** for solar adoption.  


