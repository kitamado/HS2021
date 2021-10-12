### 2.1.2 Functions

1. round rounds the values in its first argument to the specified number of decimal places (default 0). 
    round(x, digits = 0). digit argument has a default value 0

    - 四舍六入五留双
    - 被修约的数字小于5时，该数字舍去；
    - 被修约的数字大于5时，则进位；
    - 被修约的数字等于5时，要看5前面的数字，若是奇数则进位，若是偶数则将5舍掉，即修约后末尾数字都成为偶数；若5的后面还有不为“0”的任何数，则此时无论5的前面是奇数还是偶数，均应进位。

3. ```R
    round(5.678, digits=1) = 5,7
    round(x=5.678, digits=1) = 5.7
    round(digits=1, x=5.678) = 5.7
    round(1, 5.678) = **1**
    ```

4. choose(5, 3)

### 2.2.2 Variables

1. ```R
    value_1 <- 6.7
    value_2 <- -56.3
    ```

2. ```R
    sqrt(value_1)  
    sqrt(value_2)
    ```

3. `x <- 2*value_1/value_2 + value_1 * value_2`


### 4.0.4 Introduction to Vectors

1. `c(-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5)`

2. `c(-6,  c(-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5), 6)`

3. ```R
    vec1 <- -5:5    
    vec2 <- 6:10
    vec3 <- c(vec1, vec2)  
    length(vec3)  
    print(vec3)
    ```

4. `-5:5; 10:6`

5. ```R
    vec1 <- rep(1:5, 3)
   vec2 <- rep(1:5, each=3) 
   vec3 <- rep(1:5, 1:5)
   vec4 <- rep(1:5, each=3, times=2)
   ```

6. ```R
    vec1 <- seq(0, 5, by=0.5)
   vec2 <- seq(1, 8.0, length.out = 6)
   vec3 <- seq(10, -0.4, by=-0.8)
   ```

7. ```R
    x <- -5:5
   x[8]
   ```

8. `x[seq(2,10,by=2)] `

9. `x[9:11] <- c(30,40,50)`

10. ```R
     vec = numeric(5)
    vec[1:5] <- 1:5
    ```

11. ```R
    x <- -5:5
    x[-seq(2, 10, by=2)]
    ```

### 4.1.2 Numeric vectors
1. ```R
     a <- -5:5
    b <- 10:0
    a - b
    a + b
    a * b
    ```
2. `sum(c(a,b))`
3. `min(a); max(a); mean(a)`
4. `- (a - mean(a)) / sd(a)`
   - I get a warning message becasue the length of the longer vector is not a multiple of the length of the shorter vector. That is 11 %% 3 = 2
5.  `a * c(1,1,5)`

### 4.2.1 Logical vectors
1. ```R
    x <- seq(-20, 20, length.out = 41)
   y <- seq(-40, 40, length.out = 41)
   sum(y > x)
   ```

2. `x[which(x %% 2 == 0)] <- 1  ` 

3. `x[(x %% 2 == 1) & (x >= 0)]  `

4. `x[x < -10 | x > 13] `
5. -` x * c(TRUE,TRUE,TRUE,FALSE)  + !c(TRUE,TRUE,TRUE,FALSE) `
  -  ANS:`x[rep(c(F,F,F,T),length.out=length(x))] <- 1 `

### 4.3.1 Character vectors

1. `paste0(c('A','B'), 1:100, collapse=' ')`
2. ` paste0(c('A','B'), rep(1:100,each=2), collapse=' ')`

3. ```R
   hello <- "Hello"
   world <- "World"
   bang <- "!"
   paste(hello, world, bang)
   paste0(hello, world, bang)
   paste0(paste(hello,world),bang)
   paste0(paste(hello,world,sep='-'),bang)
   paste0(paste(hello,world),bang,bang,bang)
   paste0(paste(hello, world),rep(bang,3),collapse = ' ')
   ```

### 4.4.1 Factors

1. Levels: 3 4 5 7 8
2. Levels: august december july may october september 
   6 levels

### 4.6.1 Sorting and shuffling vectors
1. ```R
    x <- c(3, 4, -6, 2, -7, 2, -1, 0)
    sort(x)
    sort(x, decreasing=T)
    ```
    
2. ```R
    x <- c(3, 4, -6, 2, -7, 2, -1, 0)
    x[sort(x,index.return=T)$ix[1:3]] 
    wrong
    ```
    > Take the same vector x with elements 3, 4, -6, 2, -7, 2, -1, 0, but this time only sort the first three elements in increasing order.
    > 
    **Understanding!!**  sort first three elements in x, not show the first three elements in sorted x
    **ANS:**
    ` sort(x[1:3])`
    
3. ```R
    v <- sample(8:37, size=98, replace = T)            
     V <- sample(v, size = 10)  
     sort(V, decreasing = T)  
     wrong
    ```
     > Create a vector v with 98 evenly spaced elements between 8 and 37. Then from v, sample 10 elements at random and store these 10 elements in a new vector called V. Then, sort V in decreasing order.
     > 
    **ANS:**
    ```R
    v <- seq(8,37,length.out=98)  
    V <- sample(v, size = 10)  
     sort(V, decreasing = T) 
    ```

### 5.2.1 Accessing Matrix Elements
1. ```R
    A <- matrix(1:16, nrow=4, byrow=TRUE)
    B <- A[-4,]
    ```
2.  sum(A[2,])
3.  sum(A[,3])
4.  A[which(A+1<(A/3)^2)] <- -1

### 5.3.1 Matrix Arithmetic
1. ```R
    Z <- matrix(c(-1,1,1,-1),nrow=2)
    Z %*% t(Z)
    ```
2. ```R
    A <- matrix(1:4, ncol=2, byrow=T)
    B <- matrix(c(-1,1), ncol=3, nrow=2, byrow=T)
    A %*% B
    ```
3. `solve(matrix(c(1,-2,-1,-3,0,1,7,1,0),ncol=3))`
4. ```R
    E <- matrix(1:4, ncol=2)
    G <- matrix(5:8, ncol=2)
    E
    G
    E * G
    E / G
    E %*% G
    E + G
    E - G
    E == G
    ```
### 6.1.1 Data Frames
1. ```R
    x <- 5:0
    y <- 0:5
    data.frame(x=x,y=y)
    ```
1. ```R
    z <- 10:6
    w <- 6:10
    e <- data.frame(z=z,w=w)
    names(e) <- names(d)
    f <- rbind(d,e)
    ```
3.  `cbind(f, compared=c(x>y,z>w))`, `cbind(f, compared=f[1]>f[2])`



### 6.2.1 Accessing data frames

1. ```R
   d <- data.frame(x=1:10,y=c(1,10,-2,3,8,-7,2,1,9,4))
   d[which(d$x==d$y),]
   ```

2. `mean((d$y/d$x)[(length(d$y)-5+1):length(d$y)])`

### 6.3.1 Manipulating data frames

1. ```R
   data <- data.frame(id=paste("X",1:10,sep=""), x=sample(-10:10,size=10,replace = TRUE), y=sample(-10:10,size=10,replace = TRUE)^2)
   ```

2. ```R
   data <- data.frame(data, ok=data$y>20)
   f <- data$x > 3 & data$ok == TRUE
   other <- data[f,c("id","y")]
   ```

### 7.3.1 Lists

1. ```R
   holiday <- list(country=c("CH","USA","Japan"), continent=c("Europe","The Americas", "East Asia"))
   ```

2. ```R
   l <- list(holiday, place=c("mountain","beach"), day=c(1.0,20.0,4), like=c(TRUE, FALSE))
   ```

   > 1. Create a list with four four elements. 1) the list “holiday” from the exercise above, 2) a character vector “place” containing “mountain” and “beach,” 3) a **numerical** vector “day” containing the numbers **1.0 through 20.0**, and 4) a logical vector “like” containing `TRUE`and `FALSE`.
   >
   >    **ANS:**
   >
   >    ```R
   >    x <- list(holiday=holiday, place=c("mountain", "beach"), day=as.numeric(1:20), like=c(TRUE,FALSE))  
   >    ```
   >
   >    

3. ` l[[1]][[1]][2]`

4. ` l[[1]]$continent[1]` or `x$holiday[[2]][1]`

5. `l[[c(1,1,3)]]`

6. ```R
   name <- "day"
   l[name]
   ```

7. `new_list <- l[c('place','like')]`

8. ```R
   Chapters <- paste("Chapter 3. R-Scripts", "Chapter 4. Vectors", "Chapter 5. Matrices", "Chapter 6. Data Frames")
   split <- strsplit(Chapters, "\\. ")
   split[[1]][5]
   ```

   > 1. Create a chracter vector “Chapters” and concatenate 4 strings. 1) first “Chapter 3. R-Scripts” 2) second “Chapter 4. Vectors” 3) “Chapter 5. Matrices” 4) “Chapter 6. Data Frames.” Extract just the word “Data Frames” with no spaces as a character from Chapters.
   >
   >    **ANS:**
   >
   >    ```R
   >    Chapters <- c("Chapter 3. R-Scripts","Chapter 4. Vectors","Chapter 5. Matrices", "Chapter 6. Data Frames")  
   >    strsplit(Chapters,"\\. ")[[c(4,2)]]  
   >    ```

### 8.1.1 Conditionals

1. > Use conditionals to that informs you if the elements of a vector x of length 3 are strictly increasing, or not, by pritting an appropriate message. Test it on the vector `x <- c(1,4,3)`
   >
   > ```R
   > x <- c(1,4,3)  
   > if(x[1]<x[2]&&x[2]<x[3]){ print("increasing") }else{ print("not increasing") }  
   > ```
   >
   **QA** How can I solve this when x has more elements?

   My original thought:(not working...)

   *Warning message:*
   *In if (sort(x) == x) { :*
      *the condition has length > 1 and only the first element will be used*

    ```R
    x <- c(1,4,3)
    if (which(sort(x) == x)) {
      print("X is strictly increasing.")
    } else {
      print("X is not strictly increasing")
    }
    ```

    which(sort(x)==x)   TRUE FALSE FALSE and only TRUE is used.

    **possible way**（ugly)

    ```R
    x <- c(1,4,3)
    if (x[sort(x) != x][1] > 0) {
      print("X is not strictly increasing.")
    } else {
      print("X is strictly increasing")
    }
    ```

   **EASY**

   ```R
   if(is.unsorted(x)) print("not increasing")
   # or
   if(all(diff(x) > 0)) print("increasing")
   ```

### 8.2.3 Loops

   1. ```R
      x <- sample(1:10)
      for(i in 1:length(x)-1) {
        if (x[i] > x[i+1]) {
          print("Vector is not strictly increasing!")
          break
        }
      }
      ```

   2. ```R
      n <- 10
      v <- c()
      for (i in 1:n) {
        for (j in 1:i) {
         v <- c(v,i)
        }
      }
      ```

   3. ```R
      m <- matrix(1:120, nrow=3)
      s <- c()
      for (i in 1:ncol(m)) {
        s <- c(s, sum(m[, i]))
      }
      ```

   4. ```R
      i = 1
      while (i < 11) {
        print(paste("I like number", i))
        i <- i + 1
      }
      ```

   5. ```R
      n <- 3
      v <- integer(100)
      v[1] <- 0
      v[2] <- 1
      while (n <= 100) {
        v[n] <- v[n-1] + v[n-2]
        n <- n + 1
      }
      ```

   6. ```R
      x <- sample(1:100)
      y <- sample(1:100)
      for (i in 1:100) {
        if (x[i] > y[i]) {
          print(x[i] * y[i])
        } else if (x[i] < y[i]) {
          print(x[i] + y[i])
        }
      }
      ```

   7. ```R
      x <- c(5,6,8,2,3,7,8,1,2,3,4)
      for (i in 1:length(x)) {
        if (x[i] >= 2) print(x[i])
        else break
      }
      ```

   8. ```R
      m <- matrix(NA,3,3)
      for (i in 1:3) {
        for (j in 1:3) {
          print(paste(i,j))
          m[i,j] <- i+j
        }
      }
      ```

   9. ```R
      i <- 2
      p <- 1
      while (p < 5000000) {
        p <- p * i
        i <- i + 1
      }
      print(i-1)
      ```


   ### 9.0.2 Basic Plotting

   1.  ```R
       x <- seq(-5,5,length.out=20)
       y <- 2*x^2
       plot(x,y,col="red",type='b',xlab='My variable x',ylab='Some transformation of x', main='The plot of a noob',pch=19)
       ```

   2. ```R
      x <- seq(-5,5,length.out=20)
      y <- 2*x^2
      par(mar=c(2,2,0,0))
      plot(x, y, type='l', col=colors()[sample(length(colors()), 1)], lwd=10, xlab="", ylab="") 
      ```

   3. **ANS**

      ```r
      x <- rep(1:26, each=26)  
      y <- rep(1:26, 26)  
      plot(x, y, pch=15, col=colors(), cex=1.6)  
      ```



  4. ```r
     #There are at least two solutions:  
     plot(1:100, pch=19, col=c(rep("orange", 6), "red"))  
     # or  
     plot(1:100, pch=19, col=c("orange", "red")[1 + (1:100 %% 7 ==0)])  
     ```

### 9.1.5 Plotting

1. ```R
   x <- seq(1.0,100,by=0.5)
   y <- sqrt(x)
   z <- log(x)
   d <- data.frame(x=x,y=y,z=z)
   plot(x, y, col="red", type='l', lty=1, lwd=3, xlab='x', ylab='A transformation of x')
   lines(x,z,col='blue',lty=2)
   legend('topleft', legend=c('sqrt(x)', 'log(x)'), col=c('red', 'blue'), lty=c(1,2), lwd=c(3,1))
   ```

2. ```R
   plot(0, type='n', xlim=c(-10,10), ylim=c(-1,1), xlab='x', ylab='y')
   abline(v=0, lty=2, col='red')
   abline(h=0, lty=2, col='red')
   text(5,0.5,labels='I')
   text(-5,0.5,labels='II')
   text(-5,-0.5,labels='III')
   text(5,-0.5,labels='IV')
   ```

3. ```R
   av.high <- c(32, 34, 34, 32, 32, 30, 32, 30, 30, 30, 32, 32)
   av.rain <- c(16, 31, 104, 131, 161, 155, 193, 225, 192, 199, 76, 27)
   par(las=1, mar=c(4,4,0.5,4))
   plot(1:12,av.high,type='b',col='red',pch=19, xlab='Month',ylab='average daily high temperature[°C]')
   scale <- 52.25
   lines(1:12, (av.rain-16)/scale+30, type='b', col='blue', pch=16)
   labels <- pretty(16:225)
   axis(side=4,at=(labels-16)/scale+30,labels=labels)
   mtext("average percipitation [mm]", side=4, line=3, las=3)
   ```



### 9.2.1 Plotting Multiple Panels

1. ```R
   x <- seq(1,100,by=0.5)
   d <- data.frame(x=x,y=sqrt(x),z=log(x))
   par(mfrow=c(1,2),mar=c(4,4,2,2))
   plot(d$x,d$y,main='sqrt(x)',xlab='x',ylab='y')
   plot(d$x,d$z,main='log(x)',xlab='x',ylab='z')
   ```

2. ```r
   x <- 1:100
   y <- matrix(0,ncol=100,nrow=12)
   par(mfrow=c(3,4))
   for (i in 2:13) {
     y[i-1,] <- log(x,base=i)
     plot(x,y[i-1,],col=colors()[i],pch=i,type='b',xlab='x',ylab=paste('log',i,'(x)',sep=''))
     legend('bottomright',legend=i,bty='n')
     }
   ```

3. ```r
   layout(mat = matrix(c(1,1,2,3,4,4),nrow=3,byrow=T))
   x <- 1:100
   a <- sqrt(x)
   for (i in 1:4) {
     plot(x,a)
   }
   ```

### 10.0.4 Probability distributions

1. ```R
   > dexp(x=0.15,rate=2)
   [1] 1.481636
   ```

2. ```R
   > dpois(x=3,lambda = 2)
   [1] 0.180447
   ```

3. ```R
   > qnorm(0.99,mean=5,sd=2)
   [1] 9.652696
   ```

4. ```R
   > dbeta(0.72,shape1 = 0.7,shape2 = 0.7)
   [1] 0.8513717
   ```

5. ```r
   > qnorm(0.7)
   [1] 0.5244005
   ```

6. ```r
   rpois(100, lambda=2)
   ```

7. ```r
   rexp(13,rate=0.5)
   ```

8. ```r
   sum(rnorm(1000) < -1) / 10^3
   > pnorm(-1)
   [1] 0.1586553
   # yes, it get closer to theoretical expectation with more random draws
   ```

9. ```r
   > sum(rbinom(10^3, size=10,prob=0.1) > 2) / 10^3
   [1] 0.07
   > 1 - pbinom(2,size=10,prob=0.1)
   [1] 0.07019083
   ```

10. ```r
    plot(x, dnorm(x, mean=164.7, sd=7.1), type='l', col='red')
    lines(x, dnorm(x, mean=178.4, sd=7.6), type='l', col='blue')
    abline(v=160, lty=2)
    dnorm(160, mean=164.7, sd=7.1)
    [1] 0.04513322
    ```

11. ```r
    x <- seq(140,200,length.out=100)
    plot(x, pnorm(x, mean=164.7, sd=7.1), type='l', col='red')
    lines(x, pnorm(x, mean=178.4, sd=7.6), type='l', col='blue')
    abline(v=160, lty=2)
    pnorm(160, mean=164.7, sd=7.1)
    ```
    
12. ```r
     fq <- qnorm(c(0.05,0.32,0.5,0.68,0.95), mean=164.7, sd=7.1)
     mq <- qnorm(c(0.05,0.32,0.5,0.68,0.95), mean=178.4, sd=7.6)
        
     x <- seq(140,200,length.out=100)
     plot(x, dnorm(x, mean=164.7, sd=7.1), type='l', col='red')
     lines(x, dnorm(x, mean=178.4, sd=7.6), type='l', col='blue')
     
     abline(v = fq, col='orange')
     abline(v = mq, col='lightblue')
    ```
    
13. ```R
    par(mfrow=c(2,1))
    # Probability density function
    x <- seq(0,5,length.out=100)
    plot(x, dexp(x,rate=0.5), type='l', col='orange', ylim=c(0,1.5), lwd=3, ylab='P(x)', xlab='x')
    lines(x, dexp(x, rate=1), type='l', col='purple', lwd=3)
    lines(x, dexp(x, rate=1.5), type='l', col='lightblue', lwd=3)
    legend('topright', legend=c('λ=0.5','λ=1','λ=1.5'), col=c('orange', 'purple','lightblue'),lwd=c(3,3,3),bty='n')
     # Cumulativ distribution function
    x <- seq(0,5,length.out=100)
    plot(x, pexp(x,rate=0.5), type='l', col='orange', ylim=c(0,1), lwd=3, ylab='P(X<=x)', xlab='x')
    lines(x, pexp(x, rate=1), type='l', col='purple', lwd=3)
    lines(x, pexp(x, rate=1.5), type='l', col='lightblue', lwd=3)
    legend('bottomright', legend=c('λ=0.5','λ=1','λ=1.5'), col=c('orange', 'purple','lightblue'),lwd=c(3,3,3),bty='n')
    ```
    
14. ```r
    x <- integer(100)
    for (i in 2:length(x)) {
      x[i] <- rnorm(1, mean=x[i-1], sd=1)
    } 
    plot(x, type='p', col='purple')
    ```

15. ```r
    benefit <- integer(1000)
    times <- 0
    for (i in 1:1000) {
      win <- 0
      b <- 1
      e <- b
      while (b <= 100) {
        win <- rbinom(1, size=1, prob = 18/37)
        if (win == 0) {
          b <- 2*b
          e <- e + b
        } else {
          times <- times + 1
          benefit[i] <- b*2 - e
          break
        }
      }
      if (win == 0) {
        benefit[i] <- -e
      }
    }
    
    often <- times / 1000
    avg_benefit <- mean(benefit)
    print(paste('The player win at a possibility of', often))
    print(paste('The average net benefit is', avg_benefit))
    ```

### 10.1.3 Empirical Distributions

1. ```r
   x <- rbinom(1000, size=5, prob=0.2)
   par(mfrow=c(1,2))
   hist(x)
   plot(density(x))
   ```

2. ```r
   x <- seq(0,20,length.out=100)
   plot(x, dnorm(x, mean=10, sd=2), col='red', lty=1, type='l',lwd=3)
   lines(density(rnorm(10, mean=10, sd=2)), lty=2)
   lines(density(rnorm(100, mean=10, sd=2)), lty=3)
   lines(density(rnorm(1000, mean=10, sd=2)), lty=4)
   lines(density(rnorm(10000, mean=10, sd=2)), lty=5)
   lines(density(rnorm(100000, mean=10, sd=2)), lty=6)
   legend('topleft',legend=c('sample 10^1', 'sample 10^2', 'sample 10^3', 'sample 10^4', 'sample 10^5'), lty=c(2,3,4,5,6), bty='n')
   ```

3. ```r
   data("iris")
   
   # plot histograms  
   par(mfrow = c(1,3))  
   hist(iris$Petal.Length[iris$Species == "setosa"], col = "dodgerblue", xlab = "petal length", main = "setosa")  
   hist(iris$Petal.Length[iris$Species == "versicolor"], col = "orange2", xlab = "petal length", main = "versicolor")  
   hist(iris$Petal.Length[iris$Species == "virginica"], col = "firebrick", xlab = "petal length", main = "virginica")
   
   # plot kernel  
   par(mfrow = c(1,1))  
   plot(density(iris$Petal.Length), ylim = c(0, 2.6), main = "Distribution of petal length")  
   lines(density(iris$Petal.Length[iris$Species == "setosa"]), col = "dodgerblue")  
   lines(density(iris$Petal.Length[iris$Species == "versicolor"]), col = "orange2")  
   lines(density(iris$Petal.Length[iris$Species == "virginica"]), col = "firebrick")  
   legend("topright", legend = c("global", "setosa", "versicolor", "virginica"), col = c("black", "dodgerblue",  "orange2", "firebrick"), lty = rep(1, 4))  
   ```

### 11.0.1 Data Input and Export

1. `"C:/Users/sywu_/Documents"`
2. `setwd('D:/Documents/workspace/learning-R')`

### 11.1.5 Exporting and Importing

1. ```r
   d <- data.frame(x=rnorm(100),y=rnorm(100),z=rnorm(100))
   write.table(d, 'my_data_frame.txt', row.names = F)
   d <- read.table('my_data_frame.txt', header=T)
   ```

2. `read.csv2('foo.txt')`

3. ```r
   d <- read.csv2(url('https://www.bfs.admin.ch/bfsstatic/dam/assets/12647632/appendix'), stringsAsFactors=F)
   d <- d[-1,] 
   plot(d$pop1930, d$pop2018, xlab="1930", ylab="2018")  
   ```

### 11.2.1 Listing files

1. ```r
   > length(list.files(path='D:/Downloads', pattern='*.pdf'))/length(list.files(path='D:/Downloads'))
   [1] 0.5777778
   ```

### 11.3.1 Exporting graphics

1. ```r
   x <- rnorm(100)
   y <- 4 + 1.5*x + rnorm(100,mean=0,sd=sqrt(0.2))
   pdf('11.3.1[1].pdf')
   
   par(mar=c(4,4,0.1,0.1))
   plot(x,y)
   dev.off()
   ```

2. ```R
   x <- rnorm(100)
   y <- 4 + 1.5*x + rnorm(100,mean=0,sd=sqrt(0.2))
   pdf('11.3.1[2].pdf', width=2, height=2)
   par(mar=c(4,4,0.1,0.1))
   plot(x,y)
   dev.off()
   ```

3. ```r
   jpeg('11.3.1[3][1].jpeg', width=480, height=480, pointsize=12)
   par(mar=c(4,4,0.1,0.1))  
   plot(x,y)
   dev.off()
   jpeg('11.3.1[3][2].jpeg', width=1280, height=1280, pointsize=12*1280/480)
   par(mar=c(4,4,0.1,0.1))  
   plot(x,y)
   dev.off()
   ```

### 12.0.1 Installing packages

2. ```r
   x <- seq(-4,4,by=0.1)
   cols <- brewer.pal(10,'Spectral')
   plot(0,type='n',xlim=c(-4,4),ylim=c(0,4))
   for (i in 1:10) {
     lines(x, dnorm(x, sd=i/10), col=cols[i])
   }
   ```

### 13.1.3 Input to functions

1. ```R
   my_power <- function (x,y=2) {
     return (x^y)
   }
   ```

2. ```R
   calcKelvintoF <- function(k) {
     if (k < 0) {
       stop("Kelvin cannot be negetive!")
     }
     return (k * 9/5 - 459.67)
   }
   ```

### 13.3.4 Return Values

1. ```r
   factorialf <- function (n) {
     f <- 1
     if (n==0) 
         return (f)
     else {
         for (i in 1:n) 
           f <- f * i
         return (f)
     }
   }
   ```

2. ```r
   factorialf <- function (n) {
     if (n==0) 
       return (1)
     else 
       return (prod(1:n))
   }
   ```

3. ```r
   simulateDice <- function() {
     randomd <- sample(1:6, 100, replace=T)
     count <- 0
     for (i in randomd) {
       if (i==6) count <- count + 1
     }
     return(list(simulaterNo=randomd, totolnum6=count))
   }
   ```

4. ```r
   simulateDice <- function() {
     randomd <- sample(1:6, 100, replace=T)
     count <- sum(randomd==6)
     return(list(simulaterNo=randomd, totolnum6=count))
   }
   ```

5. ```r
   fizzbuzz <- function (n) {
     if (n %%3 == 0 & n %%5 == 0) 
       return("fizzbuzz")
     else if (n %% 3 == 0) return ("fizz")
     else if (n %% 5 == 0) return ("buzz")
     else return (n)
   }
   ```

### 13.4.1 Environment

1.  10

2. ```R
   x <- rnorm(10^6)
   sumf <- function(x) {
     sum <- 0
     for(i in 1:length(x)) {
       sum <- sum + x[i]
     }
     return (sum)
   }
   system.time(sumf(x))
   system.time(sum(x))
   ```

3. ```r
   x <- matrix(rpois(100*10, rep(1:10,100)), nrow=100, byrow=T)
   ```

   it's the same thing as the answer

   ```r
   m <- matrix(rpois(100*10, lambda=rep(1:10, each=100)), ncol=10)  
   ```

   note the difference between `rep(1:10, 100)` and `rep(1:10, each=100)`

### 14.1.5 Apply

1. ```r
   lapply(sample(1:1000, size=100, replace=T), rep, 10)
   ```

2. ```r
   m <- matrix(rnorm(11*1000,mean=rep(-5:5,1000),sd=rep(seq(0.1,2,length.out=11),1000)),nrow=11)
   apply(m,1,mean)
   apply(m,1,sd)
   ```

3. ```r
   means <- rowMeans(m)
   sds <- apply(m,1,sd)
   m <- sweep(m,1,means,"-")
   m <- sweep(m,1,sds,"/")
   apply(m,1,mean)
   apply(m,1,sd)
   ```

4. ```r
   sumBelow <- function (x, a) {
     return (sum(x[x<a]))
   }
   apply(m,1,sumBelow,a=0)
   apply(m,1,sumBelow,a=1)
   ```

5. ```r
   par(mfrow=c(2,2))
   apply(m[4:7,],1,hist)
   ```

### 15.5.1 S3 Classes

1. ```r
   circle <- function (radius) {
     if (radius <= 0) {
       stop("Error! Radius must be greater than 0")
     }
     c <- list(radius = radius)
     class(c) <- "circle"
     return (c)
   }
   
   circle(0)
   circle(22.4)
   circle(11)
   ```

2. ```r
   print.circle <- function (x,...) {
     print(paste0("Hi, I'm a circle. My radius is ",x$radius, "."))
   }
   c1 <- circle(100)
   print(c1)
   ```

3. ```r
   library(grid)
   plot.circle <- function(x){  
     grid.circle(r = x$radius)  
   }
   
   plot(c1)
   ```

4. ```r
   perimeter <- function (x) {
     UseMethod("perimeter",x)
   }
   perimeter.circle <- function (x) {
     return (2 * pi * x$radius)
   }
   
   perimeter(c1)
   ```

5. ```r
   area <- function (x) {
     UseMethod("area",x)
   }
   area.circle <- function (x) {
     return (pi * x$radius * x$radius)
   }
   
   area(c1)
   ```

6. See above

7. ```r
   rectangle <- function (width, height) {
     if (any(width <=0 | height <= 0)) {
       stop("Error! width and height have to be positive.")
     }
     r <- list(width = width, height = height)
     class(r) <- "rectangle"
     return (r)
   }
   
   print.rectangle <- function(x){  
     output <- paste0("Here's a rectangle with width = ", x$width, " and height = ", x$height, ".")  
     print(output)  
   }
   
   plot.rectangle <- function(x){  
     grid.rect(x$width, x$height)  
   }
   
   perimeter.rectangle <- function (x) {
     return (2*x$width + 2*x$height)
   }
   
   area.rectangle <- function (x) {
     return (x$width * x$height)
   }
   ```

8. `print()` call `UseMethod('print', x)`. Then call `print.default()`. which in this case print like list.

9. ```r
   print.mammal <- function(x, ...){  
     print(paste0("This is ", x$name, ". It's a ", x$color, " ", x$sex, " mammal."))  
   }
   
   print(bobby)  
   ```

10. ```r
    class(bobby) <- c("mammal", "cow")
    # same
    ```

11. ```r
    class(bobby) <- rev(class(bobby))
    ```

12. ```r
    print.cow <- function (x) {
      print(paste0("This is ", x$name, ". It's a ", x$color, " male cow."))
    }
    ```

### 16.1.9 Tidyverse

1. ```r
   filter(iris, Sepal.Length %in% c(5.0,6.0,7.0)
   ```

2. ```r
   data("ChickWeight")  
   ChickWeight %>% filter(Diet != 4) %>% group_by(Time) %>% summarise(mean_weight = mean(weight, na.rm=T))
   ```



