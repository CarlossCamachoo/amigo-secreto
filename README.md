# 🎁 Amigo Secreto

Una web para hacer el sorteo de amigo secreto en familia. Cada quien saca su papelito de un tazón, se abre y… 💥 ¡confeti!

- Nadie se saca a sí mismo.
- Cada nombre sale una sola vez.
- No hay parejas cruzadas (si Carlos le da a Andrés, Andrés no le da a Carlos).
- Funciona en iPhone y Android, sin instalar nada. Es un solo archivo: `index.html`.

## Tu lista de participantes

Al inicio del `<script>` en `index.html` está el bloque `CONFIG`: ahí van el evento, el presupuesto, la fecha, la hora, el lugar y los nombres. La página arranca con esa lista cargada. Si hay nombres repetidos, la página avisa (dos personas con el mismo nombre necesitan apellido o inicial).

## Seguro contra repetidos

- Cada sorteo tiene un **código** (ej. `NNGZ`) que aparece en el mensaje de WhatsApp y al abrir cada link: todos deben ver el mismo.
- La pantalla de links muestra **✅ Sorteo verificado** (todos tienen papelito, nadie se repite, nadie se sacó a sí mismo) sin revelar quién le tocó a quién.
- Si ya enviaste links, hacer un sorteo nuevo pide doble confirmación, porque mezclar links viejos y nuevos crearía repetidos.
- Si en un mismo celular se abre el link de otra persona, la página pregunta antes de mostrarlo.
- **Autodestrucción:** al descubrir el nombre aparece un letrero con cuenta regresiva de 15 segundos (con 3·2·1 gigante al final) y el papelito se destruye; el botón “Guardar el secreto” lo destruye al instante. Si se vuelve a abrir el link en ese celular, solo sale “Esta página se autodestruyó” (con la fecha, hora y lugar).
- Haz el sorteo **una sola vez y desde un solo celular**, y envía todos los links desde ahí.

## Anti-trampa (hasta donde permite una página web)

- Al abrir un link, la dirección se limpia: si comparten o copian desde el navegador, no va el papelito.
- Antes de descubrir pregunta “¿Eres [nombre]?”.
- El papelito tiene marca de agua “Solo para [nombre] · No compartir”.
- Si la persona sale de la página con el nombre en pantalla, se oculta y se destruye.
- El nombre no se puede seleccionar, copiar ni imprimir.
- Una página web no puede bloquear capturas de pantalla ni que alguien reenvíe el link original de WhatsApp; eso solo lo logra una app nativa o un servidor.

## Tablero: quién ya descubrió

La página principal muestra en **verde** a los participantes que ya descubrieron a su amigo secreto (se actualiza cada 30 s). Para compartir el avance entre celulares usa el contador gratuito [Abacus](https://abacus.jasoncameron.dev) (sin cuenta): solo guarda un código anónimo por participante, nunca a quién le tocó. Los links de prueba no cuentan.

## Cómo se usa

1. Escribe el nombre del evento, el presupuesto y la fecha (opcionales).
2. Agrega a los participantes (mínimo 3). Puedes pegar varios separados por coma.
3. Toca **Hacer el sorteo** y elige cómo van a sacar los papelitos:
   - **📱 Pasando el celular:** todos juntos. Cada persona toca su nombre, revuelve el tazón y abre su papelito sin que nadie mire.
   - **💌 Enviando links:** cada persona recibe su link por WhatsApp y saca el papelito desde su celular.

El sorteo queda guardado en el celular donde se hizo, así que no se pierde si cierras la página.

## Publicarlo en GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `amigo-secreto`).
2. Sube el archivo `index.html`, desde la web con **Add file → Upload files** o con git:
   ```bash
   git init && git add index.html README.md && git commit -m "Amigo secreto" && git branch -M main
   git remote add origin https://github.com/TU-USUARIO/amigo-secreto.git
   git push -u origin main
   ```
3. En el repositorio entra a **Settings → Pages**, elige **Deploy from a branch**, rama `main`, carpeta `/ (root)` y guarda.
4. Al minuto queda en `https://TU-USUARIO.github.io/amigo-secreto/`.

> Importante: haz el sorteo desde la URL de GitHub Pages (no desde el archivo local) para que los links que envíes funcionen.

## Nota sobre los links

Cada link lleva dentro (codificado) a quién le tocó esa persona. No hay servidor ni base de datos, así que no abras los links de los demás o se daña la sorpresa.
