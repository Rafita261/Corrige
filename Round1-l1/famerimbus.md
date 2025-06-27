# 🚌 Challenge IV – FamerimBus 

## 📝 Énoncé

À Madagascar, le **prix standard d’un ticket de bus est de 600 Ar** par personne.  
Lorsqu’un groupe paie collectivement, le **receveur (collecteur)** gère la monnaie. Il peut arriver qu’il **arnaque** les passagers, ou au contraire se **fasse avoir** si les passagers trichent sur la monnaie.

### 🧾 Exemple de situation :

Trois passagers paient ensemble avec un **billet de 2000 Ar**. Le receveur demande **300 Ar de plus**, puis leur rend **500 Ar**.

Dans d'autres cas, c’est le receveur qui se fait avoir : les passagers donnent **100 Ar de plus**, et réclament **500 Ar** de retour.

---

## 🎯 Objectif

Étant donné :
- Le nombre de passagers,
- Les billets donnés,
- L’appoint supplémentaire (`extra`),
- L’argent rendu (`rendu`),

Déterminer le **profit** illégal (positif ou négatif).

---

## 📥 Format d'entrée

```
p
b
<billet_1>
<billet_2>
...
<billet_b>
e
r
```

- `p` : nombre de passagers (1 ≤ p ≤ 100)
- `b` : nombre de billets donnés
- `billet_i` : valeur du ième billet (100 ≤ billet ≤ 20000)
- `e` : montant additionnel donné (extra)
- `r` : monnaie rendue par le receveur

---

## 📤 Format de sortie

- `0` : si la transaction est juste
- `> 0` : si le **receveur a volé de l'argent**
- `< 0` : si les **passagers ont payé moins que prévu**

---

## 💡 Idée de résolution — *FamerimBus*

Le problème revient à calculer un **profit (ou une perte)** pour le receveur.

- Le prix total dû est `600 × p`
- Les passagers ont donné :
  - `somme(billets) + extra`
- Le receveur rend `rendu`
- Donc, **argent réellement gardé par le receveur** :  
  `somme(billets) + extra - rendu`
- Et le **profit illégal** devient :

```text
profit = (somme(billets) + extra - rendu) - (600 × p)
```

---

## ✅ Exemples

### 🔢 Sample Input 0
```
1
1
1000
100
500
```

### 🎯 Output
```
0
```

✔️ Le receveur a gardé exactement 600 Ar → transaction juste.

---

### 🔢 Sample Input 1
```
4
3
5000
1000
500
100
500
```

### 🎯 Output
```
3700
```

✔️ Le receveur a gardé **3700 Ar de trop**.

---

## 🐍 Implémentation en Python

```python
def calc_profit(p, bills, extra, change):
    total_due = 600 * p
    total_given = sum(bills) + extra
    amount_kept = total_given - change
    return amount_kept - total_due

if __name__ == "__main__":
    p = int(input())
    b = int(input())
    bills = [int(input()) for _ in range(b)]
    e = int(input())
    r = int(input())
    print(calc_profit(p, bills, e, r))
```

---

## 💻 Implémentation en C

```c
#include <stdio.h>

int main() {
    int p, b, e, r, i, bill, sum = 0;
    scanf("%d", &p);
    scanf("%d", &b);
    for (i = 0; i < b; i++) {
        scanf("%d", &bill);
        sum += bill;
    }
    scanf("%d", &e); // extra
    scanf("%d", &r); // change returned

    int total_due = 600 * p;
    int total_given = sum + e;
    int kept = total_given - r;
    int profit = kept - total_due;

    printf("%d\n", profit);
    return 0;
}
```

---

## 📌 Résumé

- ✅ `0` → transaction honnête
- ✅ `>0` → receveur vole de l’argent
- ✅ `<0` → passagers sous-payent

---

📂 [⬅ Retour à la liste des challenges](../)

---
