# SED
### replace characters
#### the ```\``` symbol is an way you can break up command for readability
```bash
head -25 points_of_interest.csv | \
cut -d',' -f1,2 | \
```

#### s = substitute, / = seds delimiter, ',' = what were replacing, '--->>' = what were putting in place
```bash
sed 's/,/--->>/g'
```

#### replace larger peices of text Woods > Preserve
```bash
head -25 points_of_interest.csv | \
cut -d',' -f1,2 | \
sed 's/Woods/Preserve/g'
```

### sed works with regular expressions (regex)

#### delete empty lines
```bash
sed '/^$/d'
```

### Insert a line before another line matching your pattern
```bash
sed '/<pattern to match>/i'
sed '/<pattern to match>/a'
```

### Date give you todays date
```bash
date
date +%D
date +%Y-%m-%d' : '%A
```

### Join will join to files based on the first column
```bash
wget https://raw.githubusercontent.com/fpdcc/webmap_data_updates/master/map%20data/trails.csv

wget https://raw.githubusercontent.com/fpdcc/webmap_data_updates/master/map%20data/trails_desc.csv
```
```bash
head -10 trails.csv | cut -d',' -f3,4 | sort > trails_subsest.csv

head -10 trails_desc.csv | cut -d',' -f2 | sort > trails_desc_subset.csv
```
```bash
join trails_subsest.csv trails_desc_subset.csv
```

## A few extras


## Time

* Prepend time command to anything and it will tell you how long it took to execute

## Parallel 

* Is a tool to improve performance by multithreading. Works well with gdal.
```bash
sudo apt-get install parallel
time ls *.tif | parallel gdal2tiles.py --profile=mercator --zoom=11-15 --title=NZTopo50 {}
```

Next up...
jq

tmux
