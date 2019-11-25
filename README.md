# utl-count-no-of-obs-from-multiple-datasets
Count no of obs from multiple datasets
    SAS Forum: Count no of obs from multiple datasets                                                              
                                                                                                                   
     Prefered solution                                                    
                                                                         
    Keintz, Mark                                                         
    mkeintz@wharton.upenn.edu                                            
                                                                         
    data a b c d e f g h I j k l m n o p q r s t u v w x y z;            
      set sashelp.class;                                                 
    run;                                                                 
                                                                         
    data _null_;                                                         
      set a b c d e f g h I j k l m n o p q r s t u v w x y z nobs=nall; 
      put nall=;                                                         
      stop;                                                              
    run;                                                                 
                                                                         
    NALL=494                                                             
                                                                                                                 
    As a side note count(*) gets the mumber of obs from metat adta                                                                                                              
    SAS Forum                                                                                                      
    https://tinyurl.com/smze67n                                                                                    
    https://communities.sas.com/t5/SAS-Programming/Count-no-of-obs-from-multiple-datasets/m-p/606885               
                                                                                                                   
    macros                                                                                                         
    https://tinyurl.com/y9nfugth                                                                                   
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                     
                                                                                                                   
    Macro variable 'letters' is defined in my aut                                                                  
                                                                                                                   
    LETTERS=A B C D E F G H I J K L M N O P Q R S T U V W X Y Z                                                    
    *_                   _                                                                                         
    (_)_ __  _ __  _   _| |_                                                                                       
    | | '_ \| '_ \| | | | __|                                                                                      
    | | | | | |_) | |_| | |_                                                                                       
    |_|_| |_| .__/ \__,_|\__|                                                                                      
            |_|                                                                                                    
    ;                                                                                                              
    %array(ltrs,values=&letters);                                                                                  
                                                                                                                   
    data &letters;                                                                                                 
     set sashelp.class;                                                                                            
    run;quit;                                                                                                      
                                                                                                                   
    data set WORK.A has 19 observations and 5 variables                                                            
    data set WORK.B has 19 observations and 5 variables                                                            
    data set WORK.C has 19 observations and 5 variables                                                            
    data set WORK.D has 19 observations and 5 variables                                                            
    data set WORK.E has 19 observations and 5 variables                                                            
    data set WORK.F has 19 observations and 5 variables                                                            
    data set WORK.G has 19 observations and 5 variables                                                            
    data set WORK.H has 19 observations and 5 variables                                                            
    data set WORK.I has 19 observations and 5 variables                                                            
    data set WORK.J has 19 observations and 5 variables                                                            
    data set WORK.K has 19 observations and 5 variables                                                            
    data set WORK.L has 19 observations and 5 variables                                                            
    data set WORK.M has 19 observations and 5 variables                                                            
    data set WORK.N has 19 observations and 5 variables                                                            
    data set WORK.O has 19 observations and 5 variables                                                            
    data set WORK.P has 19 observations and 5 variables                                                            
    data set WORK.Q has 19 observations and 5 variables                                                            
    data set WORK.R has 19 observations and 5 variables                                                            
    data set WORK.S has 19 observations and 5 variables                                                            
    data set WORK.T has 19 observations and 5 variables                                                            
    data set WORK.U has 19 observations and 5 variables                                                            
    data set WORK.V has 19 observations and 5 variables                                                            
    data set WORK.W has 19 observations and 5 variables                                                            
    data set WORK.X has 19 observations and 5 variables                                                            
    data set WORK.Y has 19 observations and 5 variables                                                            
    data set WORK.Z has 19 observations and 5 variables                                                            
                                                                                                                   
    *            _               _                                                                                 
      ___  _   _| |_ _ __  _   _| |_                                                                               
     / _ \| | | | __| '_ \| | | | __|                                                                              
    | (_) | |_| | |_| |_) | |_| | |_                                                                               
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                              
                    |_|                                                                                            
    ;                                                                                                              
                                                                                                                   
                                                                                                                   
    ----------------------------------------------------                                                           
    Sum of obs in all 26 tables is 26*19 = 494       494                                                           
                                                                                                                   
    *                                                                                                              
     _ __  _ __ ___   ___ ___  ___ ___                                                                             
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                            
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                            
    | .__/|_|  \___/ \___\___||___/___/                                                                            
    |_|                                                                                                            
    ;                                                                                                              
                                                                                                                   
                                                                                                                   
    * very fast on muti-core multi-channel systems like teradata;                                                  
                                                                                                                   
    proc sql;                                                                                                      
      select                                                                                                       
         "Sum of obs in all 26 tables is 26*19 = 494"                                                              
         ,sum(cnt)                                                                                                 
      from                                                                                                         
        ( %do_over(ltrs,phrase=select count(*) as cnt from ?, between=union all corr) )                            
    ;quit;                                                                                                         
                                                                                                                   
                                                                                                                   
                                                                                                                   
