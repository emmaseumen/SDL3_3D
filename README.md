# SDL3_3D
# 📚 PROGET D IMPLEMENTATION DE SDL3
Ce proget montre un programme ecrit en c++ utilisant SDL3 pour afficher une fenetre avec un carre bleu que l utilisateur peut deplacer avec les touches.

## 📰 Objectif du programme
.Creer une fenetre SDL3
.Dessiner un carre bleu 
.Deplacer ce carre avec les touches du clavier

### 🛤️ Ce qu il faut avoir pour le faire
.SDL3 doit etre installe
.Un compilateur c++(g++, clang++, ect)

### compilation
clang++ -IC:/msys2/Ucrt64/include -LC:/msys2/Ucrt64/lib -lSDL3 -o nom.exe nom_du_fichier.cpp

## 💻 CODE PRINCIPALE
### Localisation du proget
#### SDL3/sdl_3D.cpp
```cpp
#include <SDL3/SDL.h>
#include <iostream>

int main(){
    //demarrer SDL
    if(SDL_Init(SDL_INIT_VIDEO) != 0){
        std::cout <<"erreur SDL : "<< SDL_GetError() << std::endl;//affiche une erreur si SDL n arrive pas a demarrer
    }
    //pour creer une fenetre 
    SDL_Window* window = SDL_CreateWindow("point bleu", 800, 600, SDL_WINDOW_RESIZABLE);//Pour donner les dimentions de notre fenetre
    //creer le renderer pour dessiner
    SDL_Renderer* renderer = SDL_CreateRenderer(window, nullptr, 0);//pour dessiner des formes et donner des couleurs
    
    //position du point
    int x = 400;
    int y = 300;
    bool running = true;
    SDL_Event event;//pour permettre de lire ce que l utilisateur fait(clavier, souris, fermeture)
    
    while(running){
      while(SDL_PollEvent(&event)){//pour lire les evenements(clavier, fermeture)
           if(event.type == SDL_EVENT_QUIT){//pour la fermeture de la fenetre donc running renvoie false
              running = false;
            }
           //pour gerer le clavier pour deplacer la position du point
           if(event.type == SDL_EVENT_KEY_DOWN){
              if(event.key.key == SDLK_UP) y-= 5;
              if(event.key.key == SDLK_DOWN) y += 5;
              if(event.key.key == SDLK_LEFT) x -= 5;
              if(event.key.key == SDLK_RIGHT) x += 5;
            }
        }
    }
    //pour effacer l ecran donc mettre en noir
    SDL_SetRenderDrawColor(renderer, 0, 0, 0, 255);//pour mettre la couleur noire on utilise(0, 0, 0)
    SDL_RenderClear(renderer);

    //pour dessiner le point bleu 
    SDL_SetRenderDrawColor(renderer, 0, 0, 255, 255);//pour mettre la couleur bleu on utilise(0, 0, 255)
    SDL_FRect point = {(float)x, (float)y, 10.0f, 10.0f};//pour creer un petit carre de 10px x 10px place aux coordonnees x et y 
    SDL_RenderFillRect(renderer, &point);//pour dessiner ce carre
    
    //pour afficher le dessin a l ecran
    SDL_RenderPresent(renderer);//affiche ce qu on a dessine a l ecrant 

    //pour nettoyer et quitter
    SDL_DestroyRenderer(renderer);//pour detruire le renderer
    SDL_DestroyWindow(window);//pour detruire la fenetre
    SDL_Quit();//pour fermer SDL

    return 0;
}
```

### 🎗️Fonctionnement 
.SDL_Init() pour initialiser SDL
.SDL_CreateWindow() pour creer une fenetre 
.SDL_CreateRenderer() pour permettre de dessiner
.SDL_PollEvent pour les touches du clavier 
.SDL_RenderPresent() pour afficher le rendu
