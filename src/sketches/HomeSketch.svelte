<script lang="ts">
    import P5 from 'p5-svelte';
    import type p5 from 'p5';

    const sketch = (p5: p5) => {
        let screenWidth: number;
        let screenHeight: number;
        let cityPointData: string[];
        let cityPoints: number[] = [];
        let time: number;
        let colours = [
            p5.color(255, 0, 0),
            p5.color(255, 0, 255),
            p5.color(255, 0, 204),
            p5.color(255, 153, 51),
        ];

        p5.preload = () => {
            cityPointData = p5.loadStrings('/assets/data/cityHeights.txt');
        };

        p5.setup = () => {
            screenWidth = window.innerWidth;
            screenHeight = window.innerHeight;
            let canvas = p5.createCanvas(screenWidth, screenHeight);
            canvas.position(0, 0);
            canvas.style('z-index: -1');

            for (let index in cityPointData) {
                cityPoints.push(parseFloat(cityPointData[index]));
            }

            time = p5.floor(p5.random(0, cityPoints.length));
        };

        p5.draw = () => {
            p5.background(0);

            let yOff = 300;
            for (var column = 0; column < screenWidth; column++) {
                let colourOffset =
                    p5.abs((((column / 2 + time) % screenWidth) * 4) / 2 - screenWidth) /
                    screenWidth;
                p5.stroke(255);
                p5.strokeWeight(12);
                gradientLine(
                    column,
                    0,
                    column,
                    screenHeight,
                    p5.lerpColor(colours[0], colours[1], colourOffset),
                    p5.lerpColor(colours[3], colours[2], colourOffset)
                );
            }

            for (var column = 0; column < screenWidth; column++) {
                p5.noStroke();
                p5.fill(0);
                p5.beginShape();
                p5.vertex(column, cityPoints[(column + time) % cityPoints.length] + yOff);
                p5.vertex(column + 1, cityPoints[(column + 1 + time) % cityPoints.length] + yOff);
                p5.vertex(column + 1, screenHeight);
                p5.vertex(column, screenHeight);
                p5.endShape(p5.CLOSE);
            }

            time += 1;
        };

        function gradientLine(
            x1: number,
            y1: number,
            x2: number,
            y2: number,
            color1: p5.Color,
            color2: p5.Color
        ) {
            // linear gradient from start to end of line
            var grad = p5.drawingContext.createLinearGradient(x1, y1, x2, y2);
            grad.addColorStop(0, color1);
            grad.addColorStop(1, color2);
            p5.drawingContext.strokeStyle = grad;
            p5.line(x1, y1, x2, y2);
            p5.drawingContext.strokeStyle = p5.color(0, 0, 0);
        }

        p5.windowResized = () => {
            screenWidth = window.innerWidth;
            screenHeight = window.innerHeight;
            p5.resizeCanvas(screenWidth, screenHeight);
        };
    };
</script>

<P5 {sketch} />
