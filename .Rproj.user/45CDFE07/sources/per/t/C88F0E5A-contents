
library(shiny)
library(shinyjs)
library(stringr)

nr<-0
parti<-0
letter<-""
cuvant<-""

dictionar_usor <- c("casa", "pisica", "mar", "cap", "pat", "viata", "copac", "papuc", "apa", "carte")
dictionar_mediu <- c("morcov", "pantof","patura","gandac","castron","masinarie","gargarita","garderoba", "ceaslov", "mlastina")
dictionar_greu <- c("pripadavatelnita", "piropopilcanita", "sternocleidomastoidian","cocostarceala","matrimoniale","encefalograma","computerizare", "zbantuiala", "amfetamina","amfiteatru"  )

ui <- fluidPage(
  theme="gallows.css",
  titlePanel("Spanzuratoarea"),
  sidebarLayout(
    sidebarPanel(
      
    
    textInput("nume", "Nume"),
      
    radioButtons("dificultate", "Alege dificultatea jocului:",c("Usor" = 1, "Mediu" = 2, "Greu" = 3), inline = TRUE),
      
    actionButton("button", "Incepe un joc nou")
    ),
    
    mainPanel(
        
        useShinyjs(),
        textOutput("nume_jucator"),
        br(),
        div(id="container",
              
              img(src="Anonymous-Gallows.png", align = "center"),
              div(id="cap"),
              div(id="corp"),
              div(id="mana-stanga"),
              div(id="mana-dreapta"),
              div(id="picior-drept"),
              div(id="picior-stang")
            )
    )

  )
)

server <- function(input, output){
  
  observeEvent(input$button, {
    
    nr<<-0
    parti<<-0
    letter<<-""
    cuvant<<-""
    print(nr)
    print(parti)
    removeUI(selector="#cuvant_container")
    removeUI(selector="#lit")
    removeUI(selector="#but")
    runjs("document.getElementById('cap').style.visibility='hidden';")
    runjs("document.getElementById('corp').style.visibility='hidden';")
    runjs("document.getElementById('mana-stanga').style.visibility='hidden';")
    runjs("document.getElementById('mana-dreapta').style.visibility='hidden';")
    runjs("document.getElementById('picior-stang').style.visibility='hidden';")
    runjs("document.getElementById('picior-drept').style.visibility='hidden';")
    
   
  
     # if(is.null(users[input$name]))
      # {users2<-c(users,input$name); # Am incercat si noi sa retinem utilizatorii, dar ne-au aparut niste erori cu environment
     #  users[[input$name]]<-0} })
    output$nume_jucator <- renderText({c("Bine ai (re)venit, ", input$nume," !")})
    
    x <- sample(1:10, 1)
    d <- input$dificultate

    insertUI(
      selector="#container",
      where="afterEnd",
      ui=div(id="cuvant_container")
    )

    if(d==1){
      
      cuvant <<- dictionar_usor[x]
      print(cuvant)
   
      i=0
      l=nchar(cuvant)
      
      while(i<l){
        
        insertUI(
          selector="#cuvant_container",
          where="beforeEnd",
          ui = div(class = "litera", id=paste0("id",i))
        )
        i=i+1
      }
    }
    else if(d==2){
      
      cuvant <<- dictionar_mediu[x]
      print(cuvant)
      
      i=0
      l=nchar(cuvant)
      
      while(i<l){
        
        insertUI(
          selector="#cuvant_container",
          where="beforeEnd",
          ui = div(class = "litera", id=paste0("id",i))
        )
        i=i+1
      }
    }
    else if(d==3){
      
      cuvant <<- dictionar_greu[x]
      print(cuvant)
      
      i=0
      l=nchar(cuvant)
      
      while(i<l){
        
        insertUI(
          selector="#cuvant_container",
          where="beforeEnd",
          ui = div(class = "litera", id=paste0("id",i))
        )
        i=i+1
      }
    }
    
    insertUI(
      selector = "#cuvant_container",
      where="afterEnd",
      ui = div(id="lit")
    )
    
   insertUI(
     selector = "#lit",
     where="beforeEnd",
     ui = textInput("liti", "Scrie o litera: ")
   )
 
   insertUI(
     selector = "#lit",
     where="afterEnd",
     ui = actionButton("but", "Incearca!")
   )
  })
  
  
  observeEvent(input$but,{
    
    letter<<-input$liti
    if(nchar(letter)==1){
      
      pozitii<- as.data.frame(str_locate_all(pattern=letter, cuvant))
      
      if(str_detect(cuvant,letter)==FALSE)
      {
        parti<<-parti+1
        print(cuvant)
        print(parti);
        
        if(parti==6){
          runjs("document.getElementById('picior-drept').style.visibility='visible';")
          runjs("alert('Din pacate nu ati reusit sa ghiciti cuvantul.');")
        }
        
        if(parti==1){
          runjs("document.getElementById('cap').style.visibility='visible';")
        }
        
        if(parti==2){
          runjs("document.getElementById('corp').style.visibility='visible';")
        }
        
        if(parti==3){
          runjs("document.getElementById('mana-stanga').style.visibility='visible';")
        }
        
        if(parti==4){
          runjs("document.getElementById('mana-dreapta').style.visibility='visible';")
        }
        
        if(parti==5){
          runjs("document.getElementById('picior-stang').style.visibility='visible';")
        }
      }
      else{
        for(y in 1:nrow(pozitii)){
          runjs(paste0("document.getElementById('id",as.character(pozitii[y,1]-1),"').innerHTML='",letter,"';"))
          nr<<-nr+1
        }
        
        if(nr==nchar(cuvant)){
          runjs("alert('Felicitari!Ati ghicit cuvantul.');")
          #users[[input$name]]<<-users[[input$name]]+1
        }
      }
    } 
    else
      runjs("alert('Introduceti doar o litera!');")
    
  })
}

shinyApp(ui = ui, server = server)

