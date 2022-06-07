# Cliclo-1-Pyton-Mintic
Solving some challenges in Python
nombres = ["Martín", "Milú", "Anastasia", "Lupita", "Tomasa", "Pelusa", "Genoveva", "Motita"]
tipos = ["canino", "canino", "felino", "felino", "felino", "canino", "bovino", "roedor"]
edades = [12, 9, 10, 8, 9, 2, 14, 1]
pesos = [33, 26, 4, 5, 5, 6, 106.4, 0.34]


diccionario, beneficiarios_can_fel, beneficiarios_equ_bov, promedio_can_fel, promedio_equ_bov = ({}, {}, {}, 0, 0)
k,j = (0,0)
sumat_edades_can_fel, sumat_edades_equ_bov = (0,0)

for i in range(0,len(nombres)):      
    diccionario[str(i+1)] = [nombres[i], tipos[i], edades[i], pesos[i]]

for i in range(0,len(nombres)):
    if((tipos[i] == "felino" or tipos[i] == "canino") and edades[i] >= 9):
        j += 1
        beneficiarios_can_fel[str(j)] = [nombres[i], tipos[i], pesos[i]]
        sumat_edades_can_fel += edades[i]

for i in range(0,len(nombres)):
    if((tipos[i] == "bovino" or tipos[i] == "equino") and edades[i] >= 16):
        k += 1
        beneficiarios_equ_bov[str(k)] = [nombres[i], tipos[i], pesos[i]]
        sumat_edades_equ_bov += edades[i] 
#Promedio edad caninos-felinos que cumplen los requicitos para entrar al programa
if len(beneficiarios_can_fel) != 0:
    promedio_can_fel = sumat_edades_can_fel/len(beneficiarios_can_fel)
else:
    promedio_can_fel = None

if len(beneficiarios_equ_bov) != 0:
    promedio_equ_bov = sumat_edades_equ_bov/len(beneficiarios_equ_bov)  
else:
    promedio_equ_bov = None
