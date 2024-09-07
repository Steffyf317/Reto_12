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
2.Extraer la cantidad de vocales y consonantes del archivo
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
