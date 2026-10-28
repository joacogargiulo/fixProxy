# 🛠️ fixProxy

**fixProxy** es una herramienta para **resolver problemas de navegación en Windows** causados por configuraciones de proxy globales.  Básicamente soluciona el problema de proxy que provoca que en el navegador te aparezca el error de *Sin internet* o *No se puede acceder a este sitio*
Al ejecutarlo, establece en el Registro:

HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\CurrentVersion\Internet Settings\ProxySettingsPerUser

el valor **1**, habilitando la **configuración de proxy por usuario**.  
Esto suele arreglar casos en los que algunas páginas no cargan o cargan de forma intermitente.

---

## 🚀 Descarga rápida (EXE listo)

➡️ **Descargar la última versión (.exe):**  
https://github.com/joacogargiulo/fixProxy/releases/latest/download/fixProxy.exe


---

## 🖥️ Cómo usarlo

1. **Descargá** el `.exe` desde el enlace anterior.
2. **Abrí** el archivo con doble clic.
3. **Aceptá** el aviso de Windows para ejecutar como **Administrador**.
4. Listo ✅:
   - Si ya estaba en `1`, te lo informa y no cambia nada.
   - Si estaba en `0` o no existía, lo crea/cambia a `1`.

**Modo silencioso (opcional):**

    pruebaProxy.exe /silent

(No muestra ventanas; imprime mensajes en consola).

---

## ⚡ Características

- Corrige automáticamente `ProxySettingsPerUser` → `1`
- Detecta si ya estaba configurado
- Compatible con Windows 7, 8, 10 y 11
- No requiere instalación
- Código abierto

---

## 🔧 Compilar desde el código fuente

### Opción A — MinGW clásico (con manifest embebido)

1) Asegurate de tener estos archivos en `src/`:
- `pruebaProxy.c`
- `pruebaProxy.exe.manifest` (contenido XML del manifest UAC)
- `resource.rc` con el contenido:
  
      1 RT_MANIFEST "pruebaProxy.exe.manifest"

2) Compilá (desde CMD):

    windres src\resource.rc -o src\resource.o
    gcc -O2 -Wall src\pruebaProxy.c src\resource.o -o dist\pruebaProxy.exe

> Si `windres` no está en tu PATH, usá su ruta completa (por ejemplo, `C:\MinGW\bin\windres`).

### Opción B — MinGW-w64 (recomendado)

    x86_64-w64-mingw32-gcc -O2 -Wall -municode src\pruebaProxy.c -o dist\pruebaProxy.exe

> En ambos casos, el ejecutable resultante pedirá permisos de **Administrador** (por el manifest embebido o side-by-side).

## 📄 Licencia

Este proyecto está bajo la licencia **MIT**.

    MIT License

    Copyright (c) 2025 Joacogargiulo

    Permission is hereby granted, free of charge, to any person obtaining a copy
    of this software and associated documentation files (the "Software"), to deal
    in the Software without restriction, including without limitation the rights
    to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
    copies of the Software, and to permit persons to whom the Software is
    furnished to do so, subject to the following conditions:

    The above copyright notice and this permission notice shall be included in all
    copies or substantial portions of the Software.

    THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
    IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
    FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
    AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
    LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
    OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
    SOFTWARE.

---

## 🔗 Enlaces útiles

- Repo: https://github.com/joacogargiulo/fixProxy
- Descarga directa última versión:  
  https://github.com/joacogargiulo/fixProxy/releases/latest/download/fixProxy.exe
