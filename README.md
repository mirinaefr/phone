# callmeparis. — site corrigé

**23,4 Mo → 236 Ko.** Soit environ **100 fois plus léger**, et enfin visible sur Google, Naver et KakaoTalk.

---

## 📦 Contenu du dossier

```
index.html          ← la page complète (87 Ko, autonome : CSS + JS inclus)
robots.txt          ← pour Google / Naver / Daum
sitemap.xml         ← plan du site
assets/
  ├── prof.webp     ← ta photo (0,52 Mo → 20 Ko)
  ├── prof.jpg      ← version de secours (38 Ko)
  ├── og-image.png  ← vignette de partage KakaoTalk / Meta (1200×630)
  ├── favicon.png
  ├── apple-touch-icon.png
  └── voice-sample.mp3   ⚠️ À AJOUTER TOI-MÊME (voir plus bas)
```

## 🚀 Déploiement

Remplace tout le contenu de ton dépôt GitHub Pages par ce dossier, puis :

```bash
git add -A
git commit -m "Refonte : 23,4 Mo -> 236 Ko, SEO + Open Graph + comparatif + garantie"
git push
```

Garde bien ton fichier `CNAME` s'il existe déjà à la racine du dépôt.

---

## ✅ Ce qui a été corrigé

### Technique — c'était le vrai blocage

| Avant | Après |
|---|---|
| 23,4 Mo à télécharger avant le moindre pixel | **236 Ko** au total |
| 18 fichiers de police intégrés en base64 (17 Mo) | Pretendard via CDN, sous-ensemble dynamique (quelques Ko) |
| React + ReactDOM + **Babel Standalone** (~3 Mo) chargés depuis unpkg, transpilation dans le navigateur | **Zéro dépendance.** HTML statique + ~90 lignes de JavaScript natif |
| Contenu injecté par JS après décodage → invisible pour les robots | HTML servi directement, lisible par tous les crawlers |
| `<title>Bundled Page</title>` | Vrai titre optimisé pour `전화 프랑스어` |
| Pixel Meta déclenché après le décodage | Pixel dans le `<head>`, déclenché immédiatement + balise `<noscript>` |
| Photo PNG 0,52 Mo | WebP 20 Ko avec repli JPEG |

**Ajouté :** `lang="ko"`, meta description, canonical, favicon, Open Graph complet + image de partage, Twitter Card, `robots.txt`, `sitemap.xml`, et données structurées JSON-LD (Organisation + Service + **FAQPage** — la FAQ peut désormais apparaître directement dans les résultats Google).

### Persuasion

- **Comparatif 전화 / 화상 / 학원** — nouvelle section, 8 lignes, ta colonne mise en avant. Avec une note honnête en bas (« le présentiel a ses avantages ») : une comparaison qui reconnaît les limites de son propre camp est nettement plus crédible qu'une comparaison unilatérale.
- **Section « 등록 버튼을 누르면 이렇게 진행됩니다 »** — les 3 étapes après le clic (상담 → 일정 조율 → 첫 수업), avec la mention explicite « 바로 결제되지 않습니다 ». Enlève la peur de l'engagement immédiat.
- **Garantie « 첫 수업 만족 보장 »** — bloc dédié, repris dans le hero, dans la section CTA et dans la barre mobile. Formulée pour ne pas contredire ta FAQ : présentée comme une garantie commerciale *en plus* du barème légal, avec renvoi vers les CGU.
- **Bandeau de réassurance dans le hero** — garantie + « 카카오톡 상담부터 시작 » + horaires 10:00–22:00.
- **Lecteur audio** dans le hero (voir la section suivante).
- **Date limite sur la promo 15 %** — actuellement `~ 9월 30일까지`. **Change la date**, elle est en dur dans les deux cartes de cours.

### Bugs corrigés

1. « Read More » sur les cartes d'avis, qui ne cliquait nulle part → supprimé.
2. Bouton « retour en haut » invisible (`showTopBtn` n'existait pas) → réparé.
3. Compteur « 1만시간 » qui comptait de 0 à 1 → compte maintenant jusqu'à 10 000.
4. Icônes des statistiques déclarées mais jamais affichées → affichées.
5. Barre mobile à deux boutons concurrents → un bouton dominant (Kakao) + un lien compact (devis).
6. Pixel : chaque CTA a maintenant son propre identifiant `data-cta`, donc tu verras **quel bouton** génère les leads.

### Accessibilité et robustesse

- FAQ en `<details>/<summary>` natifs → fonctionne même sans JavaScript, navigable au clavier.
- `prefers-reduced-motion` respecté (les animations se coupent pour qui en a besoin).
- Tableau comparatif avec `<caption>` et `scope` corrects pour les lecteurs d'écran.
- Aucun blocage si le JS échoue : tout le contenu reste lisible.

---

## 🎧 Comment ajouter ta voix (la partie que tu demandais)

Le lecteur est **déjà intégré** dans le hero. Il cherche le fichier `assets/voice-sample.mp3`. S'il ne le trouve pas, il se cache tout seul — donc rien ne casse si tu déploies avant de l'avoir enregistré.

### 1. Enregistrer

Téléphone (Dictaphone sur iPhone, 녹음기 sur Android) ou Audacity sur ordinateur — les deux suffisent largement.

- Pièce silencieuse, sans écho. Évite la salle de bain et les grandes pièces vides.
- Micro à **20–25 cm** de la bouche, pas collé.
- **N'utilise pas le micro d'oreillettes Bluetooth** : la qualité est mauvaise, et l'enjeu ici est précisément de démontrer que tu es parfaitement audible.
- Vise **25 à 35 secondes**.

### 2. Le script

Le but n'est pas de « bien parler ». C'est de prouver trois choses en trente secondes : *ta prononciation est limpide*, *tu parles vraiment coréen*, *tu es une vraie personne sympathique*. Commence par « Allô ? » — le prospect entend littéralement à quoi ressemblera son premier cours.

> **[Français — lentement, chaleureux]**
> Allô ? Bonjour ! Ici Stanislas, de callmeparis.
> Je suis né à Paris, et depuis quatorze ans j'enseigne le français à des élèves coréens.
> Par téléphone, quinze minutes à la fois. Pas de caméra, pas de préparation :
> vous décrochez, et on parle.
>
> **[한국어]**
> 안녕하세요, 콜미파리 스타니슬라스입니다.
> 전화로 편하게 프랑스어 시작해 보세요. 기다리고 있겠습니다!

Parle un peu plus lentement que naturellement, mais **sans exagérer** — l'idée est de rassurer, pas de donner l'impression que tu t'adresses à un enfant.

### 3. Convertir en MP3

Si ton enregistrement est en `.m4a` (cas de l'iPhone), il faut le convertir. Deux options :

**En ligne** — [CloudConvert](https://cloudconvert.com/m4a-to-mp3), en trois clics.

**En ligne de commande**, si tu as ffmpeg :
```bash
ffmpeg -i enregistrement.m4a -ac 1 -b:a 96k -af "loudnorm" assets/voice-sample.mp3
```
`-ac 1` passe en mono (inutile en stéréo pour une voix) et `-b:a 96k` suffit amplement. Trente secondes donnent environ **350 Ko**. Reste **sous 500 Ko**.

### 4. Déposer le fichier

Place-le dans `assets/voice-sample.mp3`, pousse sur GitHub, et c'est fini. Le lecteur apparaît automatiquement, lit la durée réelle du fichier et l'affiche.

Un événement `VoiceSamplePlay` remonte dans ton Pixel à chaque écoute — tu sauras donc si les gens l'écoutent, et si ceux qui l'écoutent convertissent mieux.

> 💡 **Ajuste le libellé** si ton enregistrement ne fait pas 30 secondes : cherche `<em>30초</em>` dans `index.html`.

---

## ⚠️ Ce qu'il te reste à faire

### 1. Les prix (le plus important)

Chaque carte de cours contient un bloc prix **en commentaire**, prêt à activer. Cherche `⚠️ 가격 표시` dans `index.html` :

```html
<!-- ⚠️ 가격 표시 : 아래 줄의 주석을 풀고 실제 금액을 넣으세요 (강력 권장)
<div class="c-price">주 1회 15분 · <b>월 00,000원</b>부터</div>
-->
```

Retire les marqueurs `<!--` et `-->`, mets tes vrais montants. Je ne les ai pas inventés — mais une page sans aucun prix pousse le cerveau du visiteur à supposer « c'est cher », et le simulateur de devis ajoute une étape que beaucoup ne franchissent pas.

Le cours **여행 프랑스어** (60 min, une seule séance) est celui où afficher le prix rapportera le plus : c'est un achat d'impulsion avant un voyage.

### 2. La date de la promo

`~ 9월 30일까지` apparaît deux fois. Mets ta vraie échéance.

### 3. Le simulateur de devis

Il pointe toujours vers `mirinaefr.github.io/cmpdevis/`. Un visiteur coréen qui quitte `callmeparis.com` pour une URL `github.io` perd confiance. Crée un sous-domaine `devis.callmeparis.com` chez OVH (un simple CNAME vers `mirinaefr.github.io`), puis remplace les 4 occurrences du lien.

### 4. Après le déploiement — 15 minutes bien investies

- **Vignette KakaoTalk** : Kakao met les aperçus en cache. Force la mise à jour sur `developers.kakao.com/tool/debugger/sharing`.
- **Vignette Meta** : `developers.facebook.com/tools/debug/` → « Scrape Again ».
- **Google Search Console** : ajoute le site, soumets `sitemap.xml`, demande l'indexation de la page d'accueil.
- **Naver Search Advisor** (`searchadvisor.naver.com`) : même chose. C'est là que se trouvent tes clients, et c'est gratuit.
- **PageSpeed Insights** : teste `www.callmeparis.com` en mobile. Tu devrais passer d'un score catastrophique à quelque chose de très correct.

### 5. Le chiffre à vérifier dans Meta

Compare **« Clics sur un lien »** et **« Vues de page de destination »** sur ta campagne, avant et après ce déploiement. Si l'écart se resserre, tu auras la preuve chiffrée que le poids de la page te coûtait des clients depuis le début.

---

## 📊 Les événements Pixel disponibles

| Événement | Déclenché par |
|---|---|
| `PageView` | chargement de la page |
| `Lead` | clic sur un lien KakaoTalk — avec `content_name` : `nav`, `hero_primary`, `course_01`, `sticky_primary`… |
| `ViewContent` + `QuoteStart` | clic vers le simulateur de devis |
| `EchoClick` | clic vers la page Écho |
| `VoiceSamplePlay` | écoute de l'extrait audio |
| `Scroll50` / `Scroll75` / `Scroll90` | profondeur de lecture |

Dans le Gestionnaire d'événements, segmente `Lead` par `content_name` : tu sauras exactement quel bouton travaille et lequel ne sert à rien.

---

*Une dernière chose : ne remets jamais en ligne un export « bundle » de ce type. Ces fichiers sont faits pour prévisualiser une maquette, pas pour servir de site. C'est ce qui t'a coûté ces derniers mois.*
