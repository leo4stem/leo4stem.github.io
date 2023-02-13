The National Assessment of Educational Progress (NAEP) is the largest
nationally representative assessment on mathematics, reading, science,
and writing. The standard administration practices provides a common and
useful measure of student achievement. 

In this post, I will show you how
to use NAEP-provided API to download the NAEP formatted data. You can
find the detail
[here](https://www.nationsreportcard.gov/api_documentation.aspx) for
further information.  

Here is an example. I use the URL to read mean score of nation-level Math data in 2013 and 2015 by gender for Grade 8.  
-    mean score: stattype=MN%3AMN  
-    by GENDER: variable=GENDER  
-    in 2013 and 2015: Year=2015,2013  
-    math subject: subject=mathematics  
-    students in Grade 8: grade=8  
-    nation level: jurisdiction=NP
-    math score name: subscale=MRPC

`url<-'https://www.nationsreportcard.gov/Dataservice/GetAdhocData.aspx?type=sigacrossjuris&subject=mathematics&grade=8&subscale=MRPCM&variable=GENDER&jurisdiction=NP&stattype=MN%3AMN&Year=2015,2013'`  

The following is the full code, which I write to download the NAEP data in national level and state level math and reading performance for Grade 4 and 8 during the period from 1996 to 2022.


    library(RSelenium)
    library(netstat)
    library(wdman)
    library(seleniumPipes)
    library(rvest)
    library(tidyverse)
    library(httr)
    library(jsonlite)
    library(tibble)

    path <-'https://www.nationsreportcard.gov/DataService/GetAdhocData.aspx'

    # Subjects: math, reading
    subject_all<-c('reading','mathematics')

    # Grade: 4, 8
    grade_all<-c('4','8')

    # subscale: 
    # Math: MRPCM - Composite scale
    # Reading: RRPCM - Composite scale

    variable_all<-c('TOTAL','SLUNCH3')

    # Jurisdiction: location 
    states<-paste0(state.abb,collapse="%2c")
    jurisdiction<-paste('NT%2cNP%2c',states,sep="")

    # stattype:
    # ALC:AB - Cumulative achievement level - At or above Basic 
    stattype_all<-c('ALC%3aAB')

    # Time: year from 1996 to 2022
    year<-'2022%2c2019%2c2017%2c2015%2c2013%2c2009%2c2007%2c2005%2c2003%2c2000%2c1996'

    # Set
    tempdata <- data.frame() 
    data<-data.frame()

    i <- 0 
    circle <- 0

    for(subject in subject_all){
      
      # define subject
      i<- i +1
      if (i == 1){
          subject <- 'reading'
          subscale <-'RRPCM'
      }
        else if (i == 2){
          subject <- 'mathematics'
          subscale <-'MRPCM'
        }
          
      # setup loops for grade, variables, and stat type   
      for(grade in grade_all){
        for(variable in variable_all){
          for(stattype in stattype_all){
            
            circle <- circle + 1
            print(paste0("Circle=",circle))
            print(paste0("Subject=",subject, "Grade=",grade, "-",variable, "-",stattype ))
            
            # create url
            url<-paste(path,'?type=data&subject=',subject,
                       '&grade=',grade,
                       '&subscale=',subscale, 
                       '&variable=',variable,
                       '&jurisdiction=',jurisdiction,
                       '&stattype=',stattype,
                       '&Year=',year,
                       sep='')
            
            # Read url 
            s <- RCurl::getURL(url )
            
            # Turn to data
            s1<- jsonlite::fromJSON(s)
            #tempdata<-tbl_df(s1)
            tempdata<-tibble::as_tibble(s1)
            
            # Append data sets
            data<-bind_rows(data,tempdata)
            
            # Make a time break
            Sys.sleep(runif(1,3,10)) 
          }
        }
      }
    }

    # Save the data as csv file
    write.csv(data,NationReportCard.csv, row.names = FALSE)
