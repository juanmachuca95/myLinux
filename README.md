### Enlaces útiles: 
Comandos de linux: https://ciberninjas.com/chuleta-comandos-linux/

### Cuando no queremos mostrar errores por consola, podemos rederigir el error mediante (stderr 2>) y enviarlos a /dev/null
```zsh
# vemos el error
whoam

# no vemos el error
whoam 2>/dev/null
```

### Una forma de ocultar la salida (stdout o output de la consola) incluyendo el stderr:
```zsh
cat /etc/host &>/dev/null

#o forma larga: el 2>$1 estamos diciendo que el stderr lo convertimos en stdout 

cat /etc/host > /dev/null 2>&1 

#O forma corta 
cat /etc/host &> /dev/null

#En el caso de que queramos ocultar un proceso hijo de un programa para seguir trabajando en la consola. Ejemplo:
wireshark &>/dev/null &

#Esta manera de ejecutar el programa hará que el programa dependa de la vida de la consola
#Por lo que una manera de independizar el proceso en segundo plano de la consola seria usa "disown"
```
 
### Descripctores de archivo 
```zsh
exec 8> descriptores_de_archivo.txt; whoami >8& 

echo "Hola Juan, estás usando descriptores de archivos?" >8&

cat descriptores_de_archivos.txt
# hackiehacky
# Hola Juan, estás usando descriptores de archivos? 
```

Eliminamos descriptores ```exec >&8-``` y si luego intentamos escribir de nuevo fallará

