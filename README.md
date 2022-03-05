# canvas animation random line in JavaScript
<img src="https://raw.githubusercontent.com/krishnawaghmode/canvas_demo/main/random_line.png" width="800">
```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>Particle JS</title>
	<style>
		*{
			margin: 0;
			padding: 0;
			box-sizing: border-box;
		}
		#canvas1{
			position: absolute;
			/*background: blue;*/
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
		}
		#title1{
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%,-50%);
			font-size: 120px;
			line-height: 110px;
			white-space: nowrap;
			border-top: 10px solid #000;
		}
		#title1:before{
			content: 'is awesome';
			position: absolute;
			bottom: -70px;
			font-size: 40px;
			text-align: center;
			width: 100%;
		}
	</style>
</head>
<body>
	<canvas id="canvas1"></canvas>
	<h1 id="title1">Life</h1>
	<script>
		const canvas = document.getElementById('canvas1'); 
		const ctx = canvas.getContext('2d');
		// console.log(ctx);
		canvas.width = window.innerWidth;
		canvas.height = window.innerHeight;

		let particlesArray = [];

		class Particle {
			constructor(x,y){
				this.x = x;
				this.y = y;
				this.size = 10;
				this.weight = 2;
				this.directionX = 1;
			}

			update(){
				if(this.y > canvas.height) {this.y = 0 -this.size;
				    this.weight =2; 
				    this.x = Math.random() * canvas.width;

				}
				this.weight +=0.05; 
				this.y +=this.weight; 
				// this.x +=this.directionX; 

			}
			draw(){
				ctx.fillStyle = 'red';
				ctx.beginPath();
				ctx.arc(this.x,this.y,this.size,0,Math.PI * 2);
				ctx.closePath();
				ctx.fill()
			}
		}

		const particle1 = new Particle(400, 900); 
		const particle2 = new Particle(100, 10); 

		function animate() {
			ctx.fillStyle = 'rgba(255,255,255,0.01)';
			ctx.fillRect(0,0,canvas.width,canvas.height);
			particle1.update();
			particle1.draw();
			particle2.update();
			particle2.draw();
			requestAnimationFrame(animate);

		}
		animate();
	</script>
</body>
</html>
```
