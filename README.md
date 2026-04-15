# Guia de Flujo de trabajo con GitFlow
---

## 1. Configuración Inicial **(Solo una vez)**
Si es la primera vez que descargas el proyecto:
1. **Clonar el repo:** `git clone [URL_DEL_REPO]`
2. **Entrar a la carpeta:** `cd [NOMBRE_DEL_PROYECTO]`
3. **Inicializar Git Flow:** `git flow init`  
   *(Presiona **Enter** a todas las preguntas para dejar los nombres por defecto).*

---

## 2. Flujo Diario de Trabajo (Paso a Paso)

### Paso 1: Actualizar tu PC
Antes de empezar cualquier tarea, asegúrate de tener lo último que hicieron tus compañeros:
```bash
git checkout develop
git pull origin develop
```

### Paso 2: Crear una rama para tu tarea
Nunca trabajes sobre `develop` directamente. Crea una rama específica:
```bash
git flow feature start nombre-de-tu-tarea
```
Ejemplo: `git flow feature start login-usuario`

### Paso 3: Programar y guardar cambios
Trabaja en tu código y haz commits frecuentes con mensajes claros:

```bash
git add .
git commit -m "feat: descripción de lo que hiciste"
```
Nomenclaturas de un commit:
1. `"feat: descripcion del commit"` --> cuando se añade nuevas caracteristicas o funcionalidades.
2. `"fix: descripcion del commit"`  --> cuando se corrrige errores o bugs
3. `"docs: descripcion del commit"`  --> cuando se corrige algo de la docuemntacion
4. `"style: descripcion del commit"`  --> cuando se hace cambios en los estilos q no afectan el comportamiento del codigo

### Paso 4: Subir tu avance a GitHub
Para que el `Administrador` pueda revisar tu código, sube tu rama al servidor (es como hacer un git push):
```bash
git flow feature publish nombre-de-tu-tarea
```

### Paso 5: Abrir el Pull Request (PR)
1. Ve a la página del repositorio en GitHub.
2. Haz clic en el botón "Compare & pull request".
3. **IMPORTANTE:** Verifica que la base sea develop (Base: develop ← Compare: feature/tu-tarea).
4. Describe brevemente qué cambiaste y espera la revisión del `Administrador`.

## 🛑 Solo se usa esto si no se aprobo tu cambios o hay errores que se tienen que corregir 
### Paso 6: Correcciones (Solo si es necesario ya que no se aprobo tus cambios)
Si el `Adminitrador` deja comentarios con correcciones, haz los cambios en tu misma rama, guarda y vuelve a subir:
```bash
git add .
git commit -m "fix: corrección según revisión"
git push
```
## ✅ Si tus cambios fueron aprobados y el Admin hizo merge realizas esto
### Paso 7: Limpieza Local 
Una vez que el `Adminitrador` apruebe y haga el Merge en GitHub, tú debes limpiar tu PC y borrar tu rama:
```bash
git checkout develop
git pull origin develop
git branch -d feature/nombre-de-tu-tarea
```
