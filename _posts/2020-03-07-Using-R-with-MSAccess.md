I'm doing a subject, Experimental Design, for my Masters of Science (Data Science) at USQ.

In that subject, we use SPSS as the analytics tool.  However, I've taken it upon myself to run the coursework in R, as a side effort to get back up-to-speed in R (mostly using Python for work).

I recently was challenged when trying to retrieve data from a Microsoft Access DB (yes - it still gets used, and yes - it's waaay more popular than you might think).

Most of the material online, references the [RODBC](https://cran.r-project.org/web/packages/RODBC/index.html) package. Newer packages are also available [DBI]() by RStudio, .  However, on Windows, none of them work out of the box.  For example, by default RODBC only works with 32-bit versions of R/MSAccess. Try this with 64-bit and get:

```r
library(RODBC)
channel <- odbcConnectAccess("C:/Program Files/IBM/SPSS/Statistics/26/Samples/English/demo.mdb")
> channel <- odbcConnectAccess("C:/Program Files/IBM/SPSS/Statistics/26/Sample$
Error in odbcConnectAccess("C:/Program Files/IBM/SPSS/Statistics/26/Samples/English/demo.mdb") : 
  odbcConnectAccess is only usable with 32-bit Windows
```
Alternatively, you can try the odbcConnectAccess2007 function, but you might get this error:
```r
> channel <- odbcConnectAccess2007("C:/Program Files/IBM/SPSS/Statistics/26/Sa$
Warning messages:
1: In odbcDriverConnect(con, ...) :
  [RODBC] ERROR: state IM002, code 0, message [Microsoft][ODBC Driver Manager] Data source name not found and no default driver specified
2: In odbcDriverConnect(con, ...) : ODBC connection failed
```
Which is telling you that you don't have a 64-bit ODBC driver installed for Access.
Here's how I resolved it:
1. Download the [Microsoft Access Database Engine](https://www.microsoft.com/en-us/download/details.aspx?id=54920).  Select the 64-bit version.
2. Run the Installer, accept the Lcense Agreement, and click-click-next your way to install.
3. Confirm by checking the ODBC Administrator panel (Start -> Type in "ODBC Data Sources (64-bit)".  Under "User Data Sources", the Access source should have the "Microsoft Access Driver" listed under Drivers.

Now the code should work:
```r
> channel <- odbcConnectAccess2007("C:/Program Files/IBM/SPSS/Statistics/26/Sa$
> 
```
The key here is the 64-bit driver.  Once installed, a lot of the other packages will also work.  If you're using RStudio they have a nice [little menu tab](https://db.rstudio.com/rstudio/connections/) in the interface that you can use with the DBI package to make the connection.
