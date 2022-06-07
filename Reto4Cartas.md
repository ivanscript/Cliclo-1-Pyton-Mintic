# Cliclo-1-Pyton-Mintic
Solving some challenges in Python
def tiene_cartas_altas(cartas_siguientes):
    # ACÁ INICIA LA FUNCIÓN
    for K in cartas_siguientes:
        if K in 'AJQK':
            return True
    return False 
    
    
    # ACÁ TERMINA LA FUNCIÓN
    # ESTA VEZ TU DEFINES TUS RETORNOS

def juego(baraja):
    # ACÁ INICIA LA FUNCIÓN
    N_cartas = len(baraja)
    jugador_actual = 'jugador1'
    puntaje_jugador1 = 0
    puntaje_jugador2 = 0

    for i,j in enumerate(baraja):
        puntos = 0
        n_cartas_restantes = N_cartas - i - 1
        if j == 'A' and n_cartas_restantes >= 1 and not (tiene_cartas_altas(baraja[i+1])):
            puntos = 1
        elif j == 'J' and n_cartas_restantes >= 2 and not (tiene_cartas_altas(baraja[i+1:i+3])):
            puntos = 2
        elif j == 'Q' and n_cartas_restantes >= 3 and not (tiene_cartas_altas(baraja[i+1:i+4])):
            puntos = 3
        elif j == 'K' and n_cartas_restantes >= 4 and not (tiene_cartas_altas(baraja[i+1:i+5])):
            puntos = 4
    
        if jugador_actual == 'jugador1':
            puntaje_jugador1 += puntos
            jugador_actual = 'jugador2'
        else:
            puntaje_jugador2 += puntos
            jugador_actual = 'jugador1'

    return puntaje_jugador1, puntaje_jugador2
