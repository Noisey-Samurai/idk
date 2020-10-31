var jittering;
var patrolling;
var wandering;
var swimming_left_and_right;
var moving_east;
var shrinking;
var growing;
var moving_north;
var moving_south;
var moving_west;
var spinning_right;

function math_random_int(a, b) {
  if (a > b) {
    // Swap a and b to ensure a is smaller.
    var c = a;
    a = b;
    b = c;
  }
  return Math.floor(Math.random() * (b - a + 1) + a);
}

function jittering2(this_sprite) {
  changePropBy(this_sprite, "scale", math_random_int(-1, 1));
}

function swimming_left_and_right2(this_sprite) {
  if (getProp(this_sprite, "direction") == 180) {
    mirrorSprite(this_sprite, "right");
  } else if (getProp(this_sprite, "direction") == 180) {
    mirrorSprite(this_sprite, "left");
  }
  moveForward(this_sprite, 5);
  if (isTouchingEdges(this_sprite)) {
    edgesDisplace(this_sprite);
    changePropBy(this_sprite, "direction", 180);
  }
}

function shrinking2(this_sprite) {
  changePropBy(this_sprite, "scale", -1);
}

function patrolling2(this_sprite) {
  moveForward(this_sprite, 5);
  if (isTouchingEdges(this_sprite)) {
    edgesDisplace(this_sprite);
    changePropBy(this_sprite, "direction", 180);
  }
}

function wandering2(this_sprite) {
  if (math_random_int(0, 5) == 0) {
    changePropBy(this_sprite, "direction", math_random_int(-25, 25));
  }
  moveForward(this_sprite, 1);
  if (isTouchingEdges(this_sprite)) {
    edgesDisplace(this_sprite);
    changePropBy(this_sprite, "direction", math_random_int(135, 225));
  }
}

function growing2(this_sprite) {
  changePropBy(this_sprite, "scale", 1);
}

function moving_east2(this_sprite) {
  moveInDirection(this_sprite, 5, "East");
}

function moving_north2(this_sprite) {
  moveInDirection(this_sprite, 5, "North");
}

function moving_south2(this_sprite) {
  moveInDirection(this_sprite, 5, "South");
}

function moving_west2(this_sprite) {
  moveInDirection(this_sprite, 5, "West");
}

function spinning_right2(this_sprite) {
  turn(this_sprite, 6, "right");
}

setBackgroundImage("https://studio.code.org/api/v1/animation-library/04L4sdTODkNZF1OHf4qO_I.Al3QP43wA/category_backgrounds/city.png");
makeNewSpriteAnon("blue alien", ({"x":200,"y":200}));
makeNewSpriteAnon("pink alien", ({"x":75,"y":250}));
makeNewSpriteAnon("yellow alien", ({"x":325,"y":250}));
addBehaviorSimple(({costume: "blue alien"}), new Behavior(jittering2, []));
addBehaviorSimple(({costume: "pink alien"}), new Behavior(patrolling2, []));
addBehaviorSimple(({costume: "yellow alien"}), new Behavior(wandering2, []));
makeNewSpriteAnon("bell", ({"x":200,"y":350}));

spriteClicked("when", ({costume: "bell"}), function (extraArgs) {
  removeAllBehaviors(({costume: "blue alien"}));
  removeAllBehaviors(({costume: "pink alien"}));
  removeAllBehaviors(({costume: "yellow alien"}));
});

checkTouching("when", ({costume: "blue alien"}), ({costume: "pink alien"}), function (extraArgs) {
  addBehaviorSimple(({costume: "blue alien"}), new Behavior(wandering2, []));
  makeNewSpriteAnon("alienBeige_1", ({"x":110,"y":67}));
  addBehaviorSimple(({costume: "alienBeige_1"}), new Behavior(swimming_left_and_right2, []));
});

checkTouching("when", ({costume: "alienBeige_1"}), ({costume: "yellow alien"}), function (extraArgs) {
  addBehaviorSimple(({costume: "alienBeige_1"}), new Behavior(moving_east2, []));
  makeNewSpriteAnon("green alien", ({"x":299,"y":54}));
  addBehaviorSimple(({costume: "green alien"}), new Behavior(patrolling2, []));
});

spriteClicked("when", ({costume: "yellow alien"}), function (extraArgs) {
  setTint(({costume: "yellow alien"}), '#66cccc');
});

spriteClicked("when", ({costume: "green alien"}), function (extraArgs) {
  removeTint(({costume: "green alien"}));
});

spriteClicked("when", ({costume: "alienBeige_1"}), function (extraArgs) {
  setTint(({costume: "alienBeige_1"}), '#006600');
});

keyPressed("when", "space", function () {
  setTint(({costume: "green alien"}), '#ffff33');
});
