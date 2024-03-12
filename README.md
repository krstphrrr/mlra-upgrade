## MLRA update from v42 to v52


- v42: mlra_name(varchar 200), mlrarsym(varchar 4)
- v52: mlra_name(varchar 254), mlrarsym(varchar 5)


- alter table alter column failed due to column used by view for public_dev due the column being used by multiple schemas.

- testing select statement before before altering `sql SELECT atttypmod FROM pg_attribute WHERE attrelid = 'public_dev."geoIndicators"'::regclass   AND attname = 'mlrarsym';`

- executing the update statement `sql UPDATE pg_attribute SET atttypmod = 5+4 WHERE attrelid = 'public_dev."geoIndicators"'::regclass   AND attname = 'mlrarsym';`

- edit `public_test.postingest_populate_mlra_name` to add new dataset 
- execute
