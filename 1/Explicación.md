Perfecto, vamos a organizarlo bien para que quede claro y útil en clase:

---

## **Ejemplos de cada lenguaje de marcas mencionado**

### **1. HTML (HyperText Markup Language)**

**Ejemplo:**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Ejemplo HTML</title>
  </head>
  <body>
    <h1>Hola Mundo</h1>
    <p>Este es un párrafo dentro de una página web.</p>
  </body>
</html>
```

**Entorno de uso:** Navegadores web. Es el estándar principal para estructurar el contenido de páginas web.

---

### **2. XML (eXtensible Markup Language)**

**Ejemplo:**

```xml
<alumno id="1">
  <nombre>Ana</nombre>
  <curso>DAM</curso>
  <nota>9.5</nota>
</alumno>
```

**Entorno de uso:** Intercambio de datos entre sistemas, archivos de configuración, almacenamiento estructurado de información (ej. RSS, SOAP, documentos técnicos).

---

### **3. SVG (Scalable Vector Graphics)**

**Ejemplo:**

```svg
<svg width="200" height="200">
  <circle cx="100" cy="100" r="80" fill="lightblue" stroke="black" stroke-width="3"/>
</svg>
```

**Entorno de uso:** Gráficos vectoriales en la web, iconografía adaptable, diagramas e ilustraciones interactivas en navegadores.

---

### **4. SGML (Standard Generalized Markup Language)**

**Ejemplo (simplificado):**

```sgml
<!DOCTYPE libro [
<!ELEMENT libro (titulo, autor, capitulo+)>
<!ELEMENT titulo (#PCDATA)>
<!ELEMENT autor (#PCDATA)>
<!ELEMENT capitulo (#PCDATA)>
]>
<libro>
  <titulo>Introducción a SGML</titulo>
  <autor>John Smith</autor>
  <capitulo>Capítulo 1: Historia</capitulo>
</libro>
```

**Entorno de uso:** Estándar genérico de los años 80-90 para definir lenguajes de marcas. Fue base de HTML y XML, usado en documentación técnica y gubernamental.

---

### **5. XHTML (eXtensible HyperText Markup Language)**

**Ejemplo:**

```xhtml
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>Ejemplo XHTML</title>
  </head>
  <body>
    <h1>Hola Mundo</h1>
    <p>Este documento está en XHTML y sigue las reglas de XML.</p>
  </body>
</html>
```

**Entorno de uso:** Navegadores web (años 2000). Fue un intento de hacer HTML más estricto y compatible con XML. Hoy en día ha sido reemplazado casi por completo por HTML5.

---

### **6. HTML5**

**Ejemplo:**

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Ejemplo HTML5</title>
  </head>
  <body>
    <header>
      <h1>Mi Web</h1>
    </header>
    <main>
      <video controls>
        <source src="video.mp4" type="video/mp4">
        Tu navegador no soporta video.
      </video>
    </main>
    <footer>
      <p>© 2025 Ejemplo</p>
    </footer>
  </body>
</html>
```

**Entorno de uso:** Desarrollo moderno de páginas web y aplicaciones, con soporte nativo para audio, vídeo, canvas y APIs (geolocalización, almacenamiento local, etc.).

---

## **Lenguajes relacionados (no mencionados arriba)**

* **XPath** → Lenguaje para navegar y seleccionar nodos dentro de documentos XML. Ejemplo: `//alumno/nombre` selecciona todos los nombres de alumnos.
* **XSLT (Extensible Stylesheet Language Transformations)** → Se usa para transformar documentos XML en otros formatos (HTML, texto plano, etc.).
* **MathML (Mathematical Markup Language)** → Describe fórmulas y expresiones matemáticas en XML.
* **UML (Unified Modeling Language)** → Aunque no es estrictamente un lenguaje de marcas, se representa a menudo en XML para definir diagramas de clases, casos de uso, etc.
* **LaTeX (TeX con macros)** → Sistema de marcas para composición tipográfica científica. No es XML, pero funciona con etiquetas para estructurar texto y fórmulas.
* **JSON (JavaScript Object Notation)** → No es un lenguaje de marcas, sino un formato ligero de datos, pero suele confundirse con XML en entornos de intercambio de información.

----

