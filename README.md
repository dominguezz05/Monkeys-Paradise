# Monkeys-Paradise

¡Bienvenido a **Monkey's Paradise**! 🐒 Un juego arcade 2D lleno de acción donde controlarás a un mono que debe esquivar meteoritos y enfrentarse a épicos jefes finales.

---

## 📖 Descripción
Este proyecto lo desarrollé como parte de mi aprendizaje en desarrollo web . Utilicé tecnologías clave para trabajar tanto la parte gráfica como la lógica de juego:

- 🎨 HTML5 + CSS3
- ⚡ JavaScript 

---

## ✂️ Fragmentos de código
Aquí algunos ejemplos del código que hay detrás de Monkey's Paradise:

### Movimiento del jugador
```javascript
function movePlayer() {
    if (input.left) player.x -= playerSpeed;
    if (input.right) player.x += playerSpeed;
}
