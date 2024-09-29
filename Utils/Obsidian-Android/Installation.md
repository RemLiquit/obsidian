
# Install Termux from PlayStore

Para clonar un repositorio de GitHub en Termux y almacenarlo en el directorio principal de Android, sigue estos pasos:

1. **Acceso a Almacenamiento**: Termux no tiene acceso directo a `/sdcard`. Debes crear un enlace simbólico:bash
```
termux-setup-storage
```
 
2. **Instala Git**: Asegúrate de que Git esté instalado:bash

```
pkg update && pkg install git
```

3. **Genera clave ssh**: 

[[Create SSH]]

La ubicación para la clave ssh tiene que ser

```
/storage/emulated/0/ssh/
```

4. **Clonar Repositorio**:
```
Git clone "repo"
```