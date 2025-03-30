# Fundamentos del ***Cifrado César***

1. Se basa en Sumas

2. es un cifrado de ***Sustitución***

#### Resumen de pasos para su uso (*Cifrado*):

1. Elegimos una Contraseña `k`, que sera un número del 0 al 26

2. convertimos las letras de nuestro mensaje en números según su posición en el alfabeto

3. sumamos `k` a todos los números

4. efectuamos módulo 27 sobre todos los números

5. convertimos los números en letras

#### Resumen de pasos para su uso 3 (Descifrado):

1. usaremos nuestra contraseña `k` para descifrarlo

2. convertimos las letras del mensaje cifrado a números

3. restamos a todos los números de nuestro mensaje cifrado `k`

4. le sumamos 27 a cada número

5. les hacemos módulo 27

#### En Programación

python

```py
# Python Version

abc = "abcdefghijklmnñopqrstuvwxyz"
k = 13 # esto es la contraseña
mensaje = "Jacobo es mujer"

def cesar(mensaje, clave, opcion):
    formateado = mensaje.lower() # hacemos que el texto sea todo minusculas
    texto_cifrado = ""
    for ch in formateado:
        if ch in abc:
            coded = abc.index(ch)
            if opcion=="encrypt":
                cifred = (coded + k) % 27
            elif opcion=="decrypt":
                cifred = (coded - k + 27) % 27
            texto_cifrado += abc[cifred]
                
        else:
            texto_cifrado += ch
    return texto_cifrado
    
cifrado = cesar(mensaje, k, "encrypt") # usando la opción encypt para encriptar
print("Texto Cifrado: " + cifrado)
descifrado = cesar(cifrado, k, "decrypt") #decrypt para desencriptar el mensaje
print("Texto Descifrado: " + descifrado)

```

```c
// C version
// esta versión es más simple, pues no hay tanta facilidad para hacer
//la gran diferencia es que aquí usamos todo el ASCII como alfabeto

void cesar(char *text, unsigned int len, unsigned int clave, unsigned char mode) {
    for (int i=0; i<len; i++) {
        if (mode==0) {
            text[i]+=clave;
        } else if (mode==1) {
            text[i]-=clave;
        }
    }
}
//no uso return porque trabajo con punteros


```

```js
//Version de javascript tengo que hacerla
```

Bueno, esos eran los apuntes, añadire la versión en java-script