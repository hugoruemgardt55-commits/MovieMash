# Déployer MovieMash — guide pas à pas (~30 min)

## Étape 1 — Créer la base de données (Supabase, gratuit)

1. Va sur https://supabase.com et crée un compte (gratuit, pas de CB requise).
2. Clique sur **New project**. Choisis un nom (ex: `moviemash`), un mot de passe de base de données (garde-le de côté), et une région proche de toi (ex: Europe West/Frankfurt).
3. Attends 1-2 minutes que le projet soit prêt.
4. Va dans l'onglet **SQL Editor** (icône dans le menu de gauche) > **New query**.
5. Colle tout le contenu du fichier `schema.sql` fourni, puis clique sur **Run**.
6. Va dans **Project Settings** (icône engrenage) > **API**.
   - Copie l'**URL du projet** (ressemble à `https://xxxxx.supabase.co`)
   - Copie la clé **anon public** (une longue chaîne de caractères)

## Étape 2 — Configurer le code

1. Ouvre le fichier `index.html`.
2. Trouve ces deux lignes tout en haut du `<script>` :
   ```js
   const SUPABASE_URL = "https://rddujgdhgxkansmazcqa.supabase.co/rest/v1/";
   const SUPABASE_ANON_KEY = "sb_publishable_LOztlk77N0NE3an9beeKgA_Z3EetKB0";
   ```
3. Remplace-les par l'URL et la clé copiées à l'étape précédente.
4. Sauvegarde le fichier.

## Étape 3 — Déployer (Vercel, gratuit)

**Option la plus simple — sans ligne de commande :**

1. Va sur https://vercel.com et crée un compte (tu peux te connecter avec GitHub, Google, ou email).
2. Une fois connecté, cherche le bouton pour importer/déployer un projet, puis l'option de déploiement par glisser-déposer ("drag and drop" / déploiement direct de fichiers, accessible depuis le dashboard Vercel ou via https://vercel.com/new).
3. Glisse le fichier `index.html` (et rien d'autre n'est nécessaire) dans la zone de dépôt.
4. Vercel te donne une URL du type `moviemash-xxxx.vercel.app` en quelques secondes. C'est en ligne.

**Option alternative si tu es à l'aise avec GitHub :**
1. Crée un repo GitHub, mets `index.html` dedans.
2. Sur Vercel, clique **New Project** > **Import Git Repository** > sélectionne ton repo.
3. Laisse les réglages par défaut (pas de build nécessaire, c'est un fichier statique) > **Deploy**.

## Étape 4 — Nom de domaine (optionnel, pour plus tard)

Si tu veux un nom personnalisé (ex: `moviemash.com` au lieu de `.vercel.app`) :
1. Achète un domaine (Namecheap, OVH, Google Domains — compte 10-15€/an).
2. Dans Vercel, va dans **Project Settings > Domains**, ajoute ton domaine.
3. Vercel te donne des enregistrements DNS à ajouter chez ton registrar. Une fois faits, ça propage en quelques minutes à quelques heures.

## Notes importantes

- **Sécurité MVP** : les règles Supabase sont ouvertes (n'importe qui peut voter ou tricher via l'API). C'est acceptable pour tester l'intérêt du concept, mais à durcir avant de scaler vraiment (voir les notes dans `schema.sql`).
- **Coûts** : Supabase et Vercel sont gratuits largement au-delà du trafic d'un lancement de test (limites généreuses sur le plan gratuit des deux).
- **Prochaine itération** : ajouter de vraies affiches (API TMDB, gratuite avec inscription), un compteur de vues, un partage social du classement.
