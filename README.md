# Building My First JavaScript Game – What I Learned

When I built this game, I started by organizing my code using **object-oriented programming**. I created separate classes for the main elements:

- `Player` – the character the user controls  
- `Projectile` – bullets fired by the player  
- `Enemy` – incoming targets  
- `Particle` – visual effects like explosions  

Each class had its own properties and methods, which helped keep things clean and reusable. I even experimented with **inheritance** — for example, I considered having `Particle` extend `Enemy` to reuse some logic while customizing behavior.

---

## Drawing and Animating with the Canvas API

To draw the game, I used the **Canvas API**. I started with simple shapes like circles and rectangles. Using `ctx.fillStyle`, I applied different colors and transparency.

To animate everything, I used `requestAnimationFrame`. This allowed me to update the canvas smoothly each frame. I also added a **trailing effect** by drawing a semi-transparent black rectangle over the canvas on each frame. This created a nice motion blur effect.

---

## Handling Collisions and Game Logic

For **collision detection**, I used `Math.hypot` to measure the distance between two objects — like a projectile and an enemy. If the distance was small enough, I would:

- Destroy the enemy  
- Create a particle explosion  
- Increase the score  

I also wrote logic to **spawn enemies randomly** from all four sides of the canvas. I used `Math.random()` to choose a side and position, then calculated a direction that would send the enemy toward the player.

---

## Projectile Movement with Trigonometry

When the player clicks, a projectile is fired toward that position. Here’s how I handled that:

1. Calculate the angle between the player and the click using `Math.atan2`.
2. Use `Math.cos` and `Math.sin` to get the velocity.
3. Move the projectile each frame using:

   ```js
   this.x += this.velocity.x;
   this.y += this.velocity.y;

   ## Creating Particle Effects

To create explosions, I generated particles when an enemy was destroyed. Each particle:

- Got a random direction using `(Math.random() - 0.5)`
- Got a random speed using `(Math.random() * 8)`
- Gradually faded out by decreasing its `alpha` property

This created a smooth and satisfying visual effect.

---

## User Interaction and Game Arrays

The game reacts to **mouse clicks** — when the player clicks, a projectile is fired in that direction. I handled this with a simple `mousedown` event listener.

I also managed arrays for `projectiles`, `enemies`, and `particles`. I added to these arrays as needed and removed items using `splice` when they were no longer active.

---


