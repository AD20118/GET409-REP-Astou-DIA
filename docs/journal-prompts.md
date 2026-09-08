# Journal de Prompts

> 5 entrées minimum. Les 3 techniques (Zero-Shot, Few-Shot, Chain-of-Thought) doivent apparaître **au moins une fois chacune** sur l'ensemble du journal. Chaque entrée = prompt exact + résumé de la réponse + note /5 + itération effectuée.

## Entrée 1 — Chapeaux de Bono

- **Technique :** Chain-of-Thought (demande de raisonner chapeau par chapeau, un par un, avant de synthétiser)
- **Outil :** Claude
- **Prompt exact :**
  > "Applique les 6 Chapeaux de Bono de Edward de Bono au HMW suivant, en contextualisant chaque chapeau avec des éléments concrets de Dakar (pas de généralités) : [HMW]. Traite un chapeau à la fois, dans l'ordre Blanc, Rouge, Noir, Jaune, Vert, Bleu, et termine par une synthèse d'arbitrage au chapeau Bleu."
- **Résumé de la réponse :** Génération des 6 sections contextualisées (feature phone, SMS/USSD, fracture numérique, agent relais communautaire) + synthèse priorisant une solution SMS/USSD à faible friction.
- **Note :** 4/5
- **Itération effectuée :** Reformulation demandée pour rendre le chapeau Noir plus spécifique (dépendance à la mise à jour humaine de l'info) plutôt que générique.

## Entrée 2 — Génération des user stories (backlog.md)

- **Technique :** Few-Shot (le format exact "En tant que… je veux… afin de…" imposé par le cours a été fourni comme modèle, avec les colonnes attendues — priorité, outil, effort, Pain Reliever, critère d'acceptation — avant de demander la génération des user stories)
- **Outil :** Claude
- **Prompt exact :**
  > "Génère un backlog au format du cours : 'En tant que… je veux… afin de…', avec pour chaque user story une priorité MUST/SHOULD/COULD, l'outil utilisé (Dify ou Lovable), un effort (S/M/L), le Pain Reliever du VPC adressé, et un critère d'acceptation testable. Minimum 2 user stories MUST. Base-toi sur les pains identifiés dans la carte d'empathie de Fatou (attente sans visibilité, absence non annoncée du personnel, perte de revenu) et sur le VPC (alerte de présence, estimation d'affluence, canal WhatsApp/SMS)."
- **Résumé de la réponse :** Génération d'un tableau de 5 user stories (2 MUST, 2 SHOULD, 1 COULD), chacune tracée jusqu'à un Pain Reliever du VPC, avec critères d'acceptation mesurables (ex. temps de réponse, mise à jour du statut en moins d'1 minute).
- **Note :** 4/5
- **Itération effectuée :** Ajustement de US-03 pour cibler explicitement l'agent relais du poste de santé (et non l'usager), afin de couvrir le risque Chapeau Noir identifié dans chapeaux-bono.md (dépendance à la mise à jour humaine de l'information).

## Entrée 3 — Configuration de l'agent Dify

- **Technique :** Zero-Shot (prompt système unique, sans exemples préalables, décrivant directement le rôle, le comportement attendu et les données simulées)
- **Outil :** Dify (Chatflow, nœud LLM, modèle gpt-5)
- **Prompt exact :**
  > "Tu es un agent d'information pour un service de santé de proximité à Dakar. Contexte : les usagers (ex. Fatou, commerçante/couturière) veulent savoir, avant de se déplacer, si le personnel de santé est présent aujourd'hui dans leur poste de santé, et estimer le temps d'attente, pour éviter un déplacement inutile. Comportement attendu : 1. Si l'usager ne précise pas de poste de santé, demande-lui lequel parmi : 'Poste de santé HLM', 'Poste de santé Grand Yoff', 'Poste de santé Pikine'. 2. Une fois le poste précisé, réponds avec un statut simulé parmi 'présent' / 'absent' / 'info non disponible', une estimation d'affluence ('faible', 'moyenne', 'élevée'), et un conseil sur le meilleur créneau pour venir. 3. Ton court et simple, adapté à un envoi SMS/WhatsApp (pas de markdown, pas de mise en forme complexe). 4. Si l'usager demande autre chose, réponds poliment que tu ne gères que ces informations pour l'instant. Données simulées à utiliser : Poste de santé HLM : infirmier présent aujourd'hui, affluence élevée, meilleur créneau 15h-17h. Poste de santé Grand Yoff : infirmier absent aujourd'hui (retour demain), affluence non pertinente. Poste de santé Pikine : infirmier présent, affluence faible, tout créneau convient."
- **Résumé de la réponse :** Testé avec "Bonjour, le médecin est-il présent aujourd'hui au poste de santé HLM ?" → réponse directe et correcte (infirmier présent, affluence élevée, conseil 15h-17h). Testé avec "Bonjour, le médecin est-il là ?" (sans poste précisé) → l'agent demande correctement de préciser le poste parmi les 3 proposés avant de répondre.
- **Note :** 5/5
- **Itération effectuée :** Aucune itération nécessaire — le comportement attendu (clarification si poste manquant, réponse directe sinon) a été obtenu dès le premier essai. Agent publié tel quel.

## Entrée 4 — Génération de l'interface Lovable

- **Technique :** Few-Shot (le prompt fournit 3 exemples concrets et complets de contenu attendu — statut, affluence, conseil pour chacun des 3 postes de santé — que le modèle doit reproduire dans l'interface plutôt que d'inventer un format)
- **Outil :** Lovable
- **Prompt exact :**
  > "Crée une interface web simple appelée 'Statut Poste de Santé' pour aider les usagers (ex. Fatou, commerçante à Dakar) à savoir avant de se déplacer si le personnel de santé est présent dans leur poste de santé, et l'affluence estimée. Fonctionnalités attendues : 1. Un menu déroulant (ou 3 boutons) pour choisir un poste de santé parmi : 'Poste de santé HLM', 'Poste de santé Grand Yoff', 'Poste de santé Pikine'. 2. Après sélection, afficher une carte avec : Statut du personnel (Présent/vert, Absent/rouge, Info non disponible/gris), Niveau d'affluence (Faible/Moyenne/Élevée), un conseil texte sur le meilleur créneau. 3. Utiliser des données simulées statiques : HLM (Présent, affluence élevée, 'Venir entre 15h et 17h'), Grand Yoff (Absent, 'retour prévu demain'), Pikine (Présent, affluence faible, 'Tout créneau convient'). 4. Design simple, mobile-first, gros boutons lisibles. 5. Titre 'Statut Poste de Santé — Dakar'. 6. Lien en bas de page vers l'assistant conversationnel Dify : https://udify.app/chat/nBeVgW1ELBcY1Hwl."
- **Résumé de la réponse :** Lovable a généré une interface avec sélecteur de poste de santé, carte de statut colorée (vert/rouge/gris), affichage de l'affluence et du conseil de créneau, et lien vers l'agent Dify — publiée sur https://infosantedakar.lovable.app/.
- **Note :** 5/5
- **Itération effectuée :** Aucune itération majeure nécessaire — l'interface générée correspondait directement aux US-01 et US-02 du backlog dès la première génération.

## Entrée 5 — Structuration de la carte d'empathie à partir des verbatims réels

- **Technique :** Chain-of-Thought (demande explicite de traiter chaque quadrant successivement — Dit, Pense, Fait, Ressent, puis Pains, puis Gains — en s'appuyant uniquement sur les verbatims fournis, avant de synthétiser)
- **Outil :** Claude
- **Prompt exact :**
  > "Voici les 5 verbatims exacts et les réponses complètes de mon interview réelle [verbatims collés]. Structure-les dans une carte d'empathie en 4 quadrants (Dit / Pense / Fait / Ressent) puis liste les Pains et les Gains qui en découlent. Ne généralise pas au-delà de ce que la personne a dit ou de ce qu'on peut raisonnablement déduire de son discours."
- **Résumé de la réponse :** Carte d'empathie remplie avec les 5 verbatims exacts en 'Dit', des déductions raisonnables en 'Pense' (ex. l'incertitude pèse plus que l'attente elle-même), les comportements décrits en 'Fait', les émotions en 'Ressent', et 3 pains / 3 gains directement traçables aux propos recueillis.
- **Note :** 5/5
- **Itération effectuée :** Ajout d'une note de cohérence persona (âge 34→40, activité vendeuse→couturière) pour expliciter l'écart mineur entre le persona de départ et la personne réellement interrogée, sans générer de nouveau contenu inventé.
