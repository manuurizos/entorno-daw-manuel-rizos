# Documentación de mi entorno de desarrollo · Práctica 2

**Nombre y apellidos:**
**URL de mi repositorio:**

> Rellena cada apartado a medida que avanzas. Donde pone «pega aquí», copia el texto
> de la terminal (no hace falta captura). Escribe con tus palabras: no se valora la longitud,
> sino que se note que entiendes lo que has hecho.

---

## 1. Instalación de entornos (CE 2.a)

### 1.1. Entorno vacío (paso 3)

Resultado de `java -version` y `node -v` **antes** de instalar nada:

```
@manuurizos ➜ /workspaces/entorno-daw-manuel-rizos (main) $ java -version
bash: java: command not found
@manuurizos ➜ /workspaces/entorno-daw-manuel-rizos (main) $ node -v
bash: node: command not found
```

¿Por qué crees que aparece ese mensaje? (relaciónalo con la diapositiva «Problemas habituales del entorno»)

porque el entorno utiliza una imagen base limpia y minima que todavia no tiene instalado ningun lenguage de programacion. 

> 

### 1.2. Después de la 1.ª reconstrucción (paso 5)

Resultado de `java -version`, `node -v` y `jupyter lab --version` **después**:

```
@manuurizos ➜ /workspaces/entorno-daw-manuel-rizos (main) $ java -version
openjdk version "27" 2026-09-15
OpenJDK Runtime Environment Temurin-27+35 (build 27+35)
OpenJDK 64-Bit Server VM Temurin-27+35 (build 27+35, mixed mode, sharing)
@manuurizos ➜ /workspaces/entorno-daw-manuel-rizos (main) $ node -v
v24.22.1
@manuurizos ➜ /workspaces/entorno-daw-manuel-rizos (main) $ jupyter lab --version
4.6.4
```

¿Qué líneas nuevas han aparecido en `devcontainer.json`? Explica con tus palabras qué hace cada una:

> 

### 1.3. Comparativa de los dos IDE (paso 6)

Aquí tienes la tabla completa y lista para copiar y pegar directamente en el apartado 1.3 de tu documento `docs/entorno.md`:

|  | Editor de GitHub Codespaces | JupyterLab |
| --- | --- | --- |
| **¿Libre o propietario?** | Propietario (desarrollado por GitHub, propiedad de Microsoft) | Libre (Open Source)

 |
| **Licencia / empresa o comunidad** | Privativa / Comercial (GitHub, Microsoft) | Licencia BSD de 3 cláusulas / Comunidad Project Jupyter |
| **¿Tiene coste? ¿Con qué límites?** | Modelo freemium; cuenta gratuita con límite mensual de horas (aprox. 60h en máquina básica) y pago por uso adicional

 | Gratuito y sin límites al ser de código abierto |
| **¿Se puede usar fuera de GitHub?** | No, está limitado exclusivamente al ecosistema de GitHub | Sí, se puede instalar y ejecutar localmente en cualquier ordenador o servidor independiente |
| **Lo que más me ha gustado** | Que no requiere instalación local y ofrece un entorno completo en la nube desde el navegador

 | Su interfaz interactiva y visual basada en pestañas en el navegador

 |
| **Lo que menos me ha gustado** | Los límites de tiempo de uso de la cuenta gratuita

 | Está más orientado a Python/datos y requiere configuración extra para otros lenguajes |
| **¿Para qué tipo de trabajo lo elegiría?** | Para desarrollo web ágil y programar desde cualquier equipo con navegador

 | Para análisis de datos, ciencia de datos o pruebas interactivas |
---

## 2. Módulos y extensiones (CE 2.b)

| Extensión | ¿Para qué sirve? | ¿Qué cambió al instalarla? | ¿La mantengo? ¿Por qué? |
|-----------|------------------|----------------------------|-------------------------|
| Extension Pack for Java |   |   |   |
| Code Spell Checker      |   |   |   |

¿Qué diferencia hay entre instalar una extensión **solo desde el panel** y añadirla **también a `devcontainer.json`**?

> 

---

## 3. Personalización y automatización (CE 2.c)

- **Tema visual elegido** (paso 10) y por qué: Light 2026, elegido por preferencia personal de contraste claro y para facilitar la lectura del código durante el día.
- **Ajuste del proyecto** (paso 10). ¿Qué archivo se ha creado y qué contiene?
## 3. Personalización y automatización (CE 2.c)

- **Ajuste del proyecto** (paso 10). ¿Qué archivo se ha creado y qué contiene?  
  Se ha creado el archivo `.vscode/settings.json`. y cotine lo de abajo

```
{
    "editor.formatOnSave": true
}
```

- **Atajo de teclado** (paso 11). ¿Qué acción, qué combinación y para qué te sirve? Acción: `Codespaces: Rebuild Container`.

Combinación: `Cmd + Shift + 8` (en Mac)
Sirve para reconstruir de manera rápida el entorno de desarrollo tras modificar los archivos de configuración, evitando navegar por los menús de VS Code.

- **Snippet** (paso 12). ¿Qué escribes y qué aparece?

  Escribo `cabecera` y al pulsar la tecla `Tab` o `Intro` aparece un bloque de comentario con mi nombre (Manuel Rizos), el nombre del archivo y la fecha actual.

- **Automatización al crear el entorno** (paso 14). ¿Qué hace `postCreateCommand` y qué archivos/carpetas han aparecido después de reconstruir?

Ejecuta automáticamente el comando `npm install` al inicializar el contenedor. Tras la reconstrucción han aparecido la carpeta `node_modules/` y el archivo `package-lock.json`.

- **Tareas** (paso 13). ¿Cuántas tareas hay en `tasks.json` y qué hace cada una?

Hay 3 tareas:
  1. **Java: compilar, empaquetar y ejecutar**: Compila con `javac`, empaqueta en `build/factura.jar` y ejecuta con `java -jar`.
  2. **TypeScript: compilar y ejecutar**: Ejecuta `npm run build` para compilar TypeScript a JavaScript y `npm start` para ejecutarlo con Node.js.
  3. **Build completo (Java + TypeScript)**: Ejecuta automáticamente en secuencia las dos tareas anteriores (`dependsOn`).


¿Qué parte de toda esta configuración es **personal** (solo para ti) y qué parte es **del proyecto** (la recibe cualquiera que abra el repositorio)?

El tema visual (*Color Theme*) y los atajos de teclado globales (`keybindings.json`), ya que quedan vinculados únicamente a las preferencias de tu cuenta de usuario en VS Code[cite: 1].
- **Del proyecto (para cualquiera que abra el repositorio):** Toda la carpeta `.vscode/` (`settings.json`, `tasks.json`, `daw.code-snippets`) y la carpeta `.devcontainer/` (`devcontainer.json`), ya que están guardadas y rastreadas en Git, por lo que se comparten con cualquiera que clone el proyecto.
> 

---

## 4. Ejecutables de diferentes lenguajes en el mismo entorno (CE 2.e)

Salida completa de la tarea **Build completo** (paso 15):  

```
 *  Ejecutando tarea: mkdir -p build/java && javac -d build/java src/java/Factura.java && jar --create --file build/factura.jar --main-class Factura -C build/java . && java -jar build/factura.jar 

=== FACTURA generada con Java 27 ===
Dominio web anual              12.00 EUR
Alojamiento web                59.90 EUR
Logotipo corporativo          150.00 EUR
-----------------------------------------
Base imponible                221.90 EUR
IVA (21 %)                     46.60 EUR
TOTAL                         268.50 EUR
 *  Las tareas reutilizarán el terminal, presione cualquier tecla para cerrarlo. 

 *  Ejecutando tarea: npm run build && npm start 


> plantilla-entorno-daw@1.0.0 build
> tsc


> plantilla-entorno-daw@1.0.0 start
> node dist/factura.js

=== FACTURA generada con Node.js v24.22.1 ===
Dominio web anual              12.00 EUR
Alojamiento web                59.90 EUR
Logotipo corporativo          150.00 EUR
-----------------------------------------
Base imponible                221.90 EUR
IVA (21 %)                     46.60 EUR
TOTAL                         268.50 EUR
 *  Las tareas reutilizarán el terminal, presione cualquier tecla para cerrarlo. 

```

| Lenguaje | Archivo fuente | Herramienta que lo traduce | Archivo generado | Cómo se ejecuta |
|----------|----------------|----------------------------|------------------|-----------------|
| Java       | `src/java/Factura.java` |   |   |   |
| TypeScript | `src/ts/factura.ts`     |   |   |   |

**Opcional:** ¿has podido ejecutar los mismos archivos desde JupyterLab (paso 19)? ¿Por qué funciona en los dos IDE sin instalar nada más?

> 

---

## 5. Sistema de actualizaciones (CE 2.d)

| Elemento | ¿Quién lo actualiza? | Modo (automático / manual / ninguno) | Qué he configurado yo |
|----------|----------------------|--------------------------------------|-----------------------|
| El editor de Codespaces |   |   |   |
| Las extensiones         |   |   |   |
| Java                    |   |   |   |
| Node.js                 |   |   |   |
| Dependencias npm (lodash, typescript…) |   |   |   |

Versión de Java **antes** (paso 5) y **después** (paso 18):

```
pega aquí
```

Resultado de `npm outdated` (paso 17):

```
pega aquí
```

Resultado de `npm audit` **antes** de actualizar lodash (solo el resumen final):

```
pega aquí
```

Resultado de `npm audit` **después**:

```
pega aquí
```

**Mi política de actualizaciones**: si este entorno lo usara un equipo de 5 personas durante todo el curso, ¿qué dejarías en automático y qué fijarías a mano? Justifícalo.

> 

---

## 6. Incidencias

Anota cualquier problema que hayas tenido y cómo lo resolviste (también si usaste un fragmento completo).

> 

## 7. Reflexión final

¿Qué ventaja tiene describir el entorno «como código» frente a instalar cada programa a mano en tu ordenador? Piensa en un equipo con Mac y Windows.

> 
