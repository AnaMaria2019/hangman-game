# hangman-game
HangMan game application with 3 levels of difficulty developed using R Shiny package.

### Prerequisites

* [R Language](https://cran.r-project.org/bin/windows/base/old/3.5.1/) - version 3.5.1
* R Studio - version 1.1.456
* The following R packages need to be installed:
  * <strong>shiny</strong> - version 1.4.0.2  1.5.0 (and all the dependencies)
  * <strong>shinyjs</strong>
### Run the application
* Download the files included in this repository
* Open R Studio
* Go to `File -> Open Project -> <select the .Rproj file from the directory where the project is located>`
* Install the prerequisites packages:
  * install <strong>shiny</strong> along with the dependencies: type `install.packages("shiny", dependencies=TRUE, type="win.binary")` in the R console
  * install <strong>shinyjs</strong>: type `install.packages("skinyjs")` in the R console
* Open <strong>app.R</strong> and click on `Run App`
