# Earth Ontology — DTDL v3 Models

Sample DTDL v3 interface models representing Earth's systems for use with Azure Digital Twins.

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
        │   └── Exosphere  ──interactsWith──► Geospace
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

## Files

| File | Interfaces |
|------|-----------|
| `Universe.json` | Universe |
| `Geospace.json` | Geospace |
| `Earth.json` | Earth |
| `Atmosphere.json` | Atmosphere, Troposphere, Stratosphere, Mesosphere, Thermosphere, Exosphere |
| `Lithosphere.json` | Lithosphere, Crust, Mantle, Core |
| `Hydrosphere.json` | Hydrosphere, Ocean, Lake, River, Glacier |
| `Biosphere.json` | Biosphere, Forest, Grassland, Desert, Mountain |

## DTDL design notes

- All interfaces use **DTDL v3** (`dtmi:dtdl:context;3`)
- DTMIs follow the pattern `dtmi:earthontology:{InterfaceName};1`
- Subclass interfaces use `extends` to inherit from their parent sphere interface
- Sphere-level interactions (e.g. Biosphere ↔ Atmosphere) are modelled as `Relationship` declarations
- Each file with multiple interfaces is a valid DTDL **array** — upload the whole file to ADT in one batch
- Telemetry fields are included for properties intended to receive live sensor/IoT data
- Enum schemas are used for categorical properties (crustType, forestType, desertType, etc.)

## Upload to Azure Digital Twins

Using the [ADT Tools UploadModels](https://github.com/Azure/opendigitaltwins-tools/tree/main/ADTTools) CLI:

```bash
# Upload all models (order matters — root interfaces first)
UploadModels -t <tenantId> -c <clientId> -h <yourInstance>.api.wcus.digitaltwins.azure.net \
  Universe.json Geospace.json Earth.json Atmosphere.json Lithosphere.json Hydrosphere.json Biosphere.json
```

Or drag-and-drop each `.json` file into [ADT Explorer](https://explorer.digitaltwins.azure.net/).

## Validation

Use the [DTDL Validator](https://github.com/Azure/opendigitaltwins-tools/tree/main/DTDLValidator) to check models before uploading:

```bash
DTDLValidator --folder ./DTDL
```
