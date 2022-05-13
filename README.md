# NEAR Certified Architect (Demo day by noemk2)


## objetivos del NCA (NEAR Certified Architect )
Este curso es una oportunidad para que los desarrolladores dentro del ecosistema de NEAR obtengan un certificado al aplicar herramientas para escalar y mantener aplicaciones descentralizadas lanzadas en la red mainnet.

## Actividades propuestas para NCA
- Día 1: Interacción con contratos inteligentes
- Día 2: Herramientas de escalamiento para aplicaciones descentralizadas.
- Día 3: Herramientas para el mantenimiento de aplicaciones descentralizadas
- Día 4: Pautas para el despliegue en mainnet
- Día 5: DEMO DAY


## 👨‍💻  Actividades realizadas por noemk2:

## Contratos utilizado en este demo (testnet):
- calc.noemk3.testnet (contrato para el cross-contract-callback)
- productos.mue.testnet (contrato principal (lib.rs): simple crud para agregar y eliminar productos )

## uso de IPFS
- obtenear un hash unico de un contenido digital de un Servidor IPFS (app.pinata.cloud)
- el hash unico implementado como CID (String) en el contrato (lib.rs) desplegado en productos.mue.testnet

## uso del nodo de thegraph en near testnet
- https://thegraph.com/hosted-service/subgraph/noemk2/simi (nodo live en thegraph)
- ./Simi/src/mapping.ts (implementacion del subgraph) 


## uso de migrate (mantenimiento del contrato)
- Creacion de una DAO en sputnikdao (nombre de la DAO: nienie.sputnikv2.testnet)
- implementacion de metodo upgrade (lib.rs) para modificar el contrato por medio de la DAO


# USO DEL CONTRATO productos.mue.testnet:

ID= productos.mue.testnet
<br>


## Inicializar contrato:
```sh
    near call productos.mue.testnet new '{"owner_id": "mue.testnet"}' --accountId $YOUR_ACCOUNT.testnet
```

## Obtener producto
```sh
    near view productos.mue.testnet get_products '{"address":"noemk3.testnet"}'
    near view productos.mue.testnet get_products '{"address":"nie.testnet"}'
    near view productos.mue.testnet  get_products '{"address":"mue.testnet"}'
```

## Guardar producto

```sh
  near call productos.mue.testnet set_products '{"address": "noemk3.testnet", "name": "phone 5", "price": 520, "stock": 50,"cid": "QmUWe3CW6NoFimZ34xWCKdzrveCD5zqExTAUeFzJ6nbDYp" }' --accountId mue.testnet


near call productos.mue.testnet set_products '{"address": "mue.testnet", "name": "phone 1", "price": 10, "stock": 10,"cid": "Qmb7VQPf7KFnXSQed5LWWQoCzmqvsQQoaEjd98wGweppvE" }' --accountId mue.testnet


near call productos.mue.testnet set_products '{"address": "nie.testnet", "name": "phone 4", "price": 40, "stock": 40,"cid": "Qmb7VQPf7KFnXSQed5LWWQoCzmqvsQQoaEjd98wGweppvE" }' --accountId mue.testnet

```

## Eliminar producto

```sh
near call productos.mue.testnet delete_products '{"address": "noemk3.testnet"}' --accountId mue.testnet
```

## Uso del Callback (bajo nivel)

```sh

near call productos.mue.testnet sum_a_b '{"a": 12, "b": 12}' --accountId mue.testnet

```


## USO DEL NODO thegraph:

![Screenshot 2022-05-13 at 12-19-59 Simi Subgraph](https://user-images.githubusercontent.com/37389982/168335902-3319c71d-90cb-4b23-9e57-bd54caa40253.png)



## USO DEL migrate

### requisitos:
- contrato ya desplegado 
- creacion de una DAO en https://testnet-v2.sputnik.fund/#/ 
- instalar sputnikdao https://www.npmjs.com/package/sputnikdao


### ir al merge migrated

```sh
	git checkout migrated 
```
### build contract
```sh
    sh build.sh
```
### create proposal para la dao (upgrade)
$ID no debe ser owner_id del contrato

```sh
	sputnikdao proposal upgrade res/products.wasm productos.mue.testnet --daoAcc nienie --accountId $ID.testnet
```

![Screenshot 2022-05-13 at 12-25-15 SputnikDAO 2](https://user-images.githubusercontent.com/37389982/168336233-4ba0f85d-8491-4980-ac1f-c92bec0dff97.png)


