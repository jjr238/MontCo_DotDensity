<html>
  <head>
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="initial-scale=1,maximum-scale=1,user-scalable=no"
    />

    <!--
  ArcGIS API for JavaScript, https://js.arcgis.com
  For more information about the visualization-dot-density sample, read the original sample description at developers.arcgis.com.
  https://developers.arcgis.com/javascript/latest/sample-code/visualization-dot-density/index.html
  -->
<title>Current Population Estimates (ACS) Dot Density</title>

    <link
      rel="stylesheet"
      href="https://js.arcgis.com/4.12/esri/themes/dark/main.css"
    />

    <style>
      html,
      body,
      #viewDiv {
        padding: 0;
        margin: 0;
        height: 100%;
        width: 100%;
      }
    </style>

    <script src="https://js.arcgis.com/4.12/"></script>

    <script>
      require([
        "esri/WebMap",
        "esri/views/MapView",
        "esri/layers/FeatureLayer",
        "esri/renderers/DotDensityRenderer",
        "esri/widgets/Legend",
        "esri/widgets/Bookmarks",
        "esri/widgets/Expand"
      ], function(
        WebMap,
        MapView,
        FeatureLayer,
        DotDensityRenderer,
        Legend,
        Bookmarks,
        Expand
      ) {
        const map = new WebMap({
          portalItem: {
            id: "733b558f47344f308837f9ce9f64bf10"
          }
        });

       const view = new MapView({
          container: "viewDiv",
          map: map,
          highlightOptions: {
            fillOpacity: 0,
            color: [50, 50, 50]
          },
          popup: {
            dockEnabled: true,
            dockOptions: {
              position: "top-right",
              breakpoint: false
            }
          },
          constraints: {
            maxScale: 35000
          }
        });

        view.when().then(function() {
          const dotDensityRenderer = new DotDensityRenderer({
            dotValue: 20,
            outline: null,
            referenceScale: 577790, // 1:577,790 view scale
            legendOptions: {
              unit: "people"
            },
            attributes: [
              {
                field: "WHITE",
                color: "#f23c3f",
                label: "White (non-Hispanic)"
              },
              {
                field: "HISPANIC",
                color: "#e8ca0d",
                label: "Hispanic"
              },
              {
                field: "BLACK",
                color: "#00b6f1",
                label: "Black or African American"
              },
              {
                field: "ASIAN",
                color: "#32ef94",
                label: "Asian"
              },
              {
                field: "AMERI_ES",
                color: "#ff7fe9",
                label: "American Indian/Alaskan Native"
              },
              {
                field: "HAWN_PI",
                color: "#e2c4a5",
                label: "Pacific Islander/Hawaiian Native"
              },
              {
                field: "OTHER",
                color: "#ff6a00",
                label: "Other race"
              },
              {
                field: "MULT_RACE",
                color: "#96f7ef",
                label: "Two or more races"
              }
            ]
          });

          // Add renderer to the layer and define a popup template
          const url =
            "https://services1.arcgis.com/kOChldNuKsox8qZD/arcgis/rest/services/usa_tracts_MontCo/FeatureServer/0";
          const layer = new FeatureLayer({
            url: url,
            minScale: 1000000,
            maxScale: 35000,
            title: "Current Population Estimates (ACS)",
            popupTemplate: {
              title: "{County}, {State}",
              content: [
                {
                  type: "fields",
                  fieldInfos: [
                    {
                      fieldName: "WHITE",
                      label: "White (non-Hispanic)",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "HISPANIC",
                      label: "Hispanic",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "BLACK",
                      label: "Black or African American",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "ASIAN",
                      label: "Asian",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "AMERI_ES",
                      label: "American Indian/Alaskan Native",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "HAWN_PI",
                      label: "Pacific Islander/Hawaiian Native",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "OTHER",
                      label: "Other race",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    },
                    {
                      fieldName: "MULT_RACE",
                      label: "Two or more races",
                      format: {
                        digitSeparator: true,
                        places: 0
                      }
                    }
                  ]
                }
              ]
            },
            renderer: dotDensityRenderer
          });

          map.add(layer);
         
          view.ui.add(
            [
              new Expand({
                view: view,
                content: new Legend({ view: view }),
                group: "top-right",
                expanded: true
              }),
              new Expand({
                view: view,
                content: new Bookmarks({ view: view }),
                group: "top-right"
              })
            ],
            "top-right"
          );
        });
      });     
    </script>
  </head>

  <body>
    <div id="viewDiv"></div>
  </body>
</html>
