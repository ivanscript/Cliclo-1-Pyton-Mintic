# Cliclo-1-Pyton-Mintic
Solving some challenges in Python
#NO ELIMINAR LAS SIGUIENTES IMPORTACIONES, sirven para el funcionamiento de las librería csv y json respectivamente
import csv, json
"""NOTAS: 
    - PARA ESTE RETO PUEDES PROBAR TU PROGRAMA, DANDO CLICK EN LA NAVE ESPACIAL
    - LA CONSOLA TE DIRÁ SI TU SOLUCIÓN ES CORRECTA O NO
    - NO olvidar evaluar tu solución
"""


"""Inicio espacio para programar funciones propias"""
#En este espacio podrás programar las funciones que deseas usar en la función solución (ES OPCIONAL)



"""Fin espacio para programar funciones propias"""

def solucion():
    #ESTA ES LA FUNCIÓN A LA QUE LE DEBES GARANTIZAR LOS RETORNOS REQUERIDOS EN EL ENUNCIADO.
    
    archivo=open('GLOBANT.csv')
    x=csv.reader(archivo)
    Date=[]
    Open=[]
    High=[]
    Low=[]
    Close=[]
    Adj_close=[]
    Volume=[]
    
    next(x,None)
    for columna in x:
      Date.append(columna[0])
      Open.append(float(columna[1]))
      High.append(float(columna[2]))
      Low.append(float(columna[3]))
      Close.append(float(columna[4]))
      Adj_close.append(float(columna[5]))
      Volume.append(int(columna[6]))   
    
    archivo.close()
    comportamiento=[]
    media=[]
    k=0
    j=0
    m=0
    for i in range(len(Open)):
      resta=Close[i]-Open[i]
      media.append(0.5*(High[i]-Low[i]))
      if resta>0:
         comportamiento.append('SUBE')
         k=k+1
      elif resta<0:
         comportamiento.append('BAJA')
         j=j+1
      elif resta==0:
         comportamiento.append('ESTABLE')
         m=m+1
    
    #Creación de archivo CSV
    with open('analisis_archivo.csv','w') as file:
      file.write('Fecha\tComportamiento de la accion\tPunto medio HIGH-LOW\n')
    
      for i in range(len(Date)):
         file.write('%s\t' % Date[i])
         file.write('%s\t' % comportamiento[i])
         file.write('%s\n' % media[i])
      file.close()
    #Creación de archivo JSON
    data={}
    lowest=min(Low)
    highest=max(High)
    for i in range(len(Date)):
      if lowest==Low[i]:
         data['date_lowest_price']=Date[i]
         data['lowest_price']=Low[i]
      if highest==High[i]:
         data['date_highest_price']=Date[i]
         data['highest_price']=High[i]
    
    data['cantidad_veces_sube']=k
    data['cantidad_veces_baja']=j
    data['cantidad_veces_estable']=m
    
    with open('detalles.json','w') as file:
      json.dump(data,file)
solucion()
