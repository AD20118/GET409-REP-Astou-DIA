# Architecture — Agent Dify (US-01)

## US couverte
US-01 : En tant que Fatou, je veux demander par message si le médecin est présent aujourd'hui au poste de santé, afin de ne pas me déplacer inutilement.

## URL de l'app Dify publiée
https://udify.app/chat/nBeVgW1ELBcY1Hwl

## Implémentation réelle

L'agent a été construit sous forme de **Chatflow Dify** (USER INPUT → nœud LLM avec prompt système → ANSWER), une version simplifiée du schéma détaillé ci-dessous : la logique de classification, de collecte du poste de santé et de génération de réponse est portée directement par le prompt système du nœud LLM (modèle gpt-5), plutôt que par des nœuds séparés. Ce choix reste fidèle à l'US-01 : testé et validé avec deux scénarios (poste précisé → réponse directe ; poste non précisé → clarification demandée avant réponse).

## Schéma du workflow (cible / détaillé)

```
[Usager envoie un message]
        |
        v
[Nœud d'entrée : classification de l'intention]
        |
        v
[L'usager précise / a déjà précisé le poste de santé ?]
   |Non                          |Oui
   v                              v
[Demander le nom du poste]   [Nœud de récupération du statut
        |                     (variable/table simulée : statut
        |                     du poste par jour)]
        |                              |
        +------------------------------+
                     |
                     v
        [Nœud de génération de réponse
         (formate : présent / absent / inconnu
          + heure estimée d'affluence)]
                     |
                     v
        [Réponse envoyée à l'usager]
```

## Rôle des agents / nœuds

| Élément | Rôle |
| --- | --- |
| Nœud de classification | Identifie que la demande concerne "présence médecin" vs autre intention. |
| Nœud de collecte du poste de santé | Demande/confirme le poste de santé concerné si non fourni. |
| Nœud de récupération du statut | Consulte la source de statut (variable Dify simulant la mise à jour de l'agent relais côté poste de santé — cf. US-03). |
| Nœud de génération de réponse | Formule une réponse claire et courte, adaptée à un usage SMS/feature phone (pas de mise en forme riche). |

## Limites connues
- Le statut est mis à jour manuellement par un agent relais (US-03) : pas d'intégration temps réel avec un système hospitalier existant (hors scope MVP).
- Couverture initiale limitée à un nombre restreint de postes de santé test.
