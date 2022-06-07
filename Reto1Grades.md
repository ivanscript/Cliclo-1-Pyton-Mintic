# Cliclo-1-Pyton-Mintic
Solving some challenges in Python
nota = float(0)
porcentaje_notas = 0
sumat_porcentajes = 0
faltan_notas = "S"
nota_acumulada = float(0)

print("¡Bienvenido! En esta aplicación los estudiantes podrán gestionar las notas de su materia.")

nombre = input("Por favor ingrese su nombre: ").capitalize()
materia = input("Ingrese el nombre de la materia: ").capitalize()

while faltan_notas == "S" and sumat_porcentajes != 1:
    nota = float(input("Ingrese la nota obtenida: "))
    porcentaje_nota = int(input("Ingrese el porcentaje de la nota: "))
    sumat_porcentajes += porcentaje_nota/100
    nota_acumulada += nota*porcentaje_nota/100   
    if (sumat_porcentajes < 1):
        falta = input("¿Falta añadir notas? S/N ").upper() #hasta aquí va el bucle infinito, siempre lleva a agregar nota y porcentaje nota
    if sumat_porcentajes > 1:
        print("El porcentaje evaluado de una materia no puede ser mayor a 100")
        sumat_porcentajes -= porcentaje_nota/100
        nota_acumulada -= nota*porcentaje_nota/100
        nota = float(input("Ingrese la nota obtenida: "))
        porcentaje_nota = int(input("Ingrese el porcentaje de la nota: "))
        sumat_porcentajes += porcentaje_nota/100
        nota_acumulada += nota*porcentaje_nota/100
        if(sumat_porcentajes == 1 and nota_acumulada >= 3):
            print(f"el estudiante %s cursó la materia %s y obtuvo %.2f resultado en desaprobado resultado en aprobado"%(nombre, materia, nota_acumulada))
        if(sumat_porcentajes == 1 and nota_acumulada < 3):
            print(f"el estudiante %s cursó la materia %s y obtuvo %.2f resultado en desaprobado resultado en reprobado"%(nombre, materia, nota_acumulada))
    else:
        if faltan_notas == "N":
           if(nota_acumulada >= 3):
               print(f"El estudiante {nombre} cursó la materia {materia} y obtuvo {nota_acumulada} resultando en aprobado")
        else:
            print(f"El estudiante {nombre} cursó la materia {materia} y obtuvo {nota_acumulada} resultando en reprobado")
