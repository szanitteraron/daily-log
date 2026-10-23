# daily-log – közös Mai nap és napi napló

Privát repó. Itt él a **közös Mai nap** artifact build-kimenete és a napi napló gépi másolata.
Céges (LB) és személyes tételeket is tartalmaz, ezért NEM az `lb-product-cockpit` repóban van (D014, D017).

| Mi | Hol |
| --- | --- |
| Mai nap artifact (élő) | https://claude.ai/artifact/Cqfs98sDycG4iMFybqBG6W – adattár: `data/plan/day/<ÉÉÉÉ-HH-NN>` |
| Napi napló (olvasásra) | Claude Doc „Napi napló”: https://claude.ai/artifact/8kv3w85r6FXBGC9QqS3vai |
| Napi napló (gépi) | `days/<ÉÉÉÉ-HH-NN>.md` (frontmatter + tételek + meta-értékelés) |
| Build-kimenet | `dist/day.html` |
| Napi lezárás protokollja | `CLOSE_DAY.md` (ütemezett feladat, 23:30 Europe/Budapest) |

## Build
A kód az `lb-product-cockpit` repóban van (sablon + `src/build_day.py`); az adat a két Project OS buildjéből:
```
cd lb-product-cockpit
python3 src/build_projects.py
(cd ../personal-linkedin-writing && python3 ../lb-product-cockpit/src/build_projects.py --space-root .)
python3 src/build_day.py --personal ../personal-linkedin-writing --out ../daily-log/dist/day.html
```
Publikálás: Artifact publish, `url` = a fenti Mai nap link, capabilities nélkül (a tárolt deklaráció megmarad).

## Publikálás (D019)
Ez a lap a `lb-product-cockpit` közös sablonjából épül. Publikálni csak commit és push után szabad, és sablonváltozásnál mindhárom artifactot (LB, Personal, Mai nap) újra kell építeni. Részletek: lb-product-cockpit `AGENTS.md`, „Publikálás: előbb repó, aztán artifact”.
