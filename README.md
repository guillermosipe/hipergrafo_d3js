# D3JS: Hipergrafo

Representación de un hipergrafo a una de grafo simple.

Aplicaciones de terceros usadas:
* [D3.js](https://d3js.org/)
* [randomColors](https://github.com/davidmerfield/randomColor)

## Formas de representación
La librería permite representar el hipergrafo de 3 formas diferentes:

### Sin unión de hiperaristas a un nodo central sin repetición de nodos.
Archivo: hipergrafo_sin_centro

### Unión de hiperaristas a un nodo central con repetición de nodos.
Archivo: data/hipergrafo_con_centro_repeticion


### Unión de hiperaristas a un nodo central sin repetición de nodos.
Archivo: data/hipergrafo_con_centro_sin_repeticion

## Formato de archivo JSON
Para poder mapear el hipergrafo usando la libreria D3.js es necesario un archivo en formato JSON con las siguientes características:
```
{
  "hyperedges":["E1","E2","E3","E4",...],
  "links":[
		{"parent": "E1", "child": "v1"},
		{"parent": "E1", "child": "v2"},
		...
	],
  "nodes": {
  		"E1": {
  			"level": 2,
  			"word": "E1"
  		},
  		"E2": {
  			"level": 2,
  			"word": "E2"
  		}...
  	}
  }
```

En donde:
  * hyperedges: Es un listado de todas las hiperaristas.
  * links: Son las aristas o relaciones entre los nodos.
  * nodes: Son los nodos, se debe de declarar cada uno de ellos, existen 3 niveles:
  ⋅⋅* 1: para el nodo central que une todas las hiperaristas.
  ⋅⋅* 2: para las hiperaristas.
  ⋅⋅* 3: para los nodos.
  
Para hacer uso de la libreria es necesario declarar lo siguiente:
```
<body>
  <div id='id_div' style="max-width:750px;"></div>
</body>

<script type="text/javascript">

d3.json("Nombre_Archivo.json", function(error, data) {
    draw_graph(data,"#id_div");
  });

</script>
```
