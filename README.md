# FirstBabylonApp
Just trying the cool babylon.js Playground 6.4.1
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

        <title>Babylon.js sample code</title>

        <!-- Babylon.js -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/dat-gui/0.6.2/dat.gui.min.js"></script>
        <script src="https://assets.babylonjs.com/generated/Assets.js"></script>
        <script src="https://cdn.babylonjs.com/ammo.js"></script>
        <script src="https://cdn.babylonjs.com/havok/HavokPhysics_umd.js"></script>
        <script src="https://cdn.babylonjs.com/cannon.js"></script>
        <script src="https://cdn.babylonjs.com/Oimo.js"></script>
        <script src="https://cdn.babylonjs.com/earcut.min.js"></script>
        <script src="https://cdn.babylonjs.com/babylon.js"></script>
        <script src="https://cdn.babylonjs.com/materialsLibrary/babylonjs.materials.min.js"></script>
        <script src="https://cdn.babylonjs.com/proceduralTexturesLibrary/babylonjs.proceduralTextures.min.js"></script>
        <script src="https://cdn.babylonjs.com/postProcessesLibrary/babylonjs.postProcess.min.js"></script>
        <script src="https://cdn.babylonjs.com/loaders/babylonjs.loaders.js"></script>
        <script src="https://cdn.babylonjs.com/serializers/babylonjs.serializers.min.js"></script>
        <script src="https://cdn.babylonjs.com/gui/babylon.gui.min.js"></script>
        <script src="https://cdn.babylonjs.com/inspector/babylon.inspector.bundle.js"></script>

        <style>
            html, body {
                overflow: hidden;
                width: 100%;
                height: 100%;
                margin: 0;
                padding: 0;
            }

            #renderCanvas {
                width: 100%;
                height: 100%;
                touch-action: none;
            }
            
            #canvasZone {
                width: 100%;
                height: 100%;
            }
        </style>
    </head>
<body>
    <div id="canvasZone"><canvas id="renderCanvas"></canvas></div>
    <script>
        var canvas = document.getElementById("renderCanvas");

        var startRenderLoop = function (engine, canvas) {
            engine.runRenderLoop(function () {
                if (sceneToRender && sceneToRender.activeCamera) {
                    sceneToRender.render();
                }
            });
        }

        var engine = null;
        var scene = null;
        var sceneToRender = null;
        var createDefaultEngine = function() { return new BABYLON.Engine(canvas, true, { preserveDrawingBuffer: true, stencil: true,  disableWebGL2Support: false}); };
        var createScene = function () {
    // This creates a basic Babylon Scene object (non-mesh)
    var scene = new BABYLON.Scene(engine);

    // This creates and positions a free camera (non-mesh)
    var camera = new BABYLON.FreeCamera("camera1", new BABYLON.Vector3(5, 5, 20), scene);

    // This targets the camera to scene origin
    camera.setTarget(BABYLON.Vector3.Zero());

    // This attaches the camera to the canvas
    camera.attachControl(canvas, true);

    // This creates a light, aiming 0,1,0 - to the sky (non-mesh)
    var light = new BABYLON.HemisphericLight("light", new BABYLON.Vector3(0, 2, 0), scene);

    // Default intensity is 1. Let's dim the light a small amount
    light.intensity = 0.9;

    // Our built-in 'sphere' shape.
    var sphere = BABYLON.MeshBuilder.CreateSphere("sphere", {diameter: 2, segments: 32}, scene);
var sphere1 = BABYLON.MeshBuilder.CreateSphere("sphere1", {diameter: 2, segments: 32},scene);
var sphere2 = BABYLON.MeshBuilder.CreateSphere("sphere2", {diameter: 2, segments: 32},scene);
var cylinder = BABYLON.MeshBuilder.CreateCylinder("cylinder1",{diameter: 0.1,height: 12},scene);
var box = BABYLON.MeshBuilder.CreateBox("box", {height: 0.2, width:  5, depth: 3},scene);
var box1 = BABYLON.MeshBuilder.CreateBox("box1",{height:0.2, width:5,depth: 3 },scene);
    // var disc1 = BABYLON.MeshBuilder.CreateDisc("disc1", {radius:1.5, sideOrientation: 3, segments: 32},scene);
    // var disc2 = BABYLON.MeshBuilder.CreateDisc("disc2", {radius: 2.5,sideOrientation: 2,segments: 32},scene);
let sphereMaterial= new BABYLON.StandardMaterial("Sphere Materials",scene);

sphere.material = sphereMaterial;
sphere1.material = sphereMaterial;
sphere2.material = sphereMaterial;
sphere1.material.diffuseColor = BABYLON.Color3.Red();
let cylinderMaterial = new BABYLON.StandardMaterial("Cylinder Materials", scene);
cylinder.material = cylinderMaterial;
cylinder.material.diffuseColor = BABYLON.Color3.Black();
    // Move the sphere upward 1/2 its height
let boxMaterial = new BABYLON.StandardMaterial("Box Materials",scene);
box.material = boxMaterial;
box1.material = boxMaterial;

box.material.diffuseColor = BABYLON.Color3.White();
box1.material.diffuseColor = BABYLON.Color3.White();
box1.position.y = 7.5;
    box.position.y = 4.5;
    cylinder.position.y = 6;
    sphere.position.y = 3;
    sphere1.position.y = 6;
    sphere2.position.y = 9;
    // disc1.position.y = 3;
    // disc2.position.y=3;
    // disc2.position.z=1.01;
    // // Our built-in 'ground' shape.
    // let discMaterial = new BABYLON.StandardMaterial("Disc Material",scene);
    // let discMaterial1= new BABYLON.StandardMaterial("Disc Material",scene);
    // disc1.material = discMaterial;
    // disc1.material.diffuseColor = BABYLON.Color3.Red();
    // disc2.material = discMaterial1;
    // disc2.material.diffuseColor = BABYLON.Color3.Blue();




    var ground = BABYLON.MeshBuilder.CreateGround("ground", {width: 6, height: 6}, scene);




    return scene;
};
                window.initFunction = async function() {
                    
                    
                    
                    var asyncEngineCreation = async function() {
                        try {
                        return createDefaultEngine();
                        } catch(e) {
                        console.log("the available createEngine function failed. Creating the default engine instead");
                        return createDefaultEngine();
                        }
                    }

                    window.engine = await asyncEngineCreation();
        if (!engine) throw 'engine should not be null.';
        startRenderLoop(engine, canvas);
        window.scene = createScene();};
        initFunction().then(() => {sceneToRender = scene                    
        });

        // Resize
        window.addEventListener("resize", function () {
            engine.resize();
        });
    </script>
</body>
</html>
