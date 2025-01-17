# leaflet-challenge

# Objective/Background: 

The United States Geological Survey, or USGS for short, is responsible for providing scientific data about natural hazards, the health of our ecosystems and environment, and the impacts of climate and land-use change. Their scientists develop new methods and tools to supply timely, relevant, and useful information about the Earth and its processes.

The USGS is interested in building a new set of tools that will allow them to visualize their earthquake data. They collect a massive amount of data from all over the world each day, but they lack a meaningful way of displaying it. In this challenge, you have been tasked with developing a way to visualize USGS data that will allow them to better educate the public and other government organizations (and hopefully secure more funding) on issues facing our planet.

### HTML file:

The purpose of this file is to set up the outline of the webpage so you can insert the logic.js file, leaflet JS file, and D3 JavaScript file, importing the CSS file, along with importing leaflet so we can use leaflet functions/code.

### Logic.js file:

We start this file by creating our tile layers and map objects to get the backgrounds of our map and then adding those tile layers to our map. We then create the layer groups, base maps, and overlays for the two sets of data and add a control layer on top of that.

Then we make a d3 request to retrieve the earthquake data and console.log it to view our data so we can extract certain elements out. Furthermore, we ccreate functions to determine the color of the markers, determine the radius of the markers, and styles the data for each earthquake plotted.

Next, we add a GeoJSON layer to the map by inserting our style function and creating a onEachFeature funtion to bind popups to each marker. We also want to create a legend control object and add all the details for the legend so the viewer can reference what's going on, loop through each interval to create colored labels, and add it to the map.

Finally, we make a request to get our tectonic plate data, we originally saved that data at the beginning of the file to the tectonic_plates layer, and then add it to the map.

### I got/referenced the following lines of code from Xpert Learning Assistant/GitHub:

* function styleInfo(feature, latlng) {
    let format = {color: getColor(feature.geometry.coordinates[2]),
      fillColor: getColor(feature.geometry.coordinates[2]),
      radius: getRadius(feature.properties.mag),
      fillOpacity: 0.5
    };
    return format

* onEachFeature: function (feature, layer) {
      layer.bindPopup(`<h3>${feature.properties.place}</h3><hr><p>${new Date(feature.properties.time)}</p><hr><p>Magnitude: ${feature.properties.mag}</p><hr><p>Depth: ${feature.geometry.coordinates[2]}</p>`);

* for (let i = 0; i < depthIntervals.length; i++) {
      labels.push('<li style=\"background-color:' + colors[i] + '\"></li> ' +
            depthIntervals[i] + (depthIntervals[i + 1] ? ' &ndash; ' + depthIntervals[i + 1] + '<br>' : '+'));
    }
    div.innerHTML += '<ul>' + labels.join('') + '</ul>';
    return div;
