#### Este script va a la carpeta de deploys del namespace compartidoms de coquena1, 
#### lee el nombre de cada archivo, corta la extensión .json, y con ese nombre obtenido
#### genera un listado. Este listado es recorrido por el comando de kubectl para ir a buscar
### la info del  deployment desde el cluster coquena3

```
av_depl=$(find /home/idm/$USER/av_res_proj/coquena1/available_resources/compartidoms/deploy -type f -name '*.json' -exec basename {} \; | sed 's/.json$//');for depl in $av_depl;do kubectl get deploy "$depl" -n compartidoms | awk 'NR>1' | awk -v OFS=';' '{print $1, $2, $3, $4, $5}';done
```
