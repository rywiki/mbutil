# MBUtil

MBUtil 用于导入导出 [MBTiles](http://mbtiles.org/) 格式的工具，通常用来创建
[Mapbox](http://mapbox.com/) [TileMill](http://mapbox.com/tilemill/)瓦片.
***（后面我只翻译重要的内容）***

Before exporting tiles to disk, see if there's a [Mapbox Hosting plan](http://mapbox.com/plans/)
or an open source [MBTiles server implementation](https://github.com/mapbox/mbtiles-spec/wiki/Implementations)
that works for you - tiles on disk are notoriously difficult to manage.

[![Build Status](https://secure.travis-ci.org/mapbox/mbutil.png)](http://travis-ci.org/mapbox/mbutil)

**Note well**: this project is no longer actively developed. Issues and pull requests will be attended to when possible, but delays should be expected.
这个项目将不再进行积极的开发，问题和推送仍然会适当的时候进行，但肯定不会及时。

## Installation

Git checkout (requires git)

    git clone git://github.com/mapbox/mbutil.git
    cd mbutil
    # get usage
    ./mb-util -h

Then to install the mb-util command globally:

    sudo python setup.py install
    # then you can run:
    mb-util

Python installation (requires easy_install)

    easy_install mbutil
    mb-util -h

## Usage

    $ mb-util -h
    Usage: mb-util [options] input output

    Examples:

        Export an mbtiles file to a directory of files:
        导出mbtiles文件到文件目录
        $ mb-util world.mbtiles tiles # tiles must not already exist

        Import a directory of tiles into an mbtiles file:
        导入瓦片目录到指定的mbtiles文件
        $ mb-util tiles world.mbtiles # mbtiles file must not already exist

    Options:
      -h, --help            Show this help message and exit
      --scheme=SCHEME       Tiling scheme of the tiles. Default is "xyz" (z/x/y),
                            other options are "tms" which is also z/x/y
                            but uses a flipped y coordinate, and "wms" which replicates
                            the MapServer WMS TileCache directory structure "z/000/000/x/000/000/y.png"''',
                            and "zyx" which is the format vips dzsave --layout google uses.
                            瓦片规则。默认是“xyz”（即存放目录是z/x/y）.
                            其他的选项包括“tms”，虽然它也是z/x/y存放，但y坐标是反转的,"wms"也是如此
                            MapServer的WMS 瓦片缓存目录结构是"z/000/000/x/000/000/y.png"'''而“zyx”则是Google所使用的格式
      --image_format=FORMAT
                            The format of the image tiles, either png, jpg, webp,pbf or terrain(cesium TIN)
                            瓦片图像的格式，可以是png，jpg，webp，pbf和terrain中的任意一种（其中terrain是cesium的一种地形瓦片）
      --grid_callback=CALLBACK
                            Option to control JSONP callback for UTFGrid tiles. If
                            grids are not used as JSONP, you can
                            remove callbacks specifying --grid_callback=""
      --do_compression      Do mbtiles compression
                            启用mbtiles压缩
      --silent              Dictate whether the operations should run silently
                            决定操作是否要静默运行


    Export an `mbtiles` file to files on the filesystem:

        mb-util World_Light.mbtiles adirectory


    Import a directory into a `mbtiles` file

        mb-util directory World_Light.mbtiles

## Requirements

* Python `>= 2.6`

## Metadata

MBUtil imports and exports metadata as JSON, in the root of the tile directory, as a file named `metadata.json`.
MBUtil 导入和导出元数据是一个JSON文件，这个文件位于根目录，名称是"metadata.json"

```javascript
{
    "name": "World Light",
    "description": "A Test Metadata",
    "version": "3"
}
```

## Testing

This project uses [nosetests](http://readthedocs.org/docs/nose/en/latest/) for testing. Install nosetests:

    pip install nose
or

    easy_install nose
    
Then run:

    nosetests

## See Also

* [node-mbtiles provides mbpipe](https://github.com/mapbox/node-mbtiles/wiki/Post-processing-MBTiles-with-MBPipe), a useful utility.
* [mbliberator](https://github.com/calvinmetcalf/mbliberator) a similar program but in node.

## License

BSD - see LICENSE.md

## Authors

- Tom MacWright (tmcw)
- Dane Springmeyer (springmeyer)
- Mathieu Leplatre (leplatrem)
