# Ni
# AUTO_DETECT_NEWVAR <- FALSE

# Returns TRUE if the user has calculated a value equal to that calculated by the given expression.
makeVector <- function(x = numeric()) {
+     m <- NULL
+     set <- function(y) {
+         x <<- y
+         m <<- NULL
+     }
+     get <- function() x
+     setmean <- function(mean) m <<- mean
+     getmean <- function() m
+     list(set = set, get = get,
+          setmean = setmean,
+          getmean = getmean)
+ }
> cachemean <- function(x, ...) {
+     m <- x$getmean()
+     if(!is.null(m)) {
+         message("getting cached data")
+         return(m)
+     }
+     data <- x$get()
+     m <- mean(data, ...)
+     x$setmean(m)
+     m
+ }
> 
