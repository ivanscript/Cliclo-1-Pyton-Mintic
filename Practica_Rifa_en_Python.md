# Cliclo-1-Pyton-Mintic
Solving some challenges in Python
print("¡¡¡Bienvenidos a esta rifa!!!")
print()
limite_inferior = 0
limite_superior = 33
numero_ganador = 23
intentos = 0
ingreso = "S"
print(f"Advina un número entre {limite_inferior} y {limite_superior}")
print()
while ingreso == "S":
    numero_usuario = int(input("Ingrese un número que esté dentro del intervalo mencionado: "))
    intentos += 1
    if(numero_usuario < limite_inferior) or (numero_usuario > limite_superior):
        print("Su número no está en el intervalo")
        print()
    else:
        if numero_usuario < numero_ganador:
            print("¡Te faltó!")
        elif numero_usuario > numero_ganador:
            print("¡Te pasaste!")
        elif numero_usuario == numero_ganador:
            break       

print(f"Adivinaste, el número ganador es {numero_ganador} y fue adivinado a los {intentos} intentos ")
