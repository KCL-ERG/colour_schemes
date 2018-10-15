# Colour schemes for plotting air quality data

The following colour schemes create breaks and colours within R that can be used with the Raster package to plot raster files of air quality.

# LAEI 2013 Colours
* [NO2](https://github.com/KCL-ERG/colour_schemes/blob/master/no2_laei2013_colours_breaks.R)
* [PM10](https://github.com/KCL-ERG/colour_schemes/blob/master/pm10_laei2013_colours_breaks.R)
* [PM10 days](https://github.com/KCL-ERG/colour_schemes/blob/master/pm10d_laei2013_breaks_colours.R)
* [PM2.5](https://github.com/KCL-ERG/colour_schemes/blob/master/pm25_laei2013_colours_breaks.R)

# Example usage
pm25       <- raster('pm25.asc')

levelplot(pm25,
          maxpixels = pm25@ncols/2 * pm25@nrows/2,
          margin = FALSE,
          colorkey = list(
            at = seq(min(pm25_laei2013_breaks), max(pm25_laei2013_breaks), length = 12),
            space = 'right',
            labels = list(at=seq(min(pm25_laei2013_breaks), max(pm25_laei2013_breaks), length = 12), 
                          labels = paste(" \n \n ",pm25_laei2013_labels), 
                          font = 1,
                          cex = 1.5)
          ),
          par.settings = list(
            axis.line =list( col = 'transparent')
          ),
          scales = list(draw = FALSE),
          col.regions = pm25_laei2013_colours,
          at = pm25_laei2013_breaks)
