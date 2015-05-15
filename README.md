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
