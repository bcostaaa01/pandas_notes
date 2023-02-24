# 🐼 Pandas Notes

This is a collection of notes I took for the Python library Pandas.

# How to install Pandas

In order to install Pandas, download it using the pip package installer:

```shell
pip install pandas
```

# Using Pandas

In order to use Pandas in a projetc, import it to the script:

```python
import pandas as pd 
```

Afterwards, you can use pd to use any functions and methods that the library offers.

# Reading CSV data

These notes were written with the following data set: https://github.com/KeithGalli/pandas/blob/master/pokemon_data.csv - download it as a raw CSV file and place it in the dame directory as your project.

In order to read a CSV file, use the read_csv() method:

```python
import pandas as pd

df = pd.read_csv("pokemon_data.csv")

print(df)
```

When you print the contents of the CSV file, it should look like this:

```shell
#                   Name   Type 1  ... Speed  Generation  Legendary
0      1              Bulbasaur    Grass  ...    45           1      False
1      2                Ivysaur    Grass  ...    60           1      False
2      3               Venusaur    Grass  ...    80           1      False
3      3  VenusaurMega Venusaur    Grass  ...    80           1      False
4      4             Charmander     Fire  ...    65           1      False
..   ...                    ...      ...  ...   ...         ...        ...
795  719                Diancie     Rock  ...    50           6       True
796  719    DiancieMega Diancie     Rock  ...   110           6       True
797  720    HoopaHoopa Confined  Psychic  ...    70           6       True
798  720     HoopaHoopa Unbound  Psychic  ...    80           6       True
799  721              Volcanion     Fire  ...    70           6       True

[800 rows x 12 columns]
```

# Delimiting

If you pass in the delimiter argument to the read_csv() function, you can delimit the CSV file on the terminal:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv', delimiter="\t")

print(df.head(5))
```

# Reading the headers/columns

In order to read the headers/columns of a CSV file:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv', delimiter="\t")

print(df.head(5).columns)
```

In the terminal:

```shell
Index(['#,Name,Type 1,Type 2,HP,Attack,Defense,Sp. Atk,Sp. Def,Speed,Generation,Legendary'], dtype='object')
```

# Reading a specific column

In order to read a specific column from a CSV file:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

print(df['Name'])
```

In the terminal:

```shell
0                  Bulbasaur
1                    Ivysaur
2                   Venusaur
3      VenusaurMega Venusaur
4                 Charmander
               ...          
795                  Diancie
796      DiancieMega Diancie
797      HoopaHoopa Confined
798       HoopaHoopa Unbound
799                Volcanion
Name: Name, Length: 800, dtype: object
```

# Read each row

In order to read each row, you can use the iloc() function:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

print(df.iloc[1])
```

In the terminal:

```shell
#                   2
Name          Ivysaur
Type 1          Grass
Type 2         Poison
HP                 60
Attack             62
Defense            63
Sp. Atk            80
Sp. Def            80
Speed              60
Generation          1
Legendary       False
Name: 1, dtype: object
```

From a row until another specific row:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

print(df.iloc[1:4])
```

In the terminal:

```shell
#                   Name Type 1  ... Speed  Generation  Legendary
1  2                Ivysaur  Grass  ...    60           1      False
2  3               Venusaur  Grass  ...    80           1      False
3  3  VenusaurMega Venusaur  Grass  ...    80           1      False
```

# Read a specific location

In order to read a specific row and column:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

print(df.iloc[2,1])
```

In the terminal:

```shell
Venusaur
```

# Iterate through rows

In order to iterate through a row, you can use a for loop:

```python
for index, row in df.iterrows():
	print(index, row)
```

In the terminal:

```shell
...
799 #                   721
Name          Volcanion
Type 1             Fire
Type 2            Water
HP                   80
Attack              110
Defense             120
Sp. Atk             130
Sp. Def              90
Speed                70
Generation            6
Legendary          True
Name: 799, dtype: object
```

# Getting rows based on a specific condition

In order to get rows based on a specific condition, you can use the loc() function, which allows us to find specific data that isn’t just integer-based:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

fire = df.loc[df['Type 1'] == 'Fire']

print(fire)
```

This allows us to get only the rows that have Type 1 = “Fire”.

In the terminal:

```shell
#                       Name Type 1  ... Speed  Generation  Legendary
4      4                 Charmander   Fire  ...    65           1      False
5      5                 Charmeleon   Fire  ...    80           1      False
6      6                  Charizard   Fire  ...   100           1      False
7      6  CharizardMega Charizard X   Fire  ...   100           1      False
8      6  CharizardMega Charizard Y   Fire  ...   100           1      False
42    37                     Vulpix   Fire  ...    65           1      False
43    38                  Ninetales   Fire  ...   100           1      False
63    58                  Growlithe   Fire  ...    60           1      False
64    59                   Arcanine   Fire  ...    95           1      False
83    77                     Ponyta   Fire  ...    90           1      False
84    78                   Rapidash   Fire  ...   105           1      False
135  126                     Magmar   Fire  ...    93           1      False
147  136                    Flareon   Fire  ...    65           1      False
158  146                    Moltres   Fire  ...    90           1       True
169  155                  Cyndaquil   Fire  ...    65           2      False
170  156                    Quilava   Fire  ...    80           2      False
171  157                 Typhlosion   Fire  ...   100           2      False
236  218                     Slugma   Fire  ...    20           2      False
237  219                   Magcargo   Fire  ...    30           2      False
259  240                      Magby   Fire  ...    83           2      False
263  244                      Entei   Fire  ...   100           2       True
270  250                      Ho-oh   Fire  ...    90           2       True
276  255                    Torchic   Fire  ...    45           3      False
277  256                  Combusken   Fire  ...    55           3      False
278  257                   Blaziken   Fire  ...    80           3      False
279  257      BlazikenMega Blaziken   Fire  ...   100           3      False
352  322                      Numel   Fire  ...    35           3      False
353  323                   Camerupt   Fire  ...    40           3      False
354  323      CameruptMega Camerupt   Fire  ...    20           3      False
355  324                    Torkoal   Fire  ...    20           3      False
435  390                   Chimchar   Fire  ...    61           4      False
436  391                   Monferno   Fire  ...    81           4      False
437  392                  Infernape   Fire  ...   108           4      False
518  467                  Magmortar   Fire  ...    83           4      False
542  485                    Heatran   Fire  ...    77           4       True
557  498                      Tepig   Fire  ...    45           5      False
558  499                    Pignite   Fire  ...    55           5      False
559  500                     Emboar   Fire  ...    65           5      False
572  513                    Pansear   Fire  ...    64           5      False
573  514                   Simisear   Fire  ...   101           5      False
614  554                   Darumaka   Fire  ...    50           5      False
615  555    DarmanitanStandard Mode   Fire  ...    95           5      False
616  555         DarmanitanZen Mode   Fire  ...    55           5      False
692  631                    Heatmor   Fire  ...    65           5      False
721  653                   Fennekin   Fire  ...    60           6      False
722  654                    Braixen   Fire  ...    73           6      False
723  655                    Delphox   Fire  ...   104           6      False
730  662                Fletchinder   Fire  ...    84           6      False
731  663                 Talonflame   Fire  ...   126           6      False
735  667                     Litleo   Fire  ...    72           6      False
736  668                     Pyroar   Fire  ...   106           6      False
799  721                  Volcanion   Fire  ...    70           6       True

[52 rows x 12 columns]
```

# High Level description of your data (min, max, mean, std dev, etc.)

In order to get a high level description of a data set:

```python
df.describe()
```

In the terminal:

```shell
#          HP      Attack  ...     Sp. Def       Speed  Generation
count  800.000000  800.000000  800.000000  ...  800.000000  800.000000   800.00000
mean   362.813750   69.258750   79.001250  ...   71.902500   68.277500     3.32375
std    208.343798   25.534669   32.457366  ...   27.828916   29.060474     1.66129
min      1.000000    1.000000    5.000000  ...   20.000000    5.000000     1.00000
25%    184.750000   50.000000   55.000000  ...   50.000000   45.000000     2.00000
50%    364.500000   65.000000   75.000000  ...   70.000000   65.000000     3.00000
75%    539.250000   80.000000  100.000000  ...   90.000000   90.000000     5.00000
max    721.000000  255.000000  190.000000  ...  230.000000  180.000000     6.00000

[8 rows x 8 columns]
```

You can sort a data set by value:

```python
df.sort_values("Name")

print(df)
```

In the terminal:

```shell
#                   Name   Type 1  ... Speed  Generation  Legendary
0      1              Bulbasaur    Grass  ...    45           1      False
1      2                Ivysaur    Grass  ...    60           1      False
2      3               Venusaur    Grass  ...    80           1      False
3      3  VenusaurMega Venusaur    Grass  ...    80           1      False
4      4             Charmander     Fire  ...    65           1      False
..   ...                    ...      ...  ...   ...         ...        ...
795  719                Diancie     Rock  ...    50           6       True
796  719    DiancieMega Diancie     Rock  ...   110           6       True
797  720    HoopaHoopa Confined  Psychic  ...    70           6       True
798  720     HoopaHoopa Unbound  Psychic  ...    80           6       True
799  721              Volcanion     Fire  ...    70           6       True

[800 rows x 12 columns]
```

Using ascending=False:

```python
df.sort_values("Name", ascending=False) # will not sort ascendingly

print(df)
```

In the terminal:

```shell
#                   Name   Type 1  ... Speed  Generation  Legendary
0      1              Bulbasaur    Grass  ...    45           1      False
1      2                Ivysaur    Grass  ...    60           1      False
2      3               Venusaur    Grass  ...    80           1      False
3      3  VenusaurMega Venusaur    Grass  ...    80           1      False
4      4             Charmander     Fire  ...    65           1      False
..   ...                    ...      ...  ...   ...         ...        ...
795  719                Diancie     Rock  ...    50           6       True
796  719    DiancieMega Diancie     Rock  ...   110           6       True
797  720    HoopaHoopa Confined  Psychic  ...    70           6       True
798  720     HoopaHoopa Unbound  Psychic  ...    80           6       True
799  721              Volcanion     Fire  ...    70           6       True
```

Using ascending=True:

```python
#                   Name   Type 1  ... Speed  Generation  Legendary
495  446               Munchlax   Normal  ...     5           4      False
230  213                Shuckle      Bug  ...     5           2      False
658  597              Ferroseed    Grass  ...    10           5      False
486  438                 Bonsly     Rock  ...    10           4      False
359  328               Trapinch   Ground  ...    10           3      False
..   ...                    ...      ...  ...   ...         ...        ...
429  386     DeoxysAttack Forme  Psychic  ...   150           3       True
71    65  AlakazamMega Alakazam  Psychic  ...   150           1      False
428  386     DeoxysNormal Forme  Psychic  ...   150           3       True
315  291                Ninjask      Bug  ...   160           3      False
431  386      DeoxysSpeed Forme  Psychic  ...   180           3       True
```

Using Ascending=[1, 0] (first one True, second one False):

```python
sorted = df.sort_values(['Type 1', 'Speed'], ascending=[1,1])

print(sorted)
```

In the terminal:

```shell
#                  Name Type 1  ... Speed  Generation  Legendary
230  213               Shuckle    Bug  ...     5           2      False
219  204                Pineco    Bug  ...    15           2      False
289  266               Silcoon    Bug  ...    15           3      False
291  268               Cascoon    Bug  ...    15           3      False
288  265               Wurmple    Bug  ...    20           3      False
..   ...                   ...    ...  ...   ...         ...        ...
713  647  KeldeoOrdinary Forme  Water  ...   108           5      False
714  647  KeldeoResolute Forme  Water  ...   108           5      False
130  121               Starmie  Water  ...   115           1      False
466  419              Floatzel  Water  ...   115           4      False
726  658              Greninja  Water  ...   122           6      False
```

# Making changes to a Data Frame

In order to make changes to a Data Frame:

Take the following example:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

print(df.head(5))
```

In the terminal:

```shell
#                   Name Type 1  ... Speed  Generation  Legendary
0  1              Bulbasaur  Grass  ...    45           1      False
1  2                Ivysaur  Grass  ...    60           1      False
2  3               Venusaur  Grass  ...    80           1      False
3  3  VenusaurMega Venusaur  Grass  ...    80           1      False
4  4             Charmander   Fire  ...    65           1      False
```

Adding a total value of a particular data frame:

```python
df["Total"] = df["HP"] + df["Defense"] + df["Speed"]

print(df.head(5))
```

In the terminal:

```shell
#                   Name Type 1  Type 2  ...  Speed  Generation  Legendary  Total
0  1              Bulbasaur  Grass  Poison  ...     45           1      False    139
1  2                Ivysaur  Grass  Poison  ...     60           1      False    183
2  3               Venusaur  Grass  Poison  ...     80           1      False    243
3  3  VenusaurMega Venusaur  Grass  Poison  ...     80           1      False    283
4  4             Charmander   Fire     NaN  ...     65           1      False    147
```

A different way is to drop a specific column:

```python
df.drop(columns=["Total"])
```

Resetting the data frame:

```python
df = df.drop(columns=["Total"])
```

This will remove the specific column that we added from the Data Frame.

# Summing multiple columns to create a new column

In order to create a new column as the sum of multiple columns:

```python
df['Total'] = df.iloc[:, 4:10].sum(axis=1) # axis=0 - vertically

print(df.head(5))
```

In the terminal:

```shell
#                   Name Type 1  Type 2  ...  Speed  Generation  Legendary  Total
0  1              Bulbasaur  Grass  Poison  ...     45           1      False    318
1  2                Ivysaur  Grass  Poison  ...     60           1      False    405
2  3               Venusaur  Grass  Poison  ...     80           1      False    525
3  3  VenusaurMega Venusaur  Grass  Poison  ...     80           1      False    625
4  4             Charmander   Fire     NaN  ...     65           1      False    309
```

Changing direction of sum:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

df["Total"] = df.iloc[:, 4:10].sum(axis=1)

cols = list(df.columns) # create a list of the values of columns

df = df[cols[0:4] + [cols[-1]] + cols[4:8]]

print(df.head(5))
```

In the terminal:

```shell
#                   Name Type 1  Type 2  Total  HP  Attack  Defense  Sp. Atk
0  1              Bulbasaur  Grass  Poison    318  45      49       49       65
1  2                Ivysaur  Grass  Poison    405  60      62       63       80
2  3               Venusaur  Grass  Poison    525  80      82       83      100
3  3  VenusaurMega Venusaur  Grass  Poison    625  80     100      123      122
4  4             Charmander   Fire     NaN    309  39      52       43       60
```

# Rearranging columns

Writing a CSV:

```python
df.to_csv("modified.csv")
```

This will create a new CSV file with the configuration you did on your Pandas script.

```shell
#                   Name Type 1  Type 2  Total  HP  Attack  Defense  Sp. Atk
0  1              Bulbasaur  Grass  Poison    318  45      49       49       65
1  2                Ivysaur  Grass  Poison    405  60      62       63       80
2  3               Venusaur  Grass  Poison    525  80      82       83      100
3  3  VenusaurMega Venusaur  Grass  Poison    625  80     100      123      122
4  4             Charmander   Fire     NaN    309  39      52       43       60
```

Removing indexes, f ex:

```python
df.to_csv("modified.csv", index=False)
```

Exporting to Excel:

```python
df.to_excel()
```

Exporting to a .txt file:

```python
df.to_csv("modified.txt", index=False, sep="\t")
```

# Filtering data

Getting single column:

```python
df.loc[df["Type 1"] == "Grass"]
```

Getting multiple columns:

```python
print(df.loc[(df["Type 1"] == "Grass") & (df["Type 2"] == "Poison")])
```

Using OR operator:

```python
print(df.loc[(df["Type 1"] == "Grass") | (df["Type 2"] == "Poison")])
```

3 columns:

```python
print(df.loc[(df["Type 1"] == "Grass") & (df["Type 2"] == "Poison") & (df["HP"] > 70)])
```

In the terminal:

```shell
#                   Name Type 1  ... Speed  Generation  Legendary
2      3               Venusaur  Grass  ...    80           1      False
3      3  VenusaurMega Venusaur  Grass  ...    80           1      False
50    45              Vileplume  Grass  ...    50           1      False
77    71             Victreebel  Grass  ...    70           1      False
652  591              Amoonguss  Grass  ...    30           5      False
```

Creating a new CSV file out of the filtered data:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

filtered = df.loc[(df["Type 1"] == "Grass") & (df["Type 2"] == "Poison") & (df["HP"] > 70)]

filtered.to_csv("filtered.csv", index=False)
```

Filtered CSV file content:

```shell
#,Name,Type 1,Type 2,HP,Attack,Defense,Sp. Atk,Sp. Def,Speed,Generation,Legendary
3,Venusaur,Grass,Poison,80,82,83,100,100,80,1,False
3,VenusaurMega Venusaur,Grass,Poison,80,100,123,122,120,80,1,False
45,Vileplume,Grass,Poison,75,80,85,110,90,50,1,False
71,Victreebel,Grass,Poison,80,105,65,100,70,70,1,False
591,Amoonguss,Grass,Poison,114,85,70,85,80,30,5,False
```

Resetting the index: 

```python
filtered = filtered.reset_index(drop=True, inplace=True)
```

# Regex filtering (filter based on textual patterns)

Filter names that contain “Mega”:

```python
df.loc[df["Name"].str.contains("Mega")]
```

Full implementation:

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

filtered = df.loc[df["Name"].str.contains("Mega")]

filtered.to_csv("filtered.csv", index=False)
```

Filtered CSV file content:

```shell
130,GyaradosMega Gyarados,Water,Dark,95,155,109,70,130,81,1,False
142,AerodactylMega Aerodactyl,Rock,Flying,80,135,85,70,95,150,1,False
150,MewtwoMega Mewtwo X,Psychic,Fighting,106,190,100,154,100,130,1,True
150,MewtwoMega Mewtwo Y,Psychic,,106,150,70,194,120,140,1,True
154,Meganium,Grass,,80,82,100,83,100,80,2,False
181,AmpharosMega Ampharos,Electric,Dragon,90,95,105,165,110,45,2,False
208,SteelixMega Steelix,Steel,Ground,75,125,230,55,95,30,2,False
212,ScizorMega Scizor,Bug,Steel,70,150,140,65,100,75,2,False
214,HeracrossMega Heracross,Bug,Fighting,80,185,115,40,105,75,2,False
229,HoundoomMega Houndoom,Dark,Fire,75,90,90,140,90,115,2,False
248,TyranitarMega Tyranitar,Rock,Dark,100,164,150,95,120,71,2,False
254,SceptileMega Sceptile,Grass,Dragon,70,110,75,145,85,145,3,False
257,BlazikenMega Blaziken,Fire,Fighting,80,160,80,130,80,100,3,False
260,SwampertMega Swampert,Water,Ground,100,150,110,95,110,70,3,False
282,GardevoirMega Gardevoir,Psychic,Fairy,68,85,65,165,135,100,3,False
302,SableyeMega Sableye,Dark,Ghost,50,85,125,85,115,20,3,False
303,MawileMega Mawile,Steel,Fairy,50,105,125,55,95,50,3,False
306,AggronMega Aggron,Steel,,70,140,230,60,80,50,3,False
308,MedichamMega Medicham,Fighting,Psychic,60,100,85,80,85,100,3,False
310,ManectricMega Manectric,Electric,,70,75,80,135,80,135,3,False
319,SharpedoMega Sharpedo,Water,Dark,70,140,70,110,65,105,3,False
323,CameruptMega Camerupt,Fire,Ground,70,120,100,145,105,20,3,False
334,AltariaMega Altaria,Dragon,Fairy,75,110,110,110,105,80,3,False
354,BanetteMega Banette,Ghost,,64,165,75,93,83,75,3,False
359,AbsolMega Absol,Dark,,65,150,60,115,60,115,3,False
362,GlalieMega Glalie,Ice,,80,120,80,120,80,100,3,False
373,SalamenceMega Salamence,Dragon,Flying,95,145,130,120,90,120,3,False
376,MetagrossMega Metagross,Steel,Psychic,80,145,150,105,110,110,3,False
380,LatiasMega Latias,Dragon,Psychic,80,100,120,140,150,110,3,True
381,LatiosMega Latios,Dragon,Psychic,80,130,100,160,120,110,3,True
384,RayquazaMega Rayquaza,Dragon,Flying,105,180,100,180,100,115,3,True
428,LopunnyMega Lopunny,Normal,Fighting,65,136,94,54,96,135,4,False
445,GarchompMega Garchomp,Dragon,Ground,108,170,115,120,95,92,4,False
448,LucarioMega Lucario,Fighting,Steel,70,145,88,140,70,112,4,False
460,AbomasnowMega Abomasnow,Grass,Ice,90,132,105,132,105,30,4,False
475,GalladeMega Gallade,Psychic,Fighting,68,165,95,65,115,110,4,False
531,AudinoMega Audino,Normal,Fairy,103,60,126,80,126,50,5,False
719,DiancieMega Diancie,Rock,Fairy,50,160,110,160,110,110,6,True
```

As you can see in the filtered.csv file, there are only names containing “Mega” - the condition you wrote using the str.contains() function.

Getting the reverse of this (not):

```python
import pandas as pd

df = pd.read_csv('pokemon_data.csv')

filtered = df.loc[~df["Name"].str.contains("Mega")]

filtered.to_csv("filtered.csv", index=False)
```

Content of filtered.csv:

```shell
#,Name,Type 1,Type 2,HP,Attack,Defense,Sp. Atk,Sp. Def,Speed,Generation,Legendary
1,Bulbasaur,Grass,Poison,45,49,49,65,65,45,1,False
2,Ivysaur,Grass,Poison,60,62,63,80,80,60,1,False
3,Venusaur,Grass,Poison,80,82,83,100,100,80,1,False
...
713,Avalugg,Ice,,95,117,184,44,46,28,6,False
714,Noibat,Flying,Dragon,40,30,35,45,40,55,6,False
715,Noivern,Flying,Dragon,85,70,80,97,80,123,6,False
716,Xerneas,Fairy,,126,131,95,131,98,99,6,True
717,Yveltal,Dark,Flying,126,131,95,131,98,99,6,True
718,Zygarde50% Forme,Dragon,Ground,108,100,121,81,95,95,6,True
719,Diancie,Rock,Fairy,50,100,150,100,150,50,6,True
720,HoopaHoopa Confined,Psychic,Ghost,80,110,60,150,130,70,6,True
720,HoopaHoopa Unbound,Psychic,Dark,80,160,60,170,130,80,6,True
721,Volcanion,Fire,Water,80,110,120,130,90,70,6,True
```

This only contains the names not containing “Mega”.

Regex expressions and more complex filtering:

```python
import re

print(df.loc[df['Type 1'].str.contains('Fire|Grass', regex=True)])
```

Match "fire" or "grass".

In the terminal:

```shell
#                   Name Type 1  ... Speed  Generation  Legendary
0      1              Bulbasaur  Grass  ...    45           1      False
1      2                Ivysaur  Grass  ...    60           1      False
2      3               Venusaur  Grass  ...    80           1      False
3      3  VenusaurMega Venusaur  Grass  ...    80           1      False
4      4             Charmander   Fire  ...    65           1      False
..   ...                    ...    ...  ...   ...         ...        ...
735  667                 Litleo   Fire  ...    72           6      False
736  668                 Pyroar   Fire  ...   106           6      False
740  672                 Skiddo  Grass  ...    52           6      False
741  673                 Gogoat  Grass  ...    68           6      False
799  721              Volcanion   Fire  ...    70           6       True
```

Flags - ignore case:

```python
import re

print(df.loc[df['Type 1'].str.contains('fire|grass', flags=re.I, regex=True)])
```

Just get data starting with ‘pi’:

```python
print(df.loc[df['Name'].str.contains('pi[a-z]', flags=re.I, regex=True)])
```

In the terminal:

```shell
#                     Name    Type 1  ... Speed  Generation  Legendary
13    10                 Caterpie       Bug  ...    45           1      False
20    16                   Pidgey    Normal  ...    56           1      False
21    17                Pidgeotto    Normal  ...    71           1      False
22    18                  Pidgeot    Normal  ...   101           1      False
23    18      PidgeotMega Pidgeot    Normal  ...   121           1      False
30    25                  Pikachu  Electric  ...    90           1      False
42    37                   Vulpix      Fire  ...    65           1      False
76    70               Weepinbell     Grass  ...    55           1      False
84    78                 Rapidash      Fire  ...   105           1      False
136  127                   Pinsir       Bug  ...    85           1      False
137  127        PinsirMega Pinsir       Bug  ...   105           1      False
181  167                 Spinarak       Bug  ...    30           2      False
186  172                    Pichu  Electric  ...    60           2      False
202  187                   Hoppip     Grass  ...    50           2      False
219  204                   Pineco       Bug  ...    15           2      False
239  221                Piloswine       Ice  ...    50           2      False
266  247                  Pupitar      Rock  ...    51           2      False
345  316                   Gulpin    Poison  ...    40           3      False
357  326                  Grumpig   Psychic  ...    80           3      False
358  327                   Spinda    Normal  ...    60           3      False
359  328                 Trapinch    Ground  ...    10           3      False
390  357                  Tropius     Grass  ...    51           3      False
438  393                   Piplup     Water  ...    40           4      False
463  416                Vespiquen       Bug  ...    40           4      False
488  440                  Happiny    Normal  ...    30           4      False
490  442                Spiritomb     Ghost  ...    35           4      False
502  452                  Drapion    Poison  ...    95           4      False
557  498                    Tepig      Fire  ...    45           5      False
558  499                  Pignite      Fire  ...    55           5      False
578  519                   Pidove    Normal  ...    43           5      False
596  536                Palpitoad     Water  ...    69           5      False
716  648  MeloettaPirouette Forme    Normal  ...   128           5      False
718  650                  Chespin     Grass  ...    38           6      False
```

# Conditional Changes

Change data frame based on conditions of filtering:

```python
df.loc[df['Type 1'] == "Fire", "Type 1"] = "Flamer"

print(df)
```

Now “Flamer” should be there instead of “Fire”:

In the terminal:

```shell
#                   Name   Type 1  ... Speed  Generation  Legendary
0      1              Bulbasaur    Grass  ...    45           1      False
1      2                Ivysaur    Grass  ...    60           1      False
2      3               Venusaur    Grass  ...    80           1      False
3      3  VenusaurMega Venusaur    Grass  ...    80           1      False
4      4             Charmander   Flamer  ...    65           1      False
..   ...                    ...      ...  ...   ...         ...        ...
795  719                Diancie     Rock  ...    50           6       True
796  719    DiancieMega Diancie     Rock  ...   110           6       True
797  720    HoopaHoopa Confined  Psychic  ...    70           6       True
798  720     HoopaHoopa Unbound  Psychic  ...    80           6       True
799  721              Volcanion   Flamer  ...    70           6       True
```

Change multiple params:

```python
df.loc[df["Total"] > 500, ["Generation", "Legendary"]] = "TEST VALUE"

print(df)
```

In the terminal:

```shell
#                   Name   Type 1  ... Sp. Atk  Generation   Legendary
0      1              Bulbasaur    Grass  ...      65         NaN         NaN
1      2                Ivysaur    Grass  ...      80         NaN         NaN
2      3               Venusaur    Grass  ...     100  TEST VALUE  TEST VALUE
3      3  VenusaurMega Venusaur    Grass  ...     122  TEST VALUE  TEST VALUE
4      4             Charmander     Fire  ...      60         NaN         NaN
..   ...                    ...      ...  ...     ...         ...         ...
795  719                Diancie     Rock  ...     100  TEST VALUE  TEST VALUE
796  719    DiancieMega Diancie     Rock  ...     160  TEST VALUE  TEST VALUE
797  720    HoopaHoopa Confined  Psychic  ...     150  TEST VALUE  TEST VALUE
798  720     HoopaHoopa Unbound  Psychic  ...     170  TEST VALUE  TEST VALUE
799  721              Volcanion     Fire  ...     130  TEST VALUE  TEST VALUE
```

Modify the values individually:

```python
df.loc[df["Total"] > 500, ["Generation", "Legendary"]] = ["Test 1", "Test 2"]
```

# Aggregate Statistics

Using the Groupby to aggregate statistics:

```python
df = pd.read_csv('modified.csv')

print(df.groupby(["Type 1"]).mean())
```

In the terminal:

```shell
#       Total         HP      Attack     Defense    Sp. Atk
Type 1                                                                        
Bug       334.492754  378.927536  56.884058   70.971014   70.724638  53.869565
Dark      461.354839  445.741935  66.806452   88.387097   70.225806  74.645161
Dragon    474.375000  550.531250  83.312500  112.125000   86.375000  96.843750
Electric  363.500000  443.409091  59.795455   69.090909   66.295455  90.022727
Fairy     449.529412  413.176471  74.117647   61.529412   65.705882  78.529412
Fighting  363.851852  416.444444  69.851852   96.777778   65.925926  53.111111
Fire      327.403846  458.076923  69.903846   84.769231   67.769231  88.980769
Flying    677.750000  485.000000  70.750000   78.750000   66.250000  94.250000
Ghost     486.500000  439.562500  64.437500   73.781250   81.187500  79.343750
Grass     344.871429  421.142857  67.271429   73.214286   70.800000  77.500000
Ground    356.281250  437.500000  73.781250   95.750000   84.843750  56.468750
Ice       423.541667  433.458333  72.000000   72.750000   71.416667  77.541667
Normal    319.173469  401.683673  77.275510   73.469388   59.846939  55.816327
Poison    251.785714  399.142857  67.250000   74.678571   68.821429  60.428571
Psychic   380.807018  475.947368  70.631579   71.456140   67.684211  98.403509
Rock      392.727273  453.750000  65.363636   92.863636  100.795455  63.340909
Steel     442.851852  487.703704  65.222222   92.703704  126.370370  67.518519
Water     303.089286  430.455357  72.062500   74.151786   72.946429  74.812500
```

Sorting by a specific column:

```python
df.groupby(["Type 1"]).mean().sort_values("Defense", ascending=True)
```

In the terminal:

```shell
#       Total         HP      Attack     Defense    Sp. Atk
Type 1                                                                        
Normal    319.173469  401.683673  77.275510   73.469388   59.846939  55.816327
Fairy     449.529412  413.176471  74.117647   61.529412   65.705882  78.529412
Fighting  363.851852  416.444444  69.851852   96.777778   65.925926  53.111111
Flying    677.750000  485.000000  70.750000   78.750000   66.250000  94.250000
Electric  363.500000  443.409091  59.795455   69.090909   66.295455  90.022727
Psychic   380.807018  475.947368  70.631579   71.456140   67.684211  98.403509
Fire      327.403846  458.076923  69.903846   84.769231   67.769231  88.980769
Poison    251.785714  399.142857  67.250000   74.678571   68.821429  60.428571
Dark      461.354839  445.741935  66.806452   88.387097   70.225806  74.645161
Bug       334.492754  378.927536  56.884058   70.971014   70.724638  53.869565
Grass     344.871429  421.142857  67.271429   73.214286   70.800000  77.500000
Ice       423.541667  433.458333  72.000000   72.750000   71.416667  77.541667
Water     303.089286  430.455357  72.062500   74.151786   72.946429  74.812500
Ghost     486.500000  439.562500  64.437500   73.781250   81.187500  79.343750
Ground    356.281250  437.500000  73.781250   95.750000   84.843750  56.468750
Dragon    474.375000  550.531250  83.312500  112.125000   86.375000  96.843750
Rock      392.727273  453.750000  65.363636   92.863636  100.795455  63.340909
Steel     442.851852  487.703704  65.222222   92.703704  126.370370  67.518519
```

You can also sum():

```python
df.groupby(["Type 1"]).sum()
```

In the terminal:

```shell
#  Total    HP  Attack  Defense  Sp. Atk
Type 1                                                
Bug       23080  26146  3925    4897     4880     3717
Dark      14302  13818  2071    2740     2177     2314
Dragon    15180  17617  2666    3588     2764     3099
Electric  15994  19510  2631    3040     2917     3961
Fairy      7642   7024  1260    1046     1117     1335
Fighting   9824  11244  1886    2613     1780     1434
Fire      17025  23820  3635    4408     3524     4627
Flying     2711   1940   283     315      265      377
Ghost     15568  14066  2062    2361     2598     2539
Grass     24141  29480  4709    5125     4956     5425
Ground    11401  14000  2361    3064     2715     1807
Ice       10165  10403  1728    1746     1714     1861
Normal    31279  39365  7573    7200     5865     5470
Poison     7050  11176  1883    2091     1927     1692
Psychic   21706  27129  4026    4073     3858     5609
Rock      17280  19965  2876    4086     4435     2787
Steel     11957  13168  1761    2503     3412     1823
Water     33946  48211  8071    8305     8170     8379
```

You can also count():

```python
df.groupby(["Type 1"]).count()
```

In the terminal:

```shell
#  Name  Type 2  Total   HP  Attack  Defense  Sp. Atk
Type 1                                                           
Bug        69    69      52     69   69      69       69       69
Dark       31    31      21     31   31      31       31       31
Dragon     32    32      21     32   32      32       32       32
Electric   44    44      17     44   44      44       44       44
Fairy      17    17       2     17   17      17       17       17
Fighting   27    27       7     27   27      27       27       27
Fire       52    52      24     52   52      52       52       52
Flying      4     4       2      4    4       4        4        4
Ghost      32    32      22     32   32      32       32       32
Grass      70    70      37     70   70      70       70       70
Ground     32    32      19     32   32      32       32       32
Ice        24    24      11     24   24      24       24       24
Normal     98    98      37     98   98      98       98       98
Poison     28    28      13     28   28      28       28       28
Psychic    57    57      19     57   57      57       57       57
Rock       44    44      35     44   44      44       44       44
Steel      27    27      22     27   27      27       27       27
Water     112   112      53    112  112     112      112      112
```

You can also group by a specific kind of “count”:

```python
df["count"] = 1

df.groupby(["Type 1"]).count()["count"]
```

In the terminal:

```shell
Type 1
Bug          69
Dark         31
Dragon       32
Electric     44
Fairy        17
Fighting     27
Fire         52
Flying        4
Ghost        32
Grass        70
Ground       32
Ice          24
Normal       98
Poison       28
Psychic      57
Rock         44
Steel        27
Water       112
```

Group by multiple params at the same time:

```python
df["count"] = 1

df.groupby(["Type 1", "Type 2"]).count()["count"]
```

In the terminal:

```shell
Type 1  Type 2  
Bug     Electric     2
        Fighting     2
        Fire         2
        Flying      14
        Ghost        1
                    ..
Water   Ice          3
        Poison       3
        Psychic      5
        Rock         4
        Steel        1
```

☝️ This is super useful for large data sets.

# Working with large amounts of data

Pandas is particularly useful for reading and working with large amounts of data.

Read in a file using pandas:

```python
for df in pd.read_csv("filename.csv", chunksize=5):
	print("CHUNK DF")
	print(df)
```

The chunksize param is used to tell the number of rows being loaded at a time. This is very useful in very large amounts of data, which might cause huge problems when it comes to memory if the file size is 20GB, for example.

Another useful thing to do is:

```python
new_df = pd.DataFrame(columns=df.columns)

for df in pd.read_csv("pokemon_data.csv", chunksize=5):
	results = df.groupby(["Type 1"]).count()

	new_df = pd.concat([new_df, results])

print(new_df)
```
