---
layout: post
title: Formulario de contacto sin PHP ni JavaScript
date: 2018-11-24 07:06:00
tags: formspree email formulario html estatico
author: kuatroestrellas
---

Hola a todos bienvenidos a esta primer entrada de mi blog **kuatroestrellas** aún sigo trabajando en corregirle algunos bugs, en estos días estuve trabajando con sitios estáticos, específicamente estuve usando jekyll un generador de contenido estático que puede ser una alternativa a wordpress si lo que quieres es unicamente crear un blog, pero bueno vayamonos directamente al grano.

Al momento de intentar ponerle un formulario de contacto me topé con que necesitas usar php, o algún otro lenguaje que se ejecute del lado del servidor, enlazarlo a un servicio online o algo complicado y buscando por ahi me encontre con <a href="https://formspree.io/" target="_blank">formpspree.io</a> , un servicio que te da el control total en tu formulario y no requiere que instales nada en tu servidor.

Ventajas:  
* No requiere PHP  
* No requiere JavaScript  
* NO requiere registro  
* Es gratis, aunque tambien cuenta con una versión de pago  
* Es ideal para sitios estáticos  

Esta solución es para ti si estas usando un servidor barato que no acepte PHP, usando un generador de contenido estático o simples ficheros html.

<h1>1. Conecta tu formulario</h1>
Señala en el atributo action la url de formspree:
```html
<form method="POST" action="https://formspree.io/example@email.com">
```
<h1>2. Agregue atributos al name</h1>
```html
<input type="text" name="name">
```

A continuación el ejemplo completo:

```html
<p>Mantengámonos en contacto. Envíame un mensaje</p>
<form method="POST" action="https://formspree.io/example@email.com">
    <input type="text" placeholder="Name" required name="name" />
    <input type="email" placeholder="Email" required name="email" />

<!--El siguiente atributo esta oculto y es para definir el
asunto de tu correo-->
    <input type="hidden" name="_subject" value="Website contact" />

<!--El siguiente campo es por seguridad para evitar spam, esta oculto
para el usuario pero no para para el bot que lo acabara rellenando
cuando formspree detecte este campo llenado lo mandará directamente  
a tu carpeta de spam-->
    <input type="text" name="_gotcha" style="display:none" />

    <textarea type="text" placeholder="Message" required name="message"></textarea>
    <button type="submit">
        ENVIAR
    </button>
</form>
```

**Listo** eso sería toda la "configuración" que tendrías que hacer, ahora simplemente copia y pega el codigo anterior en tu codigo donde quieras incluir el formulario, agregale css para que no se vea todo meco, remplaza **example@mail.com** con tu email y listo, la primera vez te pedirá que confirmes tu email.
Verdad que es bien sencillo.

En la pagina de <a href="https://formspree.io/" target="_blank">formspree.io</a> encontraras la documentación completa para usar mas elementos es tu formulario y también podrás adquirir la versión PRO.
