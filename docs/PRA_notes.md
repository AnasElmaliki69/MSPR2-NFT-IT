
# Les étapes pour la création d’un PRA

## **Étape 1 :**

Il faut décider ce que l’on doit protéger. 
Dans notre cas :

1. Le service téléphonique (IPBX-VM) CRITICAL
2. La base de données MySQL pour l’application WMS (Warehouse Management System)
3. Les serveurs DC01 et DC02
4. Le VPN Site-to-Site (datacenter ↔ franchises)
5. La plateforme de virtualisation
6. Le système de supervision

---

## **Étape 2 : Définir le RTO et le RPO**

### **RPO (Recovery Point Objective) :**

Objectif de perte de données acceptable (on accepte de perdre au maximum les données des 15 min).

**Exemple :**
Si les sauvegardes (sur le local et sur le cloud, Azure dans notre cas) sont effectuées une fois par jour à 2 h du matin :
– Le serveur plante à 16 h
– La dernière sauvegarde date d’il y a 14 heures

Du coup, si le RPO est de 2 h, le RPO n’est pas satisfait il faut augmenter la fréquence des sauvegardes.

### **RTO (Recovery Time Objective) :**

Objectif de temps de remise en service.
**Exemple :** “On doit tout remettre en marche en 2 heures.”

---

## **Étape 3 :**

Mettre en place les sauvegardes des données régulièrement (Azure et local dans notre cas).
Les sauvegardes seront planifiées automatiquement.

**Exemple :**
Si le serveur tombe à 15 h et que la dernière sauvegarde date de 14 h 45,
le RPO = 15 minutes (on perd 15 minutes de données maximum).

---

## **Étape 4 :**

Prévoir un site ou une solution de secours.

**Exemple :**
Si ton serveur principal tombe, un autre serveur prend automatiquement sa place (hyperviseur1, hyperviseur2/db1, db2)

---

## **Étape 5 : Écrire les procédures**

On documente chaque étape à suivre en cas d’incident :

* qui fait quoi,
* comment restaurer les données,
* comment relancer les serveurs,
* comment communiquer avec les utilisateurs.

---

## **Étape 6 :**

Tester régulièrement — il faut faire des tests de simulation.

---
## **Étape 7 :**

Chaque fois qu’il y a un changement dans l’entreprise (nouvelle appli, nouveau serveur, nouvelle politique),
le PRA doit être mis à jour pour rester valide.

---

