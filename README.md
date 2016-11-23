proctree.js
===========

Procedural tree creation library

### Usage ###

Mesh creation, [BabylonJS](http://babylonjs.com/) example:
```html
<script>
	var myTree = new Tree({
		"seed": 262,
		"segments": 6,
		"levels": 5,
		"vMultiplier": 2.36,
		"twigScale": 0.39,
		"initalBranchLength": 0.49,
		"lengthFalloffFactor": 0.85,
		"lengthFalloffPower": 0.99,
		"clumpMax": 0.454,
		"clumpMin": 0.404,
		"branchFactor": 2.45,
		"dropAmount": -0.1,
		"growAmount": 0.235,
		"sweepAmount": 0.01,
		"maxRadius": 0.139,
		"climbRate": 0.371,
		"trunkKink": 0.093,
		"treeSteps": 5,
		"taperRate": 0.947,
		"radiusFalloffRate": 0.73,
		"twistRate": 3.02,
		"trunkLength": 2.4
	});

	var treeMesh = new BABYLON.Mesh("tree", scene);
	treeMesh.setVerticesData(BABYLON.VertexBuffer.PositionKind, Tree.flattenArray(myTree.verts));
	treeMesh.setVerticesData(BABYLON.VertexBuffer.NormalKind, Tree.flattenArray(myTree.normals));
	treeMesh.setVerticesData(BABYLON.VertexBuffer.UVKind, Tree.flattenArray(myTree.UV));
	treeMesh.setIndices(Tree.flattenArray(myTree.faces).reverse());

	var twigMesh = [];
	for (var i = 0; i < myTree.vertsTwig.length; i++) {
		twigMesh[i] = new BABYLON.Mesh("leaves", scene);
		twigMesh[i].setVerticesData(BABYLON.VertexBuffer.PositionKind, Tree.flattenArray(myTree.vertsTwig[i]));
		twigMesh[i].setVerticesData(BABYLON.VertexBuffer.NormalKind, Tree.flattenArray(myTree.normalsTwig[i]));
		twigMesh[i].setVerticesData(BABYLON.VertexBuffer.UVKind, Tree.flattenArray(myTree.uvsTwig[i]));
		twigMesh[i].setIndices(Tree.flattenArray(myTree.facesTwig[i]).reverse());
	}
</script>
```