# rvt-holdout-models

Held-out Revit models for [rvt-rs](https://github.com/DrunkOnJava/rvt-rs) validation
([#408](https://github.com/DrunkOnJava/rvt-rs/issues/408)), authored by hemanth1986.
They were never used to develop or tune rvt-rs.

| Folder | Revit build | IFC exporter | Model |
|---|---|---|---|
| `2022/`, `2022-office/` | 22.1.80.32 | 22.6.2.0 | house, office |
| `2024/`, `2024-office/` | 24.3.60.12 | 24.3.60.12 | house, office |
| `2025/`, `2025-office/` | 25.5.10.17 | 25.5.10.17 | house, office |
| `2026/`, `2026-office/` | 26.5.10.38 | 26.5.10.38 | house, office |
| `2027/`, `2027-office/` | 27.3.0.28 | 27.3.0.28 | house, office |

Each folder holds the `.rvt` saved by that Revit release and the `.ifc` exported by the same
release. There is no Revit 2023 model.

## The two models

**House:** two storeys, 12 m × 8 m, gable roof (30° on the long sides).
10 walls: four joined corners on each floor and a T-junction on the ground floor.
2 floors, the upper one with a stair opening; 1 straight stair with 2 railings.
3 doors, 12 windows, 4 rooms, 4 furniture instances.

**Office:** one storey, L-shaped (16 m × 6 m wing plus 7 m × 8 m wing), 3.5 m high, flat roof.
9 walls: six joined corners (one of them an inside corner) and two T-junctions.
1 floor, 4 doors, 10 windows, 4 rooms, 8 furniture instances.

| IFC contents | House 2024-2027 | House 2022 | Office 2024-2027 | Office 2022 |
|---|---|---|---|---|
| IfcBuildingStorey | 3 | 8 | 2 | 7 |
| IfcWall | 10 | 10 | 9 | 9 |
| IfcSlab | 4 | 2 | 2 | 1 |
| IfcRoof | 1 | 1 | 1 | 1 |
| IfcDoor / IfcWindow | 3 / 12 | 3 / 12 | 4 / 10 | 4 / 10 |
| IfcStair / IfcRailing | 1 / 2 | 1 / 2 | 0 / 0 | 0 / 0 |
| IfcSpace | 4 | 4 | 4 | 4 |
| IfcFurniture | 4 | 4 | 8 | 8 |
| IfcOpeningElement | 16 | 16 | 14 | 14 |
| Qto_*BaseQuantities sets | 55 | 53 | 44 | 44 |

## IFC export

Each `.ifc` was exported with Revit's built-in setup **"IFC4 Reference View [Architecture]"**,
unchanged except **Export base quantities = on**. The file header shows
`ViewDefinition [ReferenceView_V1.2]`. Reference View does not export wall joins
(no `IfcRelConnectsPathElements`), so the joins exist only in the `.rvt`.

## Templates and families

Revit 2024-2027 use their default English-Imperial template (Default-Multi-discipline).
Revit 2022's default template has no furniture, so 2022 uses Residential-Default. Its door,
window and furniture families have different names, and it carries extra empty levels.
The extra levels explain the higher storey count above.

The models were built by a Revit add-in. They are not exports of any real project.

## Licence

[CC BY 4.0](LICENSE). Credit: "hemanth1986".
The door, window and furniture families come from Autodesk's own project templates.
The licence covers hemanth1986's modelling, not Autodesk's content.

Checksums: [`SHA256SUMS.txt`](SHA256SUMS.txt).
