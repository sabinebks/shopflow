# Medusa

Base de boutique en ligne associant un backend **Medusa** et une vitrine **Next.js** : catalogue, panier, commande et espace client.

> **Origine :** fork de [Medusa DTC Starter](https://github.com/medusajs/dtc-starter), sous licence MIT. Ce dépôt est une base open source en cours d’appropriation par **Boukais Sabine**. Les fonctionnalités commerciales proviennent des auteurs de Medusa ; aucune personnalisation fonctionnelle de Sabine n’a été identifiée dans les sources fournies.

## Fonctionnalités présentes

- Catalogue de produits, variantes, collections et catégories.
- Panier, codes promotionnels et parcours de commande avec livraison et paiement.
- Comptes clients, adresses, historique des commandes et transfert de commande.
- Gestion de plusieurs régions et interface d’administration Medusa.

## Technologies

TypeScript · Medusa 2 · Next.js 15 · React · Tailwind CSS · PostgreSQL · pnpm · Turborepo.

## Installation et lancement

Prérequis : **Node.js 22.22.0 ou supérieur**, **pnpm 10.11.1** (version du `packageManager`) et **PostgreSQL 15+**. La version Node indiquée ici suit les `package.json` fournis.

```bash
git clone https://github.com/sabinebks/medusa.git
cd medusa
pnpm install
```

1. Copier `apps/backend/.env.template` vers `apps/backend/.env`. Renseigner `DATABASE_URL`, les origines CORS et des valeurs personnelles pour `JWT_SECRET` et `COOKIE_SECRET`. Les valeurs du template servent d’exemples de développement.
2. Créer la base PostgreSQL désignée par `DATABASE_URL`, puis appliquer les migrations depuis `apps/backend` :

   ```bash
   pnpm exec medusa db:migrate
   pnpm exec medusa user --help
   ```

   Créer ensuite son compte administrateur avec la commande `medusa user` et ses propres identifiants, suivant cette aide.
3. Depuis la racine, lancer le backend :

   ```bash
   pnpm run backend:dev
   ```

4. Ouvrir l’administration sur `http://localhost:9000/app` et créer ou récupérer une clé API publiable. Copier `apps/storefront/.env.template` vers `apps/storefront/.env.local`, puis renseigner `NEXT_PUBLIC_MEDUSA_PUBLISHABLE_KEY` et l’URL du backend.
5. Dans un second terminal, depuis la racine :

   ```bash
   pnpm run storefront:dev
   ```

La vitrine est disponible sur `http://localhost:8000`. Une fois les deux applications configurées, `pnpm run dev` les lance ensemble. Le catalogue dépend des données de la base ; cette publication ne crée pas de boutique hébergée.

## Repères et documentation

| Chemin | Rôle |
| --- | --- |
| `apps/backend` | Backend et administration Medusa |
| `apps/storefront` | Vitrine Next.js |
| `apps/backend/medusa-config.ts` | Connexion à la base et configuration HTTP |

La [documentation d’origine](docs/amont/README.md) est conservée avec ses ressources et options de configuration. Pour démarrer cette copie, suivre les versions et chemins corrigés ci-dessus : le fichier de configuration est bien `apps/backend/.env`.

## Origine et vérification

- Auteurs du socle : Medusa et ses contributeurs ; [licence MIT](LICENSE) conservée.
- Préparation de ce portfolio : présentation en français, documentation du lancement et attribution de la base d’origine.
- Sources et scripts examinés. L’application, les paiements et les tests nécessitant PostgreSQL n’ont pas été exécutés lors de cette publication.
