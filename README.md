# Moranguinho
Um jogo feito no Unity, 3D e com o intuito de o jogador passar recolhendo todos os morangos do mapa. O objetivo desse jogo é utilizar as propriedades do canvas do unity.

# Fotos do Jogo
## Menu
<img src="imgs/menu.png">

#### Hierarquia do Menu
<img src="imgs/menuHierarquia.png">

#### Inspetor do Menu - BOTÃO
Arrastar o canvas (que possui o código) e chamar a função TrocarCenaReiniciar() do script TrocarCena.
<img src="imgs/menuBotao.png">

### Trocar de Cena (Reiniciar)
Funciona para trocar de cena para começar a jogar.
```csharp
using UnityEngine;
using UnityEngine.UIElements;
using UnityEngine.SceneManagement;

public class TrocarCena : MonoBehaviour
{
  
    public void TrocarCenaReiniciar(){
        // mudar a cena para a cena fase1
        SceneManager.LoadScene("fase1");
    }
}
```

## Jogo
<img src="imgs/jogo.png">

#### Hierarquia do Jogo
<img src="imgs/jogoHierarquia.png">

#### Inspetor do Jogo - JOGADOR & CHEGADA(gameobject para mudar de cena)
<img src="imgs/jogoCodigo.png">
<img src="imgs/chegadaJogo.png">

### Sistema de Coração
Funciona para verificar se o coração deve estar vazio ou cheio.

```csharp
using UnityEngine.UI;

public class HeartSystem : MonoBehaviour
{
    public int vida;
    public int vidaMaxima;

    public Image[] coracao;
    public Sprite cheio;
    public Sprite vazio;

    void Update()
    {
        HealthLogic();
    }
    
    void HealthLogic(){
        if(vida > vidaMaxima){
                vida = vidaMaxima; }
        for (int i = 0; i < coracao.Length; i++){
            if(i < vida){
                coracao[i].sprite = cheio;
            }
            else{
                coracao[i].sprite = vazio;
            }
            if(i < vidaMaxima){
              coracao[i].enabled = true;
            }
            else{
                 coracao[i].enabled = false;
            }
        }
    } 
}
```

### Sistema de Coleta de Coração
Funciona para quando o player encostar nos corações contar como um coração colhido no HUD.
```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class coletar : MonoBehaviour
{
     // chamando o script de sistema de coração
     public HeartSystem heart;

    // encostar em um gameobject trigger vai contar como um coração coletado no HUD
    void OnTriggerEnter (Collider other) {    
         other.gameObject.SetActive(false);
         heart.vida++;
         
    }
}
```

### Sistema de Chegada
Funciona para verificar se o Gameobject foi colisionado para mudar de cena.
```csharp
using UnityEngine.SceneManagement;

public class chegada : MonoBehaviour
{
    void OnTriggerEnter (Collider other) { 
            SceneManager.LoadScene("end");
        }
}
```


### 
## Fim 
<img src="imgs/fim.png">

#### Fim Hierarquia
<img src="imgs/fimHierarquia.png">

### Trocar de cena para Menu
Funciona para trocar a cena para o menu do jogo.
```csharp
using UnityEngine.SceneManagement;

public class TrocarMenu: MonoBehaviour
{
    public void TrocarCena(){
        // Trocar a cena para o menu do jogo
        SceneManager.LoadScene("menu");
    }
}
```

# Links Importantes
### Link do Jogo - 
### Link do Video -
### Link dos Assets usados - 
# Autores
Yuri Telis Garcia & Mariana Santiago Matos
