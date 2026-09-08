# Backlog

Format : En tant que… je veux… afin de…

| ID | User Story | Priorité | Outil | Effort | Pain Reliever adressé | Critère d'acceptation |
| --- | --- | --- | --- | --- | --- | --- |
| US-01 | En tant que Fatou, je veux demander par message si le médecin est présent aujourd'hui au poste de santé, afin de ne pas me déplacer inutilement. | MUST | Agent Dify | M | Alerte SMS/conversationnelle de présence confirmée | L'agent répond en moins de 10 secondes avec statut "présent / absent / inconnu" pour le poste de santé choisi. |
| US-02 | En tant que Fatou, je veux voir sur une interface simple l'affluence estimée du poste de santé, afin de choisir le meilleur moment pour y aller. | MUST | MVP Lovable | M | Estimation d'affluence en temps réel | L'interface affiche un niveau d'affluence (faible/moyen/élevé) pour au moins un poste de santé test. |
| US-03 | En tant qu'agent relais du poste de santé, je veux mettre à jour le statut de présence en un clic, afin que l'information reste fiable sans effort. | SHOULD | MVP Lovable | S | Réduit le risque Chapeau Noir (dépendance à la saisie humaine) | Un bouton "Présent / Absent aujourd'hui" met à jour le statut visible côté usager en moins de 1 minute. |
| US-04 | En tant que Fatou, je veux recevoir une notification si le statut change après ma dernière consultation, afin d'ajuster mon planning en temps réel. | COULD | Agent Dify | L | Prévisibilité accrue | Une notification SMS est envoyée si le statut passe de "présent" à "absent" dans les 2h précédant l'ouverture. |
| US-05 | En tant que Fatou, je veux pouvoir choisir mon poste de santé parmi une liste courte, afin de recevoir une info pertinente à mon quartier. | SHOULD | MVP Lovable | S | Pertinence de l'information | L'usager peut sélectionner un poste de santé parmi au moins 3 options dans l'interface. |

**Légende Effort :** S = petit, M = moyen, L = large.

**Traçabilité :** chaque US répond à un pain identifié dans docs/carte-empathie.md et adressé dans docs/vpc.md (colonne Pain Reliever).
