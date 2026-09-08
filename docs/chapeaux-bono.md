# Les 6 Chapeaux de Bono — appliqués au HMW retenu

**HMW retenu (S1) :** Comment pourrions-nous permettre à Fatou de savoir à l'avance si le personnel de santé sera présent, pour éviter un déplacement inutile ?

## ⚪ Chapeau Blanc — Faits et données
- Les postes de santé de quartier à Dakar (ex. HLM, Grand Yoff, Pikine) n'ont souvent pas de système de communication numérique vers les usagers.
- Fatou utilise un feature phone : SMS et appel vocal sont ses seuls canaux fiables, pas d'app smartphone.
- Une absence de médecin non annoncée fait perdre en moyenne une demi-journée de vente à Fatou (estimation à confirmer par l'interview).

## 🔴 Chapeau Rouge — Émotions, intuitions
- Frustration et sentiment d'impuissance face à un système opaque.
- Méfiance possible envers un nouvel outil numérique perçu comme "encore une app compliquée".

## ⚫ Chapeau Noir — Risques, prudence
- Dépendance à ce que le personnel du poste de santé mette à jour l'information (risque d'abandon côté staff).
- Fracture numérique : SMS fonctionne, mais qui saisit l'info côté poste de santé si le processus manuel est lourd ?
- Risque réglementaire/confidentialité si on relie des données de présence à des données de santé.

## 🟡 Chapeau Jaune — Bénéfices, optimisme
- Une simple alerte SMS "présence confirmée ce matin" peut faire gagner une demi-journée de revenu à des centaines de vendeuses comme Fatou.
- Effet réseau : les postes de santé qui adoptent l'outil gagnent en image et réduisent l'engorgement.

## 🟢 Chapeau Vert — Créativité, alternatives
- Système de "présence badge" tenu par un agent communautaire relai (pas seulement le médecin) qui met à jour un statut simple via WhatsApp/SMS.
- Ligne téléphonique/USSD gratuite consultable avant de partir.
- Affichage communautaire (radio de quartier, groupe WhatsApp de vendeuses) relayant l'info.

## 🔵 Chapeau Bleu — Synthèse, pilotage
- Prioriser une solution SMS/USSD à faible friction technique, portée par un agent relais local plutôt qu'un système 100% automatisé au démarrage (MVP réaliste avec Lovable + agent Dify pour la logique conversationnelle).
- Le risque Chapeau Noir principal à traiter dans le backlog : garantir la mise à jour de l'info sans effort systématique côté personnel de santé.
