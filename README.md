# Geohasher
A python library for geohash encoding, decoding and finding neighbour cells. This is a python port of [Chris Veness' javascript implementation](https://www.movable-type.co.uk/scripts/geohash.html).

[Wikipedia reference](http://en.wikipedia.org/wiki/Geohash)
## Installation
```pipenv install geohasher```
or
```pip install geohasher```
## Usage

    from geohasher import geohash
   ### Encode a latitude, longtiude to geohash
    geohash.encode(latitude, longitude, precision)
    >> geohash.encode('70.2995', '-27.9993', 7)
    >> gkkpfve
    
   ### Decode a geohash to latitude, longitude
    geohash.decode(geohash)
    >> geohash.decode('gkkpfve')
    >> (70.2995, -27.9993)
    
   ### Find neighbouring cells of a geohash
    geohash.neighbours(geohash) 
    retuns a namedtuple (n, ne, e, se, s, sw, w, nw)    
    
    >> neighbours = geohash.neighbours('gcpuyph')
    >> neighbours
    >> ('gcpvn11', 'gcpvn14', 'gcpvn0f', 'gcpvn08', 'gcpvn09', 'gcpvn0d', 'gcpvn0b', 'gcpvn10')
    >> neighbours.ne
    >> gcpvn14
    
   ### Find adjacent cell in a given direction
    geohash.adjacent(geohash, direction)
    >> geohash.adjacent('gcpuyph', 'ne')
    >> gcpvn14
    
   ### Find SW/NE latitude/longitude bounds of a geohash
    geohash.bounds(geohash)
    returns a namedtuple ((sw_lat, sw_lon), ((ne_lat, ne_lon))
    >> bounds = geohash.bounds('ezs42')
    >> bounds
    >> ((42.583, -5.625), (42.627, -5.58)))
    >> bounds.sw.lat 
    >> 42.583
