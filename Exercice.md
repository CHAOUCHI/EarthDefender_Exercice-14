### Chapitre 9 - Détecter les collisions entre GameObject
Pour détecter la collision il faut savoir si un GameObject est en contact avec un autre.

Dans la boucle d'événement, j'ai actuellement une boucle *for* qui déssine tout les `GameObjects`.

```ts
private loop(){
        setInterval(()=>{
            // Clear context
            this.context.clearRect(0,0,this.CANVAS_WIDTH,this.CANVAS_HEIGHT);
            this.context.fillStyle = "#141414";
            this.context.fillRect(0,0,this.CANVAS_WIDTH,this.CANVAS_HEIGHT);
            
            this.gameObjects.forEach(go=>{
                go.callUpdate();
                this.draw(go);
            })
        },10); 
    }
```

Pour commencer on peut vérifier si un alien touche un joueur.
```ts
private loop(){
    setInterval(()=>{
        // Clear context
        this.context.clearRect(0,0,this.CANVAS_WIDTH,this.CANVAS_HEIGHT);
        this.context.fillStyle = "#141414";
        this.context.fillRect(0,0,this.CANVAS_WIDTH,this.CANVAS_HEIGHT);
        
        this.gameObjects.forEach(go=>{
            go.callUpdate();
            this.draw(go);
            // Je dois donc crée une méthode overlap ...
            if(go instanceof Alien  && this.player.overlap(go)){ 
                console.log("Alien touch player");
            }
        })

    },10); 
}
```

Il me faut donc une méthode publique de la classe `GameObject` qui revnoi `true` si le gameObject passé en paramètre touche le gameObject appelant (player dans cet exemple).

#### Exercice 14

Implémentez la méthode GameObject.overlap() qui permet de vérifier si une GameObject en touche un autre.

```ts
import { Assets } from "../Assets.js";
import { Game } from "../Game.js";
import { Position } from "../Position.js";

export class GameObject{
    
    private position : Position;
    private image : HTMLImageElement;
    private game : Game;
    constructor(game : Game){
        this.position = {
            x : 0,
            y : 0
        };
        this.image = Assets.getDefaultImage();
        this.game = game;
        this.start();
    }
    protected start(){}
    protected update(){}
    public callUpdate(){
        this.update();
    }

    /**
     * Check is the other GameObject collide this GameObject
     */
    public overlap(other : GameObject) : boolean{
        // Codez ici ...









    }


    public getImage() : HTMLImageElement{
        return this.image;
    }
    public getPosition() : Position{
        return this.position;
    }
    public getGame() : Game{
        return this.game;
    }
    public setImage(image : HTMLImageElement){
        this.image = image;
    }
    public setPosition(position : Position){
        this.position = position;
    }
}
```

#### Solution Exercice 14

