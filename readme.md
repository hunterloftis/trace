# A Physically-Based Renderer in Go

Learning Go by writing a path tracer.
[[ API Docs ]](https://hunterloftis.github.io/pbr/docs/pbr.html)

![Render](https://user-images.githubusercontent.com/364501/27873088-e36c621c-6178-11e7-94c8-19171e05dc50.png)

- Unbiased Monte-Carlo integration
- Adaptive sampling
- Russian roulette (early path termination)
- Parametric shapes (spheres, cubes)
- Physically-based materials
  - Fresnel reflection, transmission, absorption, diffusion
  - Color, refractive indices, gloss, transparency, separate fresnel channels, metals
- Arbitrary light sources ('everything is a light')
- Environment maps
- Physically-based cameras
  - Sensor, aperture, focus, depth-of-field
- Anti-aliasing

## Quick start

```
$ go get -u github.com/hunterloftis/pbr/pbr
$ cd $GOPATH/src/github.com/hunterloftis/pbr
$ ./run
```

By default, the renderer runs until it receives a signal (like Ctrl + C)

## Scene bins

Scenes (like the example `cmd/cubes.go` scene) are built into binaries:

```
$ go build -o bin/cubes ./cmd/cubes.go
$ bin/cubes -help
Usage of bin/cubes:
  -adapt int
    	Adaptive sampling; 0=off, 3=medium, 5=high (default 4)
  -bounces int
    	Maximum light bounces (default 10)
  -heat string
    	Heatmap png filename
  -out string
    	Output png filename (default "render.png")
  -profile
    	Record performance into profile.pprof
  -samples float
    	Max samples per pixel (default +Inf)
  -workers int
    	Concurrency level (default 4)
```

## Testing

```
$ go test ./pbr
```