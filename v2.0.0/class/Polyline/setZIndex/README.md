# polyline.setZIndex()

Change the polyline zIndex order.

```html
<div id="map_canvas">
  <span class="smallPanel"><button>Reverse the zIndex orders</button></span>
</div>
```

```js
var path1 = [
  {"lat":32.682542,"lng":6.965338},{"lat":-18.715622,"lng":-16.940925},
  {"lat":-20.810888,"lng":12.121579},{"lat":-38.69694,"lng":-2.995607}
];
var path2 = [
  {"lat":20.124723,"lng":-47.878427},{"lat":-36.090536,"lng":-35.456546},
  {"lat":-23.631102,"lng":22.785649},{"lat":14.760725,"lng":33.684091},
  {"lat":-10.790138,"lng":-22.448735}
];
var path3 = [
  {"lat":24.460485,"lng":2.160642},{"lat":14.19339,"lng":-27.956545},
  {"lat":-37.311922,"lng":24.074706}
];

var mapDiv = document.getElementById("map_canvas");

// Create a map with specified camera bounds
var map = plugin.google.maps.Map.getMap(mapDiv);
map.addEventListener(plugin.google.maps.event.MAP_READY, function() {

  var colors = ["green", "blue", "orange"];
  var pathArray = [path2, path3, path1];
  var polylines = [];
  pathArray.forEach(function(path, idx) {

    // Create polylines
    map.addPolyline({
      points: path,
      color: colors[idx],
      width: 7,
      zIndex: idx
    }, function(polyline) {
      polylines.push(polyline);
    });
  });

  // Change the polyline zIndex orders.
  var button = document.getElementsByTagName("button")[0];
  button.addEventListener("click", function() {

    polylines = polylines.reverse();
    polylines.forEach(function(polyline, idx) {
      polyline.setZIndex(idx);
    });

  });

});
```

![](image.gif)
