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

##💻 CODE PRINCIPALE
### Localisation du proget
#### SDL3/sdl_3D.cpp

###🎗️Fonctionnement 
.SDL_Init() pour initialiser SDL
.SDL_CreateWindow() pour creer une fenetre 
.SDL_CreateRenderer() pour permettre de dessiner
.SDL_PollEvent pour les touches du clavier 
.SDL_RenderPresent() pour afficher le rendu
