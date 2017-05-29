# Peer-graded-Assignment-Programming-Assignment-2-Lexical-Scoping

makeCacheMatrix <- function(x = matrix()) { ## define the argument with default mode of "matrix"
       inv <- NULL                             ## initialize inv as NULL; will hold value of matrix inverse 
       set <- function(y) {                    ## define the set function to assign new 
                x <<- y                             ## value of matrix in parent environment
                inv <<- NULL                        ## if there is a new matrix, reset inv to NULL
            }
       get <- function() x                     ## define the get function - returns value of the matrix argument
       setinverse <- function(inverse) inv <<- inverse  ## assigns value of inv in parent environment
       getinverse <- function() inv                     ## gets the value of inv 
       list(set = set, get = get, setinverse = setinverse, getinverse = getinverse)      
}

cacheSolve <- function(x, ...) { ## Return a matrix that is the inverse of 'x'
      inv <- x$getinverse()
      if(!is.null(inv)) {
            message("getting cached data")
            return(inv)
        }
      data <- x$get()
      inv <- solve(data, ...)
      x$setinverse(inv)
      inv
}
