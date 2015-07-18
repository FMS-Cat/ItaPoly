# ItaPoly

GLSL fragment shading on rectangle library
useful for experient of fractal, filter, raymarch, etc...

### Usage

```HTML
<!DOCTYPE html>

<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<style>
		</style>
	</head>
	<body>
    <script id="frag" type="x-shader/x-fragment">
      // Your fragment shader here

      #ifdef GL_ES
      precision mediump float;
      #endif

      uniform float time;
      uniform vec2 resolution;

      void main()
      {
        vec2 uv = gl_FragCoord.xy / resolution;
        gl_FragColor = vec4( uv, 0.5 + 0.5*sin( time ), 1.0 );
      }
    </script>
    <script src="ItaPoly.js"></script>
		<script>
      var width = 240;
      var height = 240;
      var itapoly = new ItaPoly( width, height ); // create ItaPoly object
      document.body.appendChild( itapoly.canvas ); // put canvas into document
      itapoly.createProgram( document.getElementById( 'frag' ).innerHTML, function(){ // compile fragment shader then callback
          function update(){
            itapoly.update(); // draw once
            requestAnimationFrame( update ); // request next frame
          }
          update();
      } );

		</script>
	</body>
</html>
```

### Methods

- `ItaPoly( width (number), height (number) )`
	create ItaPoly Object wow

- `ItaPoly.createProgram( frag (string), callback (function) )`
	create the program wow

- `ItaPoly.update()`
	draw once wow

- `ItaPoly.setFloat( name (string), param (number) )`
- `ItaPoly.setVec2( name (string), param ([ number, number ]) )`
- `ItaPoly.setVec3( name (string), param ([ number, number, number ]) )`
- `ItaPoly.setVec4( name (string), param ([ number, number, number, number ]) )`
- `ItaPoly.setInt( name (string), param (number) )`
- `ItaPoly.setSampler2D( name (string), texture (image or canvas or video) )`
- `ItaPoly.setSampler2DFromArray( name (string), array ([ number, number, number, number, ... ]), width (number), height (number) )`
	set uniform variables wow

### Events

- `ItaPoly.onMouseDown( mouseEvent )`
- `ItaPoly.onMouseMove( mouseEvent )`
- `ItaPoly.onMouseUp( mouseEvent )`
	events wow
