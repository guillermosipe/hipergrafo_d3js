# D3JS: Hipergrafo

Representación de un hipergrafo en un grafo simple.

Aplicaciones de terceros usadas:
* [D3.js](https://d3js.org/)
* [randomColors](https://github.com/davidmerfield/randomColor)

## Formas de representación

![alt text](https://upload.wikimedia.org/wikipedia/commons/5/57/Hypergraph-wikipedia.svg)

La librería permite representar el hipergrafo de 3 formas diferentes. a través de un archivo JSON:

### Sin unión de hiperaristas a un nodo central sin repetición de nodos.
Archivo: data/hipergrafo_sin_centro.json

![alt text](https://github.com/guillermosipe/hipergrafo_d3js/blob/master/screenshots/h1.png)

### Unión de hiperaristas a un nodo central con repetición de nodos.
Archivo: data/hipergrafo_con_centro_repeticion.json

![alt text](https://github.com/guillermosipe/hipergrafo_d3js/blob/master/screenshots/h3.png)

### Unión de hiperaristas a un nodo central sin repetición de nodos.
Archivo: data/hipergrafo_con_centro_sin_repeticion.json

![alt text](https://github.com/guillermosipe/hipergrafo_d3js/blob/master/screenshots/h2.png)

## Interacción

Se puede posicionar sobre un nodo y mostrara a que hiperaristas pertenece.

![alt text](https://github.com/guillermosipe/hipergrafo_d3js/blob/master/screenshots/h1_2.png)

De igual manera se puede posicionar en una hiperarista y ver que nodos la conforman.

![alt text](https://github.com/guillermosipe/hipergrafo_d3js/blob/master/screenshots/h1_1.png)

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
  	* 1: para el nodo central que une todas las hiperaristas.
  	* 2: para las hiperaristas.
  	* 3: para los nodos.
  
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
