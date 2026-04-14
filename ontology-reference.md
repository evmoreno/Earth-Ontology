# Earth Ontology — DTDL Reference

**Version:** 1.0  
**DTDL Version:** 3  
**DTMI Namespace:** `dtmi:earthontology`  
**Repository:** [evmoreno/Earth-Ontology](https://github.com/evmoreno/Earth-Ontology)

---

## Overview

The Earth Ontology models Earth's major systems as a set of Azure Digital Twins Definition Language (DTDL) interfaces. It is designed for use with [Azure Digital Twins](https://azure.microsoft.com/en-au/products/digital-twins) to create a live, queryable digital representation of Earth's spheres and their interactions.

The ontology spans from the cosmic scale (Universe, Geospace) down to individual ecosystems (Forest, Glacier, Desert), with telemetry hooks for live sensor or IoT data at every level.

---

## Model hierarchy

```
Universe
└── Geospace
    └── Earth
        ├── Atmosphere
        │   ├── Troposphere
        │   ├── Stratosphere
        │   ├── Mesosphere
        │   ├── Thermosphere
        │   └── Exosphere  ──transitionsInto──► Geospace
        ├── Lithosphere
        │   ├── Crust
        │   ├── Mantle
        │   └── Core
        ├── Hydrosphere
        │   ├── Ocean
        │   ├── Lake
        │   ├── River
        │   └── Glacier
        └── Biosphere ──interactsWith──► Atmosphere, Hydrosphere, Lithosphere
            ├── Forest
            ├── Grassland
            ├── Desert
            └── Mountain ──isLocatedIn──► Lithosphere
```

The hierarchy has three tiers:

- **Cosmic tier** — Universe and Geospace provide the spatial context in which Earth exists.
- **Sphere tier** — Earth's four major systems (Atmosphere, Lithosphere, Hydrosphere, Biosphere), each linked to Earth via a named relationship on the Earth interface.
- **Subclass tier** — Specific zones and ecosystem types that `extend` their parent sphere interface, inheriting all parent properties and relationships.

---

## Files

| File | Interfaces defined |
|------|--------------------|
| `Universe.json` | Universe |
| `Geospace.json` | Geospace |
| `Earth.json` | Earth |
| `Atmosphere.json` | Atmosphere, Troposphere, Stratosphere, Mesosphere, Thermosphere, Exosphere |
| `Lithosphere.json` | Lithosphere, Crust, Mantle, Core |
| `Hydrosphere.json` | Hydrosphere, Ocean, Lake, River, Glacier |
| `Biosphere.json` | Biosphere, Forest, Grassland, Desert, Mountain |

Each multi-interface file is a valid DTDL **array** — you upload the whole file to ADT in a single batch operation.

---

## Interface reference

### Universe

**DTMI:** `dtmi:earthontology:Universe;1`  
**File:** `Universe.json`

The broadest context in the ontology. Represents the totality of space, time, matter, and energy. Acts as the root container from which Geospace (and through it, Earth) can be reached.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `estimatedAgeBillionYears` | Property | double | Approximate age of the Universe in billions of years |
| `observableRadiusLightYears` | Property | double | Approximate radius of the observable universe |
| `contains` | Relationship → Geospace | — | The Universe contains Geospace |

---

### Geospace

**DTMI:** `dtmi:earthontology:Geospace;1`  
**File:** `Geospace.json`

The region of outer space near Earth, including the magnetosphere and radiation belts. Sits between the Exosphere and interplanetary space, and provides the link between Earth's atmosphere and the broader Universe.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `magnetosphereExtentKm` | Property | double | Extent of Earth's magnetosphere on the sunward side |
| `hasVanAllenBelts` | Property | boolean | Presence of Van Allen radiation belts |
| `isPartOf` | Relationship → Universe | — | Geospace is part of the Universe |
| `encompasses` | Relationship → Earth | — | Geospace encompasses Earth |

---

### Earth

**DTMI:** `dtmi:earthontology:Earth;1`  
**File:** `Earth.json`

The root planet interface. Holds the four sphere relationships and key physical properties. All sphere-level interfaces trace back to Earth via their `isPartOf` relationship.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `radiusKm` | Property | double | Mean radius of Earth |
| `massKg` | Property | double | Mass of Earth |
| `surfaceTemperatureCelsius` | Property | double | Current mean global surface temperature |
| `globalMeanTemperature` | Telemetry | double | Live global mean surface temperature feed |
| `hasAtmosphere` | Relationship → Atmosphere | — | Earth has an atmosphere |
| `hasLithosphere` | Relationship → Lithosphere | — | Earth has a lithosphere |
| `hasHydrosphere` | Relationship → Hydrosphere | — | Earth has a hydrosphere |
| `hasBiosphere` | Relationship → Biosphere | — | Earth has a biosphere |
| `isLocatedIn` | Relationship → Geospace | — | Earth is located within Geospace |

---

### Atmosphere

**DTMI:** `dtmi:earthontology:Atmosphere;1`  
**File:** `Atmosphere.json`  
**Subclasses:** Troposphere, Stratosphere, Mesosphere, Thermosphere, Exosphere

The layer of gases surrounding Earth. Parent interface for all five atmospheric layers, each of which uses `extends` to inherit these base properties.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `totalMassKg` | Property | double | Total mass of Earth's atmosphere |
| `co2ConcentrationPpm` | Property | double | Current CO₂ concentration in parts per million |
| `co2Reading` | Telemetry | double | Live CO₂ concentration feed |
| `isPartOf` | Relationship → Earth | — | Atmosphere is part of Earth |
| `interactsWith` | Relationship → Biosphere | — | Gas exchange and climate interaction |

#### Subclass properties

| Interface | Key additions |
|-----------|---------------|
| **Troposphere** | `altitudeRangeKm` (0–12 km), `avgTemperatureCelsius`, Telemetry: `weatherEvent` |
| **Stratosphere** | `altitudeRangeKm` (12–50 km), `ozoneDobsonUnits` (ozone layer thickness) |
| **Mesosphere** | `altitudeRangeKm` (50–80 km), `minTemperatureCelsius` (~−90°C) |
| **Thermosphere** | `altitudeRangeKm` (80–600 km), Telemetry: `auroraActivity` |
| **Exosphere** | `altitudeRangeKm` (600–10,000 km), Relationship: `transitionsInto` → Geospace |

The `transitionsInto` relationship on **Exosphere** is the closure of the cosmic hierarchy — it links the outermost atmospheric layer back to Geospace, completing the loop from Universe → Geospace → Earth → Atmosphere → Exosphere → Geospace.

---

### Lithosphere

**DTMI:** `dtmi:earthontology:Lithosphere;1`  
**File:** `Lithosphere.json`  
**Subclasses:** Crust, Mantle, Core

The rigid outer mechanical layer of Earth, comprising the crust and uppermost mantle. Broken into tectonic plates.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `averageThicknessKm` | Property | double | Average thickness (100–200 km) |
| `numberOfTectonicPlates` | Property | integer | Number of major tectonic plates |
| `seismicActivity` | Telemetry | string | Current global seismic activity level |
| `isPartOf` | Relationship → Earth | — | Lithosphere is part of Earth |
| `interactsWith` | Relationship → Biosphere | — | Soil formation, mineral cycles, tectonics |

#### Subclass properties

| Interface | Key additions |
|-----------|--------------|
| **Crust** | `crustType` enum (oceanic/continental), `averageThicknessKm` |
| **Mantle** | `depthRangeKm` (35–2900 km), `avgTemperatureCelsius`, `convectionActive` boolean |
| **Core** | `coreType` enum (inner/outer), `depthRangeKm`, `avgTemperatureCelsius`, `generatesMagneticField` boolean |

The `generatesMagneticField` property on **Core** connects the innermost layer of the Lithosphere to Geospace's `hasVanAllenBelts` property — the magnetic field generated by the liquid outer core creates the magnetosphere that defines Geospace.

---

### Hydrosphere

**DTMI:** `dtmi:earthontology:Hydrosphere;1`  
**File:** `Hydrosphere.json`  
**Subclasses:** Ocean, Lake, River, Glacier

All water on, under, and above Earth's surface. The only sphere with real-time sea level telemetry at the parent interface level.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `totalVolumeKm3` | Property | double | Total volume of the hydrosphere |
| `saltWaterPercentage` | Property | double | ~97.5% |
| `freshWaterPercentage` | Property | double | ~2.5% |
| `globalSeaLevelMm` | Telemetry | double | Live global mean sea level |
| `isPartOf` | Relationship → Earth | — | Hydrosphere is part of Earth |
| `interactsWith` | Relationship → Biosphere | — | Water cycle, aquatic habitats |

#### Subclass properties

| Interface | Key additions |
|-----------|--------------|
| **Ocean** | `name`, `areaMillion_km2`, `averageDepthM`, Telemetry: `surfaceTemperatureCelsius` |
| **Lake** | `name`, `area_km2`, `isFreshwater` boolean |
| **River** | `name`, `lengthKm`, Telemetry: `flowRateM3s` |
| **Glacier** | `name`, `area_km2`, Telemetry: `massBalanceMmWaterEquiv`, `retreatRateMperYear` |

Glacier telemetry is particularly significant from a climate monitoring perspective — `massBalanceMmWaterEquiv` (negative = net ice loss) and `retreatRateMperYear` together give a direct signal of cryosphere change over time.

---

### Biosphere

**DTMI:** `dtmi:earthontology:Biosphere;1`  
**File:** `Biosphere.json`  
**Subclasses:** Forest, Grassland, Desert, Mountain

All living organisms on Earth and their interactions with the other three spheres. The Biosphere is the most connected interface — it has `interactsWith` relationships declared on Atmosphere, Hydrosphere, and Lithosphere, and receives reciprocal `interactsWith` from each.

| Name | Type | Schema | Description |
|------|------|--------|-------------|
| `estimatedSpeciesCount` | Property | integer | Estimated total species on Earth |
| `totalBiomassPgC` | Property | double | Total biomass in petagrams of carbon |
| `globalNPP_PgCperYear` | Telemetry | double | Annual global net primary productivity |
| `isPartOf` | Relationship → Earth | — | Biosphere is part of Earth |
| `interactsWith` | Relationship → Atmosphere | — | Gas exchange, photosynthesis, respiration |

#### Subclass properties

| Interface | Key additions |
|-----------|--------------|
| **Forest** | `name`, `forestType` enum (tropical/temperate/boreal/mangrove), `area_km2`, Telemetry: `canopyCoverPercentage`, `carbonStockPgC` |
| **Grassland** | `name`, `grasslandType` enum (savanna/prairie/steppe/pampas), `area_km2`, Telemetry: `soilCarbonPgC` |
| **Desert** | `name`, `desertType` enum (hot/cold/coastal/polar), `area_km2`, Telemetry: `annualPrecipitationMm` |
| **Mountain** | `name`, `elevationM`, `rangeOrMassif`, Relationship: `isLocatedIn` → Lithosphere |

**Mountain** is the only Biosphere subclass with a cross-sphere relationship — `isLocatedIn` → Lithosphere — reflecting that mountains are as much a geological feature as a biological one.

---

## Relationships summary

| Relationship | From | To | Direction | Notes |
|---|---|---|---|---|
| `contains` | Universe | Geospace | → | Cosmic containment |
| `isPartOf` | Geospace | Universe | → | Inverse of `contains` |
| `encompasses` | Geospace | Earth | → | Spatial containment |
| `isLocatedIn` | Earth | Geospace | → | Earth sits within Geospace |
| `hasAtmosphere` | Earth | Atmosphere | → | Sphere ownership |
| `hasLithosphere` | Earth | Lithosphere | → | Sphere ownership |
| `hasHydrosphere` | Earth | Hydrosphere | → | Sphere ownership |
| `hasBiosphere` | Earth | Biosphere | → | Sphere ownership |
| `isPartOf` | Atmosphere | Earth | → | Sphere-to-Earth |
| `isPartOf` | Lithosphere | Earth | → | Sphere-to-Earth |
| `isPartOf` | Hydrosphere | Earth | → | Sphere-to-Earth |
| `isPartOf` | Biosphere | Earth | → | Sphere-to-Earth |
| `interactsWith` | Atmosphere | Biosphere | → | Gas exchange, climate |
| `interactsWith` | Lithosphere | Biosphere | → | Soil, minerals, tectonics |
| `interactsWith` | Hydrosphere | Biosphere | → | Water cycle, habitats |
| `interactsWith` | Biosphere | Atmosphere | → | Declared on Biosphere interface |
| `transitionsInto` | Exosphere | Geospace | → | Atmospheric boundary |
| `isLocatedIn` | Mountain | Lithosphere | → | Cross-sphere subclass link |

---

## Design decisions

### Why `extends` instead of `isPartOf` for subclasses

DTDL `extends` models *interface inheritance* — a Troposphere is a type of Atmosphere and inherits all its properties and relationships. This is more precise than `isPartOf` (which implies spatial or compositional containment) and is the DTDL-idiomatic way to express a subclass relationship.

`isPartOf` is reserved for sphere-to-Earth and sphere-to-sphere spatial containment (e.g. Atmosphere `isPartOf` Earth).

### Why `interactsWith` is one-directional

DTDL does not have a native inverse relationship mechanism. Declaring `interactsWith` on both the Biosphere and each sphere separately would create maintenance overhead and potential inconsistency. The chosen pattern declares `interactsWith` going *outward from each sphere toward Biosphere*, and once on the Biosphere interface pointing back to Atmosphere. This is sufficient to create the graph edges in ADT Explorer and support `JOIN` queries across spheres.

### Property vs Telemetry

| Use `Property` when... | Use `Telemetry` when... |
|------------------------|-------------------------|
| The value is stable or changes rarely (radius, depth range, species count) | The value streams continuously from a sensor or data feed (sea surface temperature, CO₂ ppm, glacier retreat rate) |
| You want to query or filter twins by this value | You want to route to Time Series Insights or Event Hubs |
| The value is set at model instantiation | The value arrives via IoT Hub or Event Grid |

### Enum schemas for categorical properties

Categorical properties (forest type, desert type, crust type, core type) use DTDL `Enum` schemas rather than free-text strings. This enforces valid values at the ADT service layer and enables precise querying: `SELECT * FROM DIGITALTWINS WHERE IS_OF_MODEL('dtmi:earthontology:Forest;1') AND forestType = 'tropical'`.

---

## Upload to Azure Digital Twins

### Prerequisites

- An Azure Digital Twins instance
- [ADT Explorer](https://explorer.digitaltwins.azure.net/) or the [ADT Tools CLI](https://github.com/Azure/opendigitaltwins-tools/tree/main/ADTTools)

### Upload order

Interfaces must be uploaded before any interface that targets them in a `Relationship`. The correct order is:

```
1. Universe.json
2. Geospace.json
3. Earth.json
4. Atmosphere.json
5. Lithosphere.json
6. Hydrosphere.json
7. Biosphere.json
```

### Using ADT Explorer (no-code)

1. Open [ADT Explorer](https://explorer.digitaltwins.azure.net/) and connect to your instance.
2. Select **Models** → **Upload a model**.
3. Upload files in the order listed above.
4. Each array file (e.g. `Atmosphere.json`) will import all interfaces in that file in a single operation.

### Using ADT Tools CLI

```bash
UploadModels \
  -t <tenantId> \
  -c <clientId> \
  -h <yourInstance>.api.wcus.digitaltwins.azure.net \
  Universe.json Geospace.json Earth.json \
  Atmosphere.json Lithosphere.json Hydrosphere.json Biosphere.json
```

### Validation before upload

Use the DTDL Validator to catch errors before uploading:

```bash
DTDLValidator --folder ./DTDL
```

---

## Querying the ontology in ADT

Once models are uploaded and twins are instantiated, example ADT queries:

```sql
-- Find all twins that are a type of Atmosphere subclass
SELECT * FROM DIGITALTWINS WHERE IS_OF_MODEL('dtmi:earthontology:Atmosphere;1', exact)

-- Find all Forest twins with tropical type
SELECT * FROM DIGITALTWINS
WHERE IS_OF_MODEL('dtmi:earthontology:Forest;1')
AND forestType = 'tropical'

-- Traverse from Earth to all related sphere twins
SELECT T, CT FROM DIGITALTWINS T
JOIN CT RELATED T.hasAtmosphere
WHERE T.$dtId = 'earth-01'

-- Find all twins with active glacier retreat (negative mass balance)
SELECT * FROM DIGITALTWINS
WHERE IS_OF_MODEL('dtmi:earthontology:Glacier;1')
AND massBalanceMmWaterEquiv < 0
```

---

## Extending the ontology

### Adding new subclasses

To add a new ecosystem type (e.g. `Wetland` under `Biosphere`):

1. Create a new interface with `"extends": "dtmi:earthontology:Biosphere;1"`
2. Assign a DTMI following the existing pattern: `dtmi:earthontology:Wetland;1`
3. Add it to `Biosphere.json` (or a new file) as another array element
4. Upload the new interface — existing twins are unaffected

### Adding new sphere-level interactions

To model an interaction between Hydrosphere and Lithosphere (e.g. groundwater and soil):

1. Add a `Relationship` to one of the interfaces (e.g. `"interactsWith"` on `Hydrosphere` targeting `Lithosphere`)
2. Upload the updated model as version `2`: `dtmi:earthontology:Hydrosphere;2`
3. Note: ADT does not allow in-place model updates — you must upload a new version and migrate twins if needed

### Connecting to real data

- **IoT Hub → ADT**: Route IoT Hub device telemetry to ADT using Azure Functions and the ADT SDK
- **Azure Maps**: Geo-locate Ocean, River, and Mountain twins using Azure Maps integration
- **Time Series Insights**: Route Telemetry fields (glacier retreat, sea surface temperature, CO₂) to Azure Time Series Insights for historical analysis

---

## Earth Systems Simulator

The ontology has an accompanying interactive simulator — `earth-systems-simulator.html` — available in the `/DOCS` folder. Open it in any browser with no internet connection or dependencies required.

The simulator exposes the eight key writable/telemetry parameters from the DTDL model as drag sliders:

| Simulator parameter | Maps to DTDL field | Interface |
|---|---|---|
| CO₂ concentration (ppm) | `co2ConcentrationPpm` | Atmosphere |
| Ozone layer (Dobson Units) | `ozoneDobsonUnits` | Stratosphere |
| Tectonic activity (0–10) | `seismicActivity` | Lithosphere |
| Volcanic activity (0–10) | `seismicActivity` | Lithosphere |
| Sea level change (mm) | `globalSeaLevelMm` | Hydrosphere |
| Ocean temperature (°C) | `surfaceTemperatureCelsius` | Ocean |
| Forest cover (%) | `canopyCoverPercentage` | Forest |
| Biodiversity index (0–100) | `totalBiomassPgC` (proxy) | Biosphere |

Derived outputs — global mean temperature, ocean pH, glacier mass balance, coral reef health, extinction risk, carbon sequestration — are calculated from cross-sphere feedback formulas modelled on the `interactsWith` relationships in the ontology. The formulas are directionally correct based on published climate science but are simplified for educational use, not calibrated simulations.

Three preset scenarios are included alongside a baseline reset:

- **Baseline** — current real-world values (CO₂ 420ppm, forest 31%, ocean 17°C)
- **Hothouse Earth** — CO₂ 900ppm, ocean 29°C, forest 12%, sea level +500mm. Comparable to Eocene conditions (~50 million years ago)
- **Super-eruption** — volcanic activity 9/10, demonstrating the SO₂ aerosol cooling paradox where surface temperature is suppressed despite elevated CO₂
- **Restored Earth** — CO₂ 310ppm, forest 62%, biodiversity 91/100. See the section below.

---

## Baseline to Restored Earth — what would it take?

The simulator's **Restored Earth** scenario (CO₂ 310ppm, ozone 330 DU, sea level −20mm, ocean temperature 15°C, forest cover 62%, biodiversity index 91) represents a late 22nd-century outcome if sustained global action is taken across all spheres simultaneously. It is not a near-term policy target — it describes what a genuinely recovered planet would look like, and how far the current baseline sits from it.

### CO₂: 420 → 310ppm

Reaching 310ppm is not achievable by emissions reduction alone — it requires active carbon drawdown at scale. The primary pathways under serious research and deployment are:

- **Reforestation and ecosystem restoration** — natural carbon sinks remain the most cost-effective drawdown mechanism. The IPCC estimates forests, soils, and wetlands could sequester 10–12 GtCO₂/year if restored at scale, roughly 25–30% of current annual emissions. [^1]
- **Enhanced weathering** — spreading crushed silicate rock (basalt) on agricultural land accelerates geological weathering, locking CO₂ into carbonate minerals. Studies suggest a potential of 2–4 GtCO₂/year globally. [^2]
- **Direct air capture (DAC)** — industrial facilities that chemically bind atmospheric CO₂. Currently expensive (~$300–600/tonne) and energy-intensive, but costs are falling. Global capacity as of 2024 was approximately 0.01 MtCO₂/year — orders of magnitude below what 310ppm would require. [^3]
- **Ocean-based carbon removal** — kelp farming, iron fertilisation, and ocean alkalinity enhancement are all under active research. The ocean already absorbs ~25% of annual CO₂ emissions; enhancing this capacity without ecological harm is an open scientific challenge. [^4]

The IPCC's most optimistic SSP1-1.9 scenario reaches approximately 350ppm by 2100 with aggressive decarbonisation. Returning to 310ppm — pre-1960 levels — is a multi-century trajectory even under ideal conditions.

### Ocean temperature: 17 → 15°C

Ocean temperature is the most inertial parameter in the system. The ocean has absorbed approximately 90% of the excess heat accumulated since industrialisation, and that heat dissipates over centuries, not decades. A sustained return to 15°C global mean ocean surface temperature would require CO₂ to remain below ~320ppm for 50–100 years minimum. This is the reason the Restored Earth scenario sits so far in the future — the atmosphere can be decarbonised faster than the ocean can cool. [^5]

### Forest cover: 31 → 62%

Doubling global forest cover is the most tractable of the major parameters. There is sufficient degraded and marginal land globally — estimated at 900 million hectares suitable for restoration without displacing food production. [^6] Key initiatives include:

- **The Bonn Challenge** — a global goal to restore 350 million hectares of degraded land by 2030
- **UN Decade on Ecosystem Restoration (2021–2030)** — coordinating restoration across biomes
- **30x30** — the global target to protect 30% of land and ocean by 2030, agreed at COP15 in Montreal (2022)

The constraint is not land availability but time: a mature closed-canopy forest takes 50–150 years to establish and accumulate significant carbon stocks. Planting today commits to carbon outcomes in the 2070s–2100s.

### Biodiversity: 72 → 91

Biodiversity recovery follows habitat restoration but faces a hard constraint: extinction is irreversible. The current rate of species loss is estimated at 100–1,000 times the natural background rate. [^7] Recovery pathways include:

- **Halting further habitat loss** — the most urgent intervention; every species lost permanently reduces the ceiling of what recovery can achieve
- **Expanding protected areas** — the 30x30 commitment, if met, would significantly slow loss rates
- **Rewilding** — reintroduction of keystone species to restore trophic cascades (wolf reintroduction to Yellowstone produced measurable changes in river geomorphology via restored trophic cascades) [^8]
- **Assisted migration** — moving species poleward or to higher elevation as climate zones shift

### The biosphere as the primary lever

The simulator makes a key structural point visible: the biosphere parameters (forest cover, biodiversity) are the ones most directly under human control in the near term, requiring no technology breakthroughs — only different land use decisions. And they feed back into every other sphere:

- More forest → more CO₂ drawdown → slower atmospheric warming → slower ocean warming → slower glacier melt → slower sea level rise
- Higher biodiversity → more resilient carbon sinks → more stable soil formation → reduced erosion → healthier watersheds

This is reflected directly in the ontology: the `carbonStockPgC` Telemetry field on the `Forest` interface and `soilCarbonPgC` on `Grassland` are the fields that would carry the most policy-relevant signal in a live ADT implementation connected to real restoration monitoring data.

The path to Restored Earth runs through the biosphere first.

### Timeline summary

| Parameter | Current | 2050 (ambitious) | 2100 (optimistic) | Restored Earth |
|---|---|---|---|---|
| CO₂ (ppm) | 420 | 350–400 | 310–350 | 310 |
| Ocean temp (°C) | 17 | 17.5–18 | 16–17 | 15 |
| Forest cover (%) | 31 | 35–40 | 45–55 | 62 |
| Biodiversity index | 72 | 65–70 | 70–80 | 91 |
| Sea level change (mm) | +100 | +150–200 | +200–400 | −20 |

*2050 and 2100 values reflect the IPCC SSP1-1.9 most optimistic pathway. Restored Earth represents a multi-century recovery scenario, not a dated projection.*

---

## Sources and further reading

[^1]: IPCC (2022). *Climate Change 2022: Mitigation of Climate Change.* Working Group III, Sixth Assessment Report. Chapter 7: Agriculture, Forestry and Other Land Uses. [https://www.ipcc.ch/report/ar6/wg3/](https://www.ipcc.ch/report/ar6/wg3/)

[^2]: Beerling, D.J. et al. (2020). Potential for large-scale CO₂ removal via enhanced rock weathering with croplands. *Nature*, 583, 242–248. [https://doi.org/10.1038/s41586-020-2448-9](https://doi.org/10.1038/s41586-020-2448-9)

[^3]: IEA (2024). *Direct Air Capture: A key technology for net zero.* International Energy Agency. [https://www.iea.org/reports/direct-air-capture-2022](https://www.iea.org/reports/direct-air-capture-2022)

[^4]: National Academies of Sciences, Engineering, and Medicine (2022). *A Research Strategy for Ocean-based Carbon Dioxide Removal and Sequestration.* The National Academies Press. [https://doi.org/10.17226/26278](https://doi.org/10.17226/26278)

[^5]: Cheng, L. et al. (2022). Another Record: Ocean Warming Continues through 2021 despite La Niña Conditions. *Advances in Atmospheric Sciences*, 39, 373–385. [https://doi.org/10.1007/s00376-022-1461-3](https://doi.org/10.1007/s00376-022-1461-3)

[^6]: Bastin, J.F. et al. (2019). The global tree restoration potential. *Science*, 365(6448), 76–79. [https://doi.org/10.1126/science.aax0848](https://doi.org/10.1126/science.aax0848)

[^7]: Ceballos, G. et al. (2017). Biological annihilation via the ongoing sixth mass extinction signaled by vertebrate population losses and declines. *PNAS*, 114(30). [https://doi.org/10.1073/pnas.1704949114](https://doi.org/10.1073/pnas.1704949114)

[^8]: Ripple, W.J. & Beschta, R.L. (2012). Trophic cascades in Yellowstone: The first 15 years after wolf reintroduction. *Biological Conservation*, 145(1), 205–213. [https://doi.org/10.1016/j.biocon.2011.11.005](https://doi.org/10.1016/j.biocon.2011.11.005)

---

## Licence

This ontology is provided as open-source sample material. See repository for licence details.
