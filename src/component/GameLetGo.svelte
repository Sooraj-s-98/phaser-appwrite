<script>
  import PreloadScene from "../game/PreloadScene";
  import PlayScene from "../game/PlayScene";

  /** @type {Phaser.Types.Core.GameConfig} */
  const gameConfig = {
    type: Phaser.AUTO,
    width: 1000,
    height: 340,
    pixelArt: true,
    transparent: true,
    physics: {
      default: "arcade",
      arcade: {
        debug: false,
      },
    },
    parent: "game",
    scene: [PreloadScene, PlayScene],
  };
  const game = new Phaser.Game(gameConfig);
</script>

<div id="game" />
