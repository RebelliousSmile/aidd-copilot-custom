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

## Installation

Cloner ce dépôt dans `.github/copilot-custom/` de votre projet :

```bash
git clone <repo-url> .github/copilot-custom
```

Ou ajouter comme sous-module git (recommandé) :

```bash
git submodule add <repo-url> .github/copilot-custom
```

## Usage

Dans GitHub Copilot CLI, référencer le prompt avec `@` puis décrire ce que tu veux :

```
@.github/copilot-custom/prompts/08/changelog.md v1.2.0
```

```
@.github/copilot-custom/prompts/01/migrate-docs.md
```

L'argument (version, description, etc.) se passe directement dans le message textuel après la référence.

## Ajouts projet-spécifiques

Pour ajouter des prompts propres à un projet sans toucher au submodule, créer un dossier séparé dans le projet :

```
.github/
  copilot-custom/        ← submodule (ce repo, ne pas modifier)
  prompts/               ← prompts spécifiques au projet (dans le git du projet)
    my-custom-prompt.md
```

Usage :
```
@.github/prompts/my-custom-prompt.md
```

## Mise à jour du framework

```bash
git submodule update --remote .github/copilot-custom
```

## Prérequis

- [GitHub Copilot CLI](https://docs.github.com/copilot/concepts/agents/about-copilot-cli)
- [AIDD](https://github.com/ai-driven-dev/aidd-framework) configuré dans le projet cible (`aidd_docs/` présent)
- `gh` CLI pour les prompts interagissant avec GitHub
