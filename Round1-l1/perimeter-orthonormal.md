# 📐 Challenge III – Perimeter of Triangle (Orthonormal Plane)

## 📝 Énoncé

Étant donné les coordonnées de trois points `A`, `B`, `C` dans un **plan orthonormé (O, i, j)**, calculez le **périmètre du triangle** formé par ces trois points.

---

## 📥 Format d'entrée

Trois lignes contenant chacune deux entiers, séparés par un espace :

```
xA yA
xB yB
xC yC
```

**Contraintes :**
- `-1000 ≤ xi, yi ≤ 1000` pour chaque `i ∈ {A, B, C}`

---

## 📤 Format de sortie

Un **nombre réel**, arrondi à **2 chiffres après la virgule**, représentant le périmètre.

---

## ⚠️ Piège du problème

Quand **deux points coïncident**, le triangle devient **dégénéré** (ligne droite).  
Dans ce cas, il faut **éviter de compter deux fois la même distance** :

- Si A = B → Triangle = segment AC
- Si B = C → Triangle = segment AB
- Si A = C → Triangle = segment AB
- Si A = B = C → Périmètre = 0.00

✅ Il faut donc :
- Identifier les **points identiques**
- Ne **compter qu'une seule fois** la distance réelle dans ce cas

---

## ✅ Exemple

### 🔢 Input
```
1 2
3 3
-2 2
```

### 🎯 Output
```
10.34
```

---

## 🧪 Cas Limite

### 🔢 Input
```
1 1
1 1
4 5
```

### 🎯 Output
```
5.00
```

**Explication :**  
A = B → Le triangle n'est qu'un segment entre A et C → Distance = 5.00

---

## 💻 Implémentation en C

```c
#include <stdio.h>
#include <math.h>
#include <stdbool.h>

float distance(int x1, int y1, int x2, int y2) {
    if (x1 == x2 && y1 == y2)
        return 0.0;
    return sqrt((x2 - x1)*(x2 - x1) + (y2 - y1)*(y2 - y1));
}

int main() {
    int xA, yA, xB, yB, xC, yC;
    scanf("%d %d", &xA, &yA);
    scanf("%d %d", &xB, &yB);
    scanf("%d %d", &xC, &yC);

    float peri;

    if (xA == xB && yA == yB)
        peri = distance(xA, yA, xC, yC);
    else if (xB == xC && yB == yC)
        peri = distance(xA, yA, xB, yB);
    else if (xA == xC && yA == yC)
        peri = distance(xA, yA, xB, yB);
    else
        peri = distance(xA, yA, xB, yB) + distance(xB, yB, xC, yC) + distance(xC, yC, xA, yA);

    printf("%.2f\n", peri);
    return 0;
}
```

---

## 🐍 Implémentation en Python

```python
import math

def distance(p1, p2):
    if p1 == p2:
        return 0.0
    return math.sqrt((p1[0] - p2[0])**2 + (p1[1] - p2[1])**2)

def perimeter(a, b, c):
    if a == b or b == c:
        return distance(a, c)
    if a == c:
        return distance(a, b)

    peri = 0.0
    peri += distance(a, b) + distance(b, c) + distance(c, a)
    return peri

if __name__ == "__main__":
    a = tuple(map(int, input().split()))
    b = tuple(map(int, input().split()))
    c = tuple(map(int, input().split()))
    result = perimeter(a, b, c)
    print(f"{result:.2f}")
```

---

📂 [⬅ Retour à la liste des challenges](../)

---
