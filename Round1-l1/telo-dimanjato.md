# 🥇 Challenge I – Telo Dimanjato

## 📝 Énoncé

Rakahihatra veut acheter `n` **mofogasy** (gâteaux traditionnels malgaches) auprès de Maman’i Kambana.

- Pour **chaque lot de 3 mofogasy**, elle accepte un prix spécial de **500 Ar**.
- Pour les mofogasy restants (moins de 3), elle garde le prix habituel de **200 Ar par mofogasy**.

On vous demande de calculer le **prix total en Ariary (Ar)** que Rakahihatra doit payer pour `n` mofogasy.

---

## 💡 Idée de Résolution

Il faut :

- Diviser `n` par 3 :
  - Le **quotient** donne le nombre de lots à 500 Ar.
  - Le **reste** donne le nombre de mofogasy restants à 200 Ar.

---

## 🔧 Implémentation

### 📜 Pseudo-Code

```text
entier fonction prix(d entier n)
debfonc
    entier nb500, nb200 ;
    nb500 ← n div 3 ;
    nb200 ← n mod 3 ;
    retourner (nb500*500) + (nb200*200) ;
finfonc ;
```

---

### 🐍 Python

```python
def prix(n) : return ((n//3) * 500)+((n%3) * 200)
if __name__ == '__main__' : print(prix(int(input()))) #Programme principale
```

---

### 💻 C / C++

⚠️ Attention : remplacez les guillemets typographiques (‘’ ou “”) par des guillemets simples droits (") dans un vrai éditeur C.

```c
#include <stdio.h>
#define prix(n)  ((n/3) * 500) + ((n%3) * 200) 
int main(){
    int n ;
    scanf("%d", &n) ;
    printf("%d", prix(n)) ;
    return 0 ;
}
```

---

## 📤 Format de Sortie

Un seul entier – le **prix total** en **Ariary (Ar)**.

---

## 📘 Exemples

### 🧪 Sample Input 0

```
3
```

### ✅ Sample Output 0

```
500
```

**Explication :** Rakahihatra achète 3 mofogasy → 1 lot à 500 Ar.

---

### 🧪 Sample Input 1

```
2
```

### ✅ Sample Output 1

```
400
```

**Explication :** Pas de lot possible. Chaque mofogasy coûte 200 Ar → 2 × 200 = 400 Ar.

---

### 🧪 Sample Input 2

```
5
```

### ✅ Sample Output 2

```
900
```

**Explication :**

- 3 mofogasy → 500 Ar
- 2 restants → 2 × 200 = 400 Ar  
  ➡️ **Total = 900 Ar**


---

📂 [⬅ Retour à la liste des challenges](../)

---
