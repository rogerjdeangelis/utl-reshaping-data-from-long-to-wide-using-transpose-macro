# utl-reshaping-data-from-long-to-wide-using-transpose-macro
Reshaping data from long to wide using-transpose-macro   
    Reshaping data from long to wide using transpose macro                                                     
                                                                                                               
     Problem                                                                                                   
         Transpose  variables FEE PROC PD CT  by CLM DOS FEE                                                   
         One liner                                                                                             
         %utl_transpose(data=havkey, out=want, by=clm dos fee, delimiter=_, var=proc pd ct);                   
                                                                                                               
    SAS Proc Transpose cannot transpose multiple sets of variables                                             
                                                                                                               
    Use Art's fast and flexible transpose macro                                                                
    AUTHORS: Arthur Tabachneck, Xia Ke Shan, Robert Virgile and Joe Whitehurst                                 
                                                                                                               
    filename tr url "https://raw.githubusercontent.com/art297/transpose/master/transpose.sas";                 
                                                                                                               
                                                                                                               
    GitHub                                                                                                     
    https://cutt.ly/xgF42ld                                                                                    
    https://github.com/rogerjdeangelis/utl-reshaping-data-from-long-to-wide-using-transpose-macro              
                                                                                                               
    macros                                                                                                     
    https://tinyurl.com/y9nfugth                                                                               
    https://github.com/rogerjdeangelis/utl-macros-used-in-many-of-rogerjdeangelis-repositories                 
                                                                                                               
    https://cutt.ly/JgF9SDn                                                                                    
    https://communities.sas.com/t5/SAS-Programming/Reshaping-data-from-long-to-wide/m-p/696708                 
                                                                                                               
                                                                                                               
    *                                                                                                          
    #####  #   #  ####   #   #  #####                                                                          
      #    ##  #  #   #  #   #    #                                                                            
      #    # # #  #   #  #   #    #                                                                            
      #    #  ##  ####   #   #    #                                                                            
      #    #   #  #      #   #    #                                                                            
      #    #   #  #      #   #    #                                                                            
    #####  #   #  #       ###     #                                                                            
    ;                                                                                                          
                                                                                                               
    data have;                                                                                                 
     input CLM DOS FEE PROC$ PD CT;                                                                            
    cards4;                                                                                                    
    1 1 9 A 3 1                                                                                                
    2 1 10 B 3 4                                                                                               
    2 2 11 B 1 6                                                                                               
    2 2 11 C 4 3                                                                                               
    3 1 12 A 4 8                                                                                               
    3 1 12 B 8 5                                                                                               
    3 2 13 A 5 1                                                                                               
    3 2 13 C 6 4                                                                                               
    3 3 14 B 3 3                                                                                               
    ;;;;                                                                                                       
    run;quit;                                                                                                  
                                                                                                               
    Up to 40 obs WORK.HAVE total obs=9                                                                         
                                                                                                               
     CLM    DOS    FEE    PROC    PD    CT                                                                     
                                                                                                               
      1      1       9     A       3     1                                                                     
      2      1      10     B       3     4                                                                     
      2      2      11     B       1     6                                                                     
      2      2      11     C       4     3                                                                     
      3      1      12     A       4     8                                                                     
      3      1      12     B       8     5                                                                     
      3      2      13     A       5     1                                                                     
      3      2      13     C       6     4                                                                     
      3      3      14     B       3     3                                                                     
                                                                                                               
    *                                                                                                          
     ###   #   #  #####  ####   #   #  #####                                                                   
    #   #  #   #    #    #   #  #   #    #                                                                     
    #   #  #   #    #    #   #  #   #    #                                                                     
    #   #  #   #    #    ####   #   #    #                                                                     
    #   #  #   #    #    #      #   #    #                                                                     
    #   #  #   #    #    #      #   #    #                                                                     
     ###    ###     #    #       ###     #                                                                     
    ;                                                                                                          
                                                                                                               
     WORK.WANT total obs=6                                                                                     
                                                                                                               
      CLM    DOS    FEE    PROC_1    PD_1    CT_1    PROC_2    PD_2    CT_2                                    
                                                                                                               
       1      1       9      A         3       1                 .       .                                     
       2      1      10      B         3       4                 .       .                                     
       2      2      11      B         1       6       C         4       3                                     
       3      1      12      A         4       8       B         8       5                                     
       3      2      13      A         5       1       C         6       4                                     
       3      3      14      B         3       3                 .       .                                     
                                                                                                               
    *                                                                                                          
    ####   ####    ###    ###   #####   ###    ###                                                             
    #   #  #   #  #   #  #   #  #      #   #  #   #                                                            
    #   #  #   #  #   #  #      #       #      #                                                               
    ####   ####   #   #  #      ####     #      #                                                              
    #      # #    #   #  #      #         #      #                                                             
    #      #  #   #   #  #   #  #      #   #  #   #                                                            
    #      #   #   ###    ###   #####   ###    ###                                                             
                                                                                                               
    proc datasets lib=work nolist;                                                                             
      delete want;                                                                                             
    run;quit;                                                                                                  
                                                                                                               
    %utl_transpose(data=havkey, out=want, by=clm dos fee, delimiter=_, var=proc pd ct);                        
                                                                                                               
                                                                                                               
                                                                                                               
                                                                                                               
