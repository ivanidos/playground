{

}

# Logic Step

To keep your code clean you should separate logic from rendering.

Update `step: function(dt) { }`

Render `render: function(dt) { }`

Just a little recap if you are new to gamedev. `dt` is delta time. Time that passed since last step.
You should use it in your updates if you want characters in your game to move at the same speed regardless
of being run on Intel Core i7 or Atari ST.

run
```javascript
app = playground({

  create: function() {

    this.thomas = { 
      x: 0, 
      y: this.center.y, 
      width: 32,
      height: 64,
      color: "#e2543e", 
      speed: 100 
    };

  },

  step: function(dt) {

    this.thomas.x += this.thomas.speed * dt;    

    if(this.thomas.x > this.width) this.thomas.x = -this.thomas.width;

  },

  render: function(dt) {
    
    var thomas = this.thomas;

    this.layer.clear("#000");

    this.layer
      .fillStyle(thomas.color)
      .fillRect(thomas.x, thomas.y, thomas.width, thomas.height);

  },

  container: exampleContainer

});
```