# notes

## oracle/shp import
```bash
ogr2ogr -f "OCI" OCI:MEDIUM/password@localhost:1521/orcldev.tugce.com -geomfield GEOM -lco DIM=2 -lco SRID=5256 -lco GEOMETRY_NAME=GEOM -lco PRECISION=NO -nln MAHALLE5256  C:\Users\tugcetay\Desktop\data\mahalle\mahalle5256.shp 
```

## postgre to oracle
```bash
ogr2ogr -f "OCI" OCI:DENEME/password@localhost:1521/orcldev.tugce.com -geomfield GEOM -lco DIM=2 -lco SRID=5256 -lco GEOMETRY_NAME=GEOM -lco PRECISION=NO -nln MAHALLE5256-nlt MULTIPOLYGON -t_srs "EPSG:5256" PG:"host=localhost user=postgres dbname=sample_data password=****" mahalle5256
```
##  oracle to postgre 
```bash
ogr2ogr -f "PostgreSQL" PG:"host=localhost user=postgres dbname=sample_data password= 'password' " -lco DIM=2 -lco SRID=5256 -t_srs "EPSG:5256" -lco GEOMETRY_NAME=geom -lco PRECISION=NO -nln mahalle -nlt MULTIPOLYGON "OCI:MEDIUM/'user_password'@localhost:1521/service_name " MAHALLE5256 -geomfield GEOM
```

## postgre shp import(ogr2ogr)
```bash
ogr2ogr -f "PostgreSQL" PG:"dbname=tucbs user=postgres password=**** host=localhost port=5432" C:\Users\tugcetay\Desktop\data\mahalle\mahalle5256.shp  -nln mahalle2 -lco GEOMETRY_NAME=geom -overwrite -progress
```

## postgre shp import(shp2pgsql)
```bash
 shp2pgsql -I -s 4326 -g geom C:\Users\tugcetay\Desktop\data\mahalle\mahalle5256.shp  public.mahalle3 | psql -h localhost -d tucbs -U postgres -
```
## postgre raster import
```bash
 C:\Users\tugcetay\Desktop\AYP1_son\GEO474_vize\uygulama\data\sym.tif -F | psql -d  DbFatih  -h localhost -U postgres -p 5432 -w 
```
