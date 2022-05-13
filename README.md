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
echo $ID

## Inicializar contrato:
```rust
	near call $ID init_contract '{"owner_id":"'$ID'"}' --accountId $ID
```

## Obtener producto
```rust
    near view $ID get_products '{"address":"0x1"}'
    near view $ID get_products '{"address":"0x2"}'
    near view $ID get_products '{"address":"0x3"}'
```

## Guardar producto

```rust
    near call $ID set_products '{"address":"0x1", "name":"zapatos", "price": 250, "stock":5, "cid": ""}' --accountId yairnava.testnet
    near call $ID set_products '{"address":"0x2", "name":"botas", "price": 450, "stock":10, "cid": ""}' --accountId yairnava.testnet
    near call $ID set_products '{"address":"0x3", "name":"tenis", "price": 300, "stock":7, "cid": ""}' --accountId yairnava.testnet
```

## Eliminar producto

```rust
    near call $ID delete_products '{"address":"0x3"}' --accountId yairnava.testnet
```


## USO DEL NODO thegraph:




## USO DEL migrate



