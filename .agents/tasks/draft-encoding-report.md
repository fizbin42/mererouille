# Rapport d’analyse d’encodage de `draft.txt`

## Résumé — réponse directe

**Verdict : le fichier est sain et correctement encodé en UTF-8.** Le décodage UTF-8 strict réussit avec `iconv` et Python, sans octet invalide. Le fichier ne contient **aucun BOM**, aucun caractère de remplacement `U+FFFD`, aucun caractère de largeur nulle, aucun contrôle inattendu et aucun indice usuel de mojibake.

Le copier-coller depuis l’interface web a vraisemblablement conservé une ponctuation Unicode typographique normale : **84 apostrophes courbes `’` (`U+2019`)**, **12 paires de guillemets français `« … »` (`U+00AB`/`U+00BB`)** et **3 points de suspension `…` (`U+2026`)**. Ces caractères sont cohérents avec le texte français et ne constituent pas des erreurs d’encodage. Il n’y a **aucun espace insécable `U+00A0` ni espace fine insécable `U+202F`**.

Seul détail de format à signaler : les fins de ligne sont uniformément **LF**, mais la dernière ligne ne se termine pas par un saut de ligne. Cela n’affecte ni l’UTF-8 ni l’affichage normal du texte.

## Preuves

### Identification du fichier et validation UTF-8

Fichier inspecté uniquement : `/Users/christianfisette/Documents/dnd/Mech/draft.txt`.

- Taille : **12 064 octets**, **11 551 caractères Unicode**.
- Empreinte SHA-256 au moment de l’analyse : `e0818eb436990342097d5f7f5c8374f00c149f7c15ebf4e42f11526b8`.
- `file -b` : `Unicode text, UTF-8 text, with very long lines (565)`.
- `file -bI` : `text/plain; charset=utf-8`.
- `iconv -f UTF-8 -t UTF-8` : succès, sans erreur.
- Python `bytes.decode("utf-8", errors="strict")` : succès, sans `UnicodeDecodeError`.
- Premiers octets : `2d 20 2a 2a 44 61 6e 73` (`- **Dans`) ; ils ne correspondent à aucun BOM.
- BOM UTF-8 `EF BB BF` : **absent**. BOM UTF-16/UTF-32 : **absent**.
- Octets NUL `00` : **0**.
- Le texte est déjà en normalisation Unicode **NFC**, adaptée au texte français précomposé.

### Fins de ligne

- Séquences LF (`\n`) seules : **56**.
- Séquences CRLF (`\r\n`) : **0**.
- CR (`\r`) isolés : **0**.
- Nombre de lignes logiques : **57**.
- Saut de ligne final : **absent**.

Les fins de ligne sont donc homogènes. L’absence de LF final est un détail de style/compatibilité POSIX, pas un problème d’encodage.

### Inventaire des caractères recherchés

| Famille | Point(s) de code | Total | Résultat |
|---|---:|---:|---|
| Espace insécable | `U+00A0` | 0 | Absent |
| Espace fine insécable | `U+202F` | 0 | Absent |
| Apostrophe typographique | `U+2019` `’` | 84 | Présente, usage français normal |
| Autres apostrophes/guillemets simples typographiques | `U+2018`, `U+201A`, `U+201B` | 0 | Absents |
| Guillemets français | `U+00AB` `«`, `U+00BB` `»` | 12 + 12 | 12 paires équilibrées |
| Guillemets doubles courbes | `U+201C` à `U+201F` | 0 | Absents |
| Tirets Unicode | `U+2010` à `U+2015`, `U+2212` | 0 | Absents |
| Points de suspension | `U+2026` `…` | 3 | Présents sur une seule ligne |
| Largeur nulle / formatage invisible | `U+200B`, `U+200C`, `U+200D`, `U+2060`, `U+FEFF` | 0 | Absents |
| Trait d’union conditionnel | `U+00AD` | 0 | Absent |
| Caractère de remplacement | `U+FFFD` | 0 | Absent |
| Contrôles inattendus `Cc`/`Cf` | — | 0 | Aucun ; également 0 tabulation, saut vertical ou saut de page |
| Marqueurs usuels de mojibake | `Ã`, `Â`, `â€™`, `â€œ`, `â€”`, `ðŸ`, `ï»¿`, `ï¿½`, etc. | 0 ligne | Aucun indice détecté |

Il n’existe par ailleurs **aucun caractère Unicode de catégorie `Cf`** dans le fichier. Cela confirme l’absence de marques bidirectionnelles et de caractères de formatage invisibles, au-delà de la liste explicite ci-dessus.

### Emplacements de la ponctuation Unicode

Les numéros ci-dessous sont les lignes physiques de [`draft.txt`](/Users/christianfisette/Documents/dnd/Mech/draft.txt).

#### Apostrophe courbe `’` — `U+2019`, 84 occurrences

Présente sur 27 lignes, uniquement dans des contractions ou élisions françaises telles que `s’accrochent`, `d’une`, `l’épave` et `qu’elle` (par exemple [`draft.txt:1`](/Users/christianfisette/Documents/dnd/Mech/draft.txt#L1) et [`draft.txt:3`](/Users/christianfisette/Documents/dnd/Mech/draft.txt#L3)). Emplacements exacts, sous la forme `ligne:colonnes` :

```text
1:135,159,219,355
3:380,404
7:113,212
9:97,180,314,319
11:68,95,313
15:9,35,65,235,355,379,392
17:64,132,279,316,454
19:209,221,250,316,373,379,437
21:86,193
23:439
25:148,274
27:99,354
29:288,326
31:84,319
33:318,425
35:72,215
37:41,70,192,222
39:78,262,296,513,528
41:369,415
43:60,84
45:327
47:70,154,218,225,266
49:48,160,169,273,299,357
51:66,129,136,187
53:40,275
55:55,278
57:42,133
```

#### Guillemets français `«` / `»` — `U+00AB` / `U+00BB`, 12 paires

Les comptes sont équilibrés et chaque paire encadre visiblement du dialogue. Lignes et colonnes :

```text
L9   : « col. 296, » col. 378
L15  : « col. 102, » col. 192
L17  : « col. 381, » col. 463
L23  : « col. 319, » col. 419
L29  : « col. 193, » col. 270
L31  : « col. 384, » col. 413
L39  : « col. 502, » col. 563
L45  : « col. 337, » col. 399
L49  : « col. 89,  » col. 144 ; « col. 351, » col. 364
L51  : « col. 42,  » col. 114
L55  : « col. 322, » col. 371
```

Exemples : [`draft.txt:9`](/Users/christianfisette/Documents/dnd/Mech/draft.txt#L9), [`draft.txt:49`](/Users/christianfisette/Documents/dnd/Mech/draft.txt#L49) et [`draft.txt:55`](/Users/christianfisette/Documents/dnd/Mech/draft.txt#L55). Les espaces à l’intérieur des guillemets sont des espaces ordinaires `U+0020`, et non des espaces insécables.

#### Points de suspension `…` — `U+2026`, 3 occurrences

Les trois occurrences sont dans le même dialogue, à [`draft.txt:55`](/Users/christianfisette/Documents/dnd/Mech/draft.txt#L55), colonnes **330, 351 et 369** : `Arkadi… il a pris Goldoroff… la route du nord…`. Cet usage est cohérent et non corrompu.

### Autres caractères non ASCII

En dehors de la ponctuation ci-dessus, l’inventaire non ASCII ne contient que des lettres françaises attendues :

```text
U+00C0 À ×4      U+00C7 Ç ×1
U+00E0 à ×33     U+00E2 â ×3
U+00E7 ç ×7      U+00E8 è ×45
U+00E9 é ×197    U+00EA ê ×14
U+00EE î ×5      U+00EF ï ×1
U+00F4 ô ×4      U+00F9 ù ×1
```

Aucune séquence du type `Ã©` à la place de `é`, `â€™` à la place de `’`, ou `Â«` à la place de `«` n’a été trouvée. Le décodage strict, l’inventaire cohérent et l’absence de ces marqueurs convergent vers l’absence de mojibake.

## Conclusions et recommandations

1. **Aucune réparation d’encodage n’est nécessaire.** Conserver le fichier en UTF-8 sans BOM est approprié.
2. **Conserver les fins de ligne LF.** Ajouter éventuellement un LF final seulement si un outil, un linter ou une convention de dépôt l’exige ; ce serait une correction de format, pas d’encodage.
3. **Conserver la ponctuation typographique** (`’`, `« »`, `…`) si le système cible accepte Unicode, ce qui est le cas général. Elle est lisible, équilibrée et adaptée au français.
4. Si une cible impose explicitement l’ASCII, effectuer alors une conversion volontaire et contrôlée (`’` → `'`, `« … »` → `"…"`, `…` → `...`) plutôt qu’un changement d’encodage global. Une telle conversion ferait perdre de la typographie et n’est pas recommandée sans contrainte réelle.
5. Pour une typographie française stricte, on pourrait choisir des espaces insécables ou fines insécables autour du texte entre `« »`. Elles sont actuellement absentes, ce qui favorise toutefois la portabilité lors des copier-coller ; leur absence n’est pas une anomalie.
6. Le fichier source n’a pas été modifié pendant cette investigation.
