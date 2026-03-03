# AIDD Copilot Custom Prompts

Collection de prompts personnalisés pour [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli), conçus pour le framework **AIDD** (AI-Driven Development).

Équivalent de [aidd-claude-custom](https://github.com/RebelliousSmile/aidd-claude-custom) pour Claude Code.

## Prompts disponibles

| Prompt | Description |
|---|---|
| `prompts/01/migrate-docs.md` | Scanne `docs/` et `documentation/`, classifie chaque fichier et le reformate selon les templates AIDD dans `aidd_docs/` |
| `prompts/02/release-to-site.md` | Récupère une release GitHub et traduit les changements notables en contenu marketing sur le site |
| `prompts/03/site-section.md` | Planifie et implémente une section sur le site marketing (Nuxt + Vue + UnoCSS) |
| `prompts/08/changelog.md` | Génère ou met à jour `CHANGELOG.md` à partir de l'historique git, puis commit et tag la release |
| `prompts/08/end-plan.md` | Archive le plan comme traité, retourne sur la branche parente et nettoie |

## Installation

Copier le contenu de ce dépôt dans `.github/custom/` de votre projet :

```bash
git clone <repo-url> .github/custom
```

La structure dans votre projet sera :

```
.github/
  custom/
    prompts/
      01/
      02/
      03/
      08/
    agents/        ← vos agents custom
    instructions/  ← vos instructions custom
    skills/        ← vos skills custom
```

## Usage

Dans GitHub Copilot CLI, référencer le prompt avec `@` :

```
@.github/custom/prompts/08/changelog.md v1.2.0
```

```
@.github/custom/prompts/01/migrate-docs.md
```

## Ajouts projet-spécifiques

Ajouter vos propres prompts directement dans `.github/custom/prompts/` aux côtés des prompts de ce repo.

## Mise à jour du framework

```bash
git -C .github/custom pull
```

## Prérequis

- [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)
- [AIDD](https://github.com/ai-driven-dev/aidd-framework) configuré dans le projet cible (`aidd_docs/` présent)
- `gh` CLI pour les prompts interagissant avec GitHub
