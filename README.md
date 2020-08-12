# MSc-Project


import re

with open("C:\\Users\\maham_000\\OneDrive\\bioinformatics\\MSc Project\\TXT\\LUZY.txt","r") as f:
    string = f.read()

#Splitting at | and -
result = string.split("|")
print(result[0])

y = result[0].split("-")
print(y[0])


for i in range(len(y)):
    print(y[i])

#Domain validity    
    Domain = '^(VL|CL|VH|CH1|H|CH2|CH3|CH4|L|X)'
    domainmatch = re.match(Domain,y[i], re.IGNORECASE)
    
    if domainmatch:
        print('Valid Domains')
    else:
        print('Invalid Domains')
        
    
#specificity validity  
    specificity = '(VL\D|VH\D|)'
    specificitymatch =  re.search(specificity,y[i], re.IGNORECASE)
    
    if specificitymatch:
          print('Valid Specificity')
          
    else:
        print('Invalid Specificity')
        
      
#Id and intercation validity       
    id_interaction = '(\([1-9][0-9]?|100)\W([1-9][0-9]?|100+)\)*'
    id_only = '(\([1-9][0-9]?|100)\)'
    idmatch =  re.compile('(%s|%s)' % (id_interaction,id_only)).findall(y[i])
    
    if idmatch:
          print('Valid Identifier or Valid Identifier and interaction(s)')
          
    else :
          print('Invalid Identifier or invalid Identifier and interaction(s)')                                                                                                                                                      
