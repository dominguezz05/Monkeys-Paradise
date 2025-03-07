# Monkeys-Paradise

¡Bienvenido a **Monkey's Paradise**! 🐒 Un juego arcade 2D lleno de acción donde controlarás a un mono que debe esquivar meteoritos y enfrentarse a épicos jefes finales.

---

## 📖 Descripción
Este proyecto lo desarrollé como parte de mi aprendizaje en desarrollo web . Utilicé tecnologías clave para trabajar tanto la parte gráfica como la lógica de juego:

- 🎨 HTML5 + CSS3
- ⚡ JavaScript 

---

# Características principales:

🔬 Diseño atractivo con gráficos animados.

🔧 Diferentes niveles con dificultad creciente.

🔥 Múltiples enemigos y jefes desafiantes.

🌐 Accesible directamente desde cualquier navegador.

🎨 Fondos y diseños personalizados.

---

# 🔄 Cómo Jugar

Controles:

Mover al mono: Usa las teclas W, A, S, D.

disparar: Usa la barra espaciadora.

Eventos especiales: Usar la tecla e

---

# 🏆 Contribuciones

Si deseas contribuir al proyecto, no dudes en contactarme y mejoremos esta gran idea.

---

## ✂️ Fragmentos de código
Aquí algunos ejemplos del código que hay detrás de Monkey's Paradise:

### Movimiento del jugador
```javascript
function moveMonkey() {
  // Si la tecla derecha es presionada
  if (keys.right) {
    monkey.dx = monkey.speed;
  }
  // Si la tecla izquierda es presionada
  else if (keys.left) {
    monkey.dx = -monkey.speed;
  }
  // Si la tecla arriba es presionada
  else if (keys.up && !monkey.jumping) {
    monkey.dy = monkey.jumpPower;
    monkey.jumping = true;
  }
  // Si ninguna tecla es presionada
  else {
    monkey.dx = 0;
  }

  monkey.y += monkey.dy;
  monkey.x += monkey.dx;

  // Evitar que el mono salga del lienzo
  if (monkey.x < 0) monkey.x = 0;
  if (monkey.x + monkey.width > canvas.width)
    monkey.x = canvas.width - monkey.width;

  if (monkey.y + monkey.height >= canvas.height) {
    monkey.y = canvas.height - monkey.height;
    monkey.dy = 0;
    monkey.jumping = false;
  } else {
    monkey.dy += gravity;
  }
}
````

### Creacion de los meteroritos
```javascript
function generateEnemy() {
  const size = Math.floor(Math.random() * 3) + 1; // Tamaño aleatorio de 1 a 3
  const x = Math.random() * (canvas.width - 30 * size); // Asegurar que el meteorito no salga del lienzo
  const y = -30; // Aparece fuera de la pantalla

  enemies.push({ x, y, speed: enemyFallSpeed, size });
}

// Dibuja meteoritos con tamaños aleatorios
function drawEnemies() {
  enemies.forEach((enemy, index) => {
    const meteorWidth = 30 * enemy.size;
    const meteorHeight = 30 * enemy.size;

    ctx.drawImage(enemyImage, enemy.x, enemy.y, meteorWidth, meteorHeight);
    enemy.y += enemy.speed; // Velocidad de caída

    // Eliminar meteoritos que salen del lienzo
    if (enemy.y > canvas.height) {
      enemies.splice(index, 1);
    }
  });
}

// Actualiza los enemigos
function updateEnemies() {
  if (Math.random() < enemySpawnRate) {
    generateEnemy(); // Probabilidad de generar un enemigo
  }
}
````
### Colisiones para la obtención de puntuaje
```javascript

function checkCollisions() {
  // Verificar colisión con los plátanos y agregar puntos
  bananas.forEach((banana, index) => {
    if (
      banana.x < monkey.x + monkey.width &&
      banana.x + 30 > monkey.x &&
      banana.y < monkey.y + monkey.height &&
      banana.y + 30 > monkey.y
    ) {
      score += 10; // Aumentar el puntaje
      bananas.splice(index, 1); // Eliminar el plátano
    }
  });
}
````
### Aparición del boss
```javascript
function spawnBoss() {
  boss = {
    x: canvas.width / 2 - 50, // Aparece centrada
    y: 100, // Aparece más abajo en la pantalla
    width: 100,
    height: 100,
    speed: 1, // Velocidad de descenso
  };
  bossTransition = true;
}
````
---
## 📸 Capturas

| Gameplay      | Enemigos |
|----------------|---------|
| ![Gameplay](./assets/gameplay.png) | ![Boss](./assets/boss.png) |
---
## 🎧 Creditos

Mono Aventurero fue desarrollado por Iker Domínguez.

Agradecimientos: Alejandro, Adrian y Fernando.

## 📬 Contacto

¿Tienes alguna idea o sugerencia? No dudes en escribirme:

- 📧 **Email:** [ikerdc2005@gmail.com](mailto:ikerdc2005@gmail.com)
- 🔗 **LinkedIn:** [Iker Domínguez - LinkedIn](https://www.linkedin.com/in/iker-dom%C3%ADnguez-calcerrada-423736298/)


© 2025 Monkey´s Paradise. Todos los derechos reservados.
