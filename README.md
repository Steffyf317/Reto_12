# Reto 12: Strings
### Elaborado por Steffy Geraldine Fernández González
1. Métodos de strings en python:
## endswith
### Verifica que una cadena termine con un carácter indicado y retorna un booleano, por ejemplo:
```python
cadena = "Hello World."
x = cadena.endswith(".")
print(x)
```

## startswith
### Verifica que una cadena inicie con un carácter indicado:
```python
cadena = "Hello World."
x = cadena.startswith("H")
print(x)
```

## isalpha
### Verifica que todo lo que esté en el string sean letras:
```python
cadena = "Hello World."
x = cadena.isalpha()
print(x)
```

## isalnum
### Verifica que todo lo que esté en el string sea alfanumérico:
```python
txt = "Company12"
x = txt.isalnum()
print(x)
```
## isdigit
### Verifica que todo en el string sean dígitos:
```python
txt = "50800"
x = txt.isdigit()
print(x)
```
## isspace
### Verifica que todo en el string sean espacios en blanco:
```python
txt = "   "
x = txt.isspace()
print(x)
```
## istitle
### Verifica que cada palabra en el string inicie con mayúscula:
```python
txt = "Hello, And Welcome To My World!"
x = txt.istitle()
print(x)
```
## islower
### Verifica que todo en el string esté en minúscula:
```python
txt = "hello world!"
x = txt.islower()
print(x)
```
## isupper
### Verifica que todo el string esté en mayúscula:
```python
txt = "THIS IS NOW!"
x = txt.isupper()
print(x)
```
(Ejemplos extraídos de https://www.w3schools.com/)

2. Extraer la cantidad de vocales y consonantes del archivo (.txt disponible en los files del repo)
```python
def contar_vocales_y_consonantes(texto:str):
  vocales = "aeiouAEIOU"
  consonantes = "bcdfghjklmnpqrstvwxyzBCDFGHJKLMNPQRSTVWXYZ" #se hacen las cadenas con minusculas y mayusculas
  
  numero_vocales = 0 #se inician los contadores
  numero_consonantes = 0

  for chr in texto: # para cada caracter dentro del texto
    if chr in vocales: #si el caracter esta en las cadenas anteriormente especificadas, hacer:
      numero_vocales +=1
    elif chr in consonantes:
      numero_consonantes +=1

  return(numero_vocales,numero_consonantes) 
   

if __name__ == '__main__':
  file = open('archivotexto.txt') #abrir el archivo .txt
  texto = file.read() #leer el archivo de texto
  vocales_y_consonantes_contadas = contar_vocales_y_consonantes(texto) #llamar a la funcion 
  print("El número de vocales y consonantes encontradas en el archivo son respectivamente " +str(vocales_y_consonantes_contadas))
```
Listado de las 50 palabras que más se repiten
```python
# Función que extrae las palabras del texto
def separar_palabras(texto):
  palabras = []
  palabra = ""
  # Recorre cada caracter del texto
  for chr in texto:
    # Cuando haya un caracter que no se una letra y se haya formado una palabra se agrega para luego formar la siguiente
    if not(chr.isalpha()) and len(palabra) > 0:
      palabras.append(palabra)
      palabra = ""
    # Se forma la palabra si es una letra
    if chr.isalpha():
      palabra += chr
  return palabras

# La función devuelve los n primeros elementos del arreglo
def tomar_elementos(arreglo, n):
  elementos = []
  for i in range(n):
    elementos.append(arreglo[i])
  return elementos

def listado_cincuenta_repetidas(texto):
  # Diccionario en donde se agregan las palabras repetidas
  repetidas = {}
  # Se pasa el texto a lowercase para evitar que hayan diferencias por las mayúsculas
  texto_min = texto.lower()
  # Extraer la palabras del texto
  palabras = separar_palabras(texto_min)
  for palabra_actual in palabras:
    # Si la palabra actual de la iteración no está en el diccionario, se inicializa su contador en 1. Si ya esta, se va aumentando el contador
    if palabra_actual in repetidas:
      repetidas[palabra_actual] += 1
    else:
      repetidas[palabra_actual] = 1
  listado_palabras = list(dict(sorted(repetidas.items(), key=lambda item: item[1], reverse=True)).keys()) # Ordena los elementos del diccionario en orden descendente y se toman las keys, que son la palabras repetidas, para convertirlos en una lista
  return tomar_elementos(listado_palabras, 50) # Devuelve las 50 palabras más repetidas


if __name__ == "__main__":
  file = open("archivotexto.txt")
  texto = file.read()
  repetidas = listado_cincuenta_repetidas(texto)
  print(repetidas)
```
