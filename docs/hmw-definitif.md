# HMW définitif

## Draft S1
Comment pourrions-nous permettre à Fatou de savoir à l'avance si le personnel de santé sera présent, pour éviter un déplacement inutile ?

## 3 versions retravaillées

**Version 1 (plus large) :**
Comment pourrions-nous réduire le temps perdu par les vendeuses de marché lors de leurs démarches de santé ?

**Version 2 (plus ciblée sur le canal) :**
Comment pourrions-nous informer Fatou par SMS, avant qu'elle ne quitte sa boutique, de la présence du médecin au poste de santé ?

**Version 3 (orientée solution testable) :**
Comment pourrions-nous, via un agent conversationnel simple, permettre à Fatou de vérifier en moins d'une minute si un déplacement au poste de santé vaut le coup aujourd'hui ?

## Version retenue

> **Comment pourrions-nous permettre à Fatou de vérifier, avant de quitter sa boutique, si le personnel de santé est présent et le temps d'attente estimé au poste de santé, via un canal accessible à tous (SMS/agent conversationnel) ?**

## Les 3 critères de validation (cours)

1. **Persona présent :** ✅ Fatou, 34 ans, vendeuse au marché HLM, feature phone — nommée explicitement dans le HMW.
2. **3 solutions imaginables :**
   - Alerte SMS automatique envoyée par un agent relais du poste de santé.
   - Agent conversationnel (Dify) consultable par SMS/WhatsApp répondant en langage naturel.
   - Ligne USSD courte avec menu simple (1 = présence médecin, 2 = affluence).
3. **Risque Chapeau Noir intégré :** dépendance à la mise à jour de l'information par le personnel de santé — traité dans le backlog via une US dédiée à la simplicité de saisie côté agent relais.
