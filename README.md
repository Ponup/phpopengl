[![Build Status](https://travis-ci.org/Ponup/php-opengl.svg?branch=master)](https://travis-ci.org/Ponup/php-opengl)

# PHP-OpenGL

PHP bindings of the OpenGL library. This library allows you to create inmersive 3D applications and games for the desktop with the comfort of the PHP language.

The extension only supports modern OpenGL and the core profile. The OpenGL compatibility profile (which provides functions such as glRotate, glBegin, glLight, etc...) is not supported.

[<img src="opengl-camera-demo.gif" width="250" />](opengl-camera-demo.gif)

## Requirements

- PHP7.3
- [SDL extension for PHP](https://github.com/Ponup/phpsdl)
- OpenGL library/framework
- Linux/MacOS (Windows support coming soon)
- The PHP GD extension is required to run some of the examples.

## Installation

### Linux

```bash
pecl install opengl-devel
```

Or

```bash
$ git clone git://github.com/phpopengl/extension.git --recursive phpopengl
$ cd phpopengl
$ phpize
$ ./configure --enable-opengl
$ make
$ sudo make install
```

## Examples

```php
<?php
SDL_Init(SDL_INIT_EVERYTHING);

$window = SDL_CreateWindow("Fixed pipeline example", SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED,                
                640, 480, SDL_WINDOW_OPENGL | SDL_WINDOW_SHOWN);                                                                                               
SDL_GL_CreateContext($window);    

glClearColor(0, 0, .2, 1); 
glClear(GL_COLOR_BUFFER_BIT);
SDL_GL_SwapWindow($window);

$event = new SDL_Event;
while(true) {
	SDL_PollEvent($event);
	if($event->type == SDL_KEYDOWN) break;
	SDL_Delay(50);
}

SDL_DestroyWindow($window);
```

Complete examples can be found in the [examples](examples) folder.

## License

GPL-3.0+

