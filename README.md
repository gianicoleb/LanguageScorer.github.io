<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Language Learning Quiz</title>
  <style>
    body {
      font-family: Arial, sans-serif;
    }

    .container {
      max-width: 600px;
      margin: 0 auto;
      padding: 20px;
      text-align: center;
    }

    #question {
      margin-top: 20px;
    }

    button {
      margin: 10px;
    }
  </style>
</head>

<body>
  <div class="container">
    <h1>Language Learning Quiz</h1>
    <div>
      <label for="language">Select Language: </label>
      <select id="language">
        <option value="french">French</option>
        <option value="spanish">Spanish</option>
        <option value="german">German</option>
      </select>
      <button onclick="startQuiz()">Start Quiz</button>
    </div>
    <div id="quiz" style="display:none;">
      <p id="question"></p>
      <button onclick="submitAnswer('y')">Yes</button>
      <button onclick="submitAnswer('n')">No</button>
      <button onclick="goBack()">Back</button>
      <p id="score"></p>
    </div>
  </div>

  <script>
    const french = {
      "comme": "as",
      "je": "I",
      "son": "his",
      "que": "that",
      "il": "he",
      "était": "was",
      "pour": "for",
      "sur": "on",
      "sont": "are",
      "avec": "with",
      "ils": "they",
      "être": "be",
      "à": "at",
      "un": "one",
      "avoir": "have",
      "ce": "this",
      "à partir de": "from",
      "par": "by",
      "chaud": "hot",
      "mot": "word",
      "mais": "but",
      "que": "what",
      "certains": "some",
      "est": "is",
      "il": "it",
      "vous": "you",
      "ou": "or",
      "eu": "had",
      "la": "the",
      "de": "of",
      "à": "to",
      "et": "and",
      "un": "a",
      "dans": "in",
      "nous": "we",
      "boîte": "can",
      "dehors": "out",
      "autre": "other",
      "étaient": "were",
      "qui": "which",
      "faire": "do",
      "leur": "their",
      "temps": "time",
      "si": "if",
      "volonté": "will",
      "comment": "how",
      "dit": "said",
      "un": "an",
      "chaque": "each",
      "dire": "tell",
      "ne": "does",
      "ensemble": "set",
      "trois": "three",
      "vouloir": "want",
      "air": "air",
      "bien": "well",
      "aussi": "also",
      "jouer": "play",
      "petit": "small",
      "fin": "end",
      "mettre": "put",
      "maison": "home",
      "lire": "read",
      "main": "hand",
      "port": "port",
      "grand": "large",
      "épeler": "spell",
      "ajouter": "add",
      "même": "even",
      "terre": "land",
      "ici": "here",
      "il faut": "must",
      "grand": "big",
      "haut": "high",
      "tel": "such",
      "suivre": "follow",
      "acte": "act",
      "pourquoi": "why",
      "interroger": "ask",
      "hommes": "men",
      "changement": "change",
      "est allé": "went",
      "lumière": "light",
      "genre": "kind",
      "de": "off",
      "besoin": "need",
      "maison": "house",
      "image": "picture",
      "essayer": "try",
      "nous": "us",
      "encore": "again",
      "animal": "animal",
      "point": "point",
      "mère": "mother",
      "monde": "world",
      "près de": "near",
      "construire": "build",
      "soi": "self",
      "terre": "earth",
      "père": "father",
      "tout": "any",
      "nouveau": "new",
      "travail": "work",
      "partie": "part",
      "prendre": "take",
      "obtenir": "get",
      "lieu": "place",
      "fabriqué": "made",
      "vivre": "live",
      "où": "where",
      "après": "after",
      "arrière": "back",
      "peu": "little",
      "seulement": "only",
      "tour": "round",
      "homme": "man",
      "année": "year",
      "est venu": "came",
      "montrer": "show",
      "tous": "every",
      "bon": "good",
      "moi": "me",
      "donner": "give",
      "notre": "our",
      "sous": "under",
      "nom": "name",
      "très": "very",
      "par": "through",
      "juste": "just",
      "forme": "form",
      "phrase": "sentence",
      "grand": "great",
      "penser": "think",
      "dire": "say",
      "aider": "help",
      "faible": "low",
      "ligne": "line",
      "différer": "differ",
      "tour": "turn",
      "la cause": "cause",
      "beaucoup": "much",
      "signifier": "mean",
      "avant": "before",
      "déménagement": "move",
      "droit": "right",
      "garçon": "boy",
      "vieux": "old",
      "trop": "too",
      "même": "same",
      "elle": "she",
      "tous": "all",
      "là": "there",
      "quand": "when",
      "jusqu’à": "up",
      "utiliser": "use",
      "votre": "your",
      "manière": "way",
      "sur": "about",
      "beaucoup": "many",
      "puis": "then",
      "les": "them",
      "écrire": "write",
      "voudrais": "would",
      "comme": "like",
      "si": "so",
      "ces": "these",
      "son": "her",
      "long": "long",
      "faire": "make",
      "chose": "thing",
      "voir": "see",
      "lui": "him",
      "deux": "two",
      "a": "has",
      "regarder": "look",
      "plus": "more",
      "jour": "day",
      "pourrait": "could",
      "aller": "go",
      "venir": "come",
      "fait": "did",
      "nombre": "number",
      "son": "sound",
      "aucun": "no",
      "plus": "most",
      "personnes": "people",
      "ma": "my",
      "sur": "over",
      "savoir": "know",
      "eau": "water",
      "que": "than",
      "appel": "call",
      "première": "first",
      "qui": "who",
      "peut": "may",
      "vers le bas": "down",
      "côté": "side",
      "été": "been",
      "maintenant": "now",
      "trouver": "find",
      "tête": "head",
      "supporter": "stand",
      "propre": "own",
      "page": "page",
      "devrait": "should",
      "pays": "country",
      "trouvé": "found",
      "réponse": "answer",
      "école": "school",
      "croître": "grow",
      "étude": "study",
      "encore": "still",
      "apprendre": "learn",
      "usine": "plant",
      "couvercle": "cover",
      "nourriture": "food",
      "soleil": "sun",
      "quatre": "four",
      "entre": "between",
      "état": "state",
      "garder": "keep",
      "œil": "eye",
      "jamais": "never",
      "dernier": "last",
      "laisser": "let",
      "pensée": "thought",
      "ville": "city",
      "arbre": "tree",
      "traverser": "cross",
      "ferme": "farm",
      "dur": "hard",
      "début": "start",
      "puissance": "might",
      "histoire": "story",
      "scie": "saw",
      "loin": "far",
      "mer": "sea",
      "tirer": "draw",
      "gauche": "left",
      "tard": "late",
      "courir": "run",
      "needs a context": "don’t",
      "tandis que": "while",
      "presse": "press",
      "proche": "close",
      "nuit": "night",
      "réel": "real",
      "vie": "life",
      "peu": "few",
      "nord": "north",
      "livre": "book",
      "porter": "carry",
      "a pris": "took",
      "science": "science",
      "manger": "eat",
      "chambre": "room",
      "ami": "friend",
      "a commencé": "began",
      "idée": "idea",
      "poisson": "fish",
      "montagne": "mountain",
      "Arrêtez": "stop",
      "une fois": "once",
      "base": "base",
      "entendre": "hear",
      "cheval": "horse",
      "coupe": "cut",
      "sûr": "sure",
      "regarder": "watch",
      "couleur": "color",
      "face": "face",
      "bois": "wood",
      "principal": "main",
      "ouvert": "open",
      "paraître": "seem",
      "ensemble": "together",
      "suivant": "next",
      "blanc": "white",
      "enfants": "children",
      "commencer": "begin",
      "eu": "got",
      "marcher": "walk",
      "exemple": "example",
      "facilité": "ease",
      "papier": "paper",
      "groupe": "group",
      "toujours": "always",
      "musique": "music",
      "ceux": "those",
      "tous les deux": "both",
      "marque": "mark",
      "souvent": "often",
      "lettre": "letter",
      "jusqu’à ce que": "until",
      "mile": "mile",
      "rivière": "river",
      "voiture": "car",
      "pieds": "feet",
      "soins": "care",
      "deuxième": "second",
      "assez": "enough",
      "plaine": "plain",
      "fille": "girl",
      "habituel": "usual",
      "jeune": "young",
      "prêt": "ready",
      "au-dessus": "above",
      "jamais": "ever",
      "rouge": "red",
      "liste": "list",
      "bien que": "though",
      "sentir": "feel",
      "parler": "talk",
      "oiseau": "bird",
      "bientôt": "soon",
      "corps": "body",
      "chien": "dog",
      "famille": "family",
      "direct": "direct",
      "pose": "pose",
      "laisser": "leave",
      "chanson": "song",
      "mesurer": "measure",
      "porte": "door",
      "produit": "product",
      "noir": "black",
      "court": "short",
      "chiffre": "numeral",
      "classe": "class",
      "vent": "wind",
      "question": "question",
      "arriver": "happen",
      "complète": "complete",
      "navire": "ship",
      "zone": "area",
      "moitié": "half",
      "rock": "rock",
      "ordre": "order",
      "feu": "fire",
      "sud": "south",
      "problème": "problem",
      "pièce": "piece",
      "dit": "told",
      "savait": "knew",
      "passer": "pass",
      "depuis": "since",
      "haut": "top",
      "ensemble": "whole",
      "roi": "king",
      "rue": "street",
      "pouce": "inch",
      "multiplier": "multiply",
      "rien": "nothing",
      "cours": "course",
      "rester": "stay",
      "roue": "wheel",
      "plein": "full",
      "force": "force",
      "bleu": "blue",
      "objet": "object",
      "décider": "decide",
      "surface": "surface",
      "profond": "deep",
      "lune": "moon",
      "île": "island",
      "pied": "foot",
      "système": "system",
      "occupé": "busy",
      "test": "test",
      "record": "record",
      "bateau": "boat",
      "commun": "common",
      "or": "gold",
      "possible": "possible",
      "plan": "plane",
      "place": "stead",
      "sec": "dry",
      "se demander": "wonder",
      "rire": "laugh",
      "mille": "thousand",
      "il ya": "ago",
      "ran": "ran",
      "vérifier": "check",
      "jeu": "game",
      "forme": "shape",
      "assimiler": "equate",
      "chaud": "hot",
      "manquer": "miss",
      "apporté": "brought",
      "chaleur": "heat",
      "neige": "snow",
      "pneu": "tire",
      "apporter": "bring",
      "oui": "yes",
      "lointain": "distant",
      "remplir": "fill",
      "est": "east",
      "peindre": "paint",
      "langue": "language",
      "entre": "among",
      "unité": "unit",
      "puissance": "power",
      "ville": "town",
      "fin": "fine",
      "certain": "certain",
      "voler": "fly",
      "tomber": "fall",
      "conduire": "lead",
      "cri": "cry",
      "sombre": "dark",
      "machine": "machine",
      "Note": "note",
      "patienter": "wait",
      "plan": "plan",
      "figure": "figure",
      "étoile": "star",
      "boîte": "box",
      "nom": "noun",
      "domaine": "field",
      "reste": "rest",
      "correct": "correct",
      "capable": "able",
      "livre": "pound",
      "Terminé": "done",
      "beauté": "beauty",
      "entraînement": "drive",
      "résisté": "stood",
      "contenir": "contain",
      "avant": "front",
      "enseigner": "teach",
      "semaine": "week",
      "finale": "final",
      "donné": "gave",
      "vert": "green",
      "oh": "oh",
      "rapide": "quick",
      "développer": "develop",
      "océan": "ocean",
      "chaud": "warm",
      "gratuit": "free",
      "minute": "minute",
      "fort": "strong",
      "spécial": "special",
      "esprit": "mind",
      "derrière": "behind",
      "clair": "clear",
      "queue": "tail",
      "produire": "produce",
      "fait": "fact",
      "espace": "space",
      "entendu": "heard",
      "meilleur": "best",
      "heure": "hour",
      "mieux": "better",
      "vrai": "true",
      "pendant": "during",
      "cent": "hundred",
      "cinq": "five",
      "rappeler": "remember",
      "étape": "step",
      "tôt": "early",
      "tenir": "hold",
      "ouest": "west",
      "sol": "ground",
      "intérêt": "interest",
      "atteindre": "reach",
      "rapide": "fast",
      "verbe": "verb",
      "chanter": "sing",
      "écouter": "listen",
      "six": "six",
      "table": "table",
      "Voyage": "travel",
      "moins": "less",
      "matin": "morning",
      "dix": "ten",
      "simple": "simple",
      "plusieurs": "several",
      "voyelle": "vowel",
      "vers": "toward",
      "guerre": "war",
      "poser": "lay",
      "contre": "against",
      "modèle": "pattern",
      "lent": "slow",
      "centre": "center",
      "amour": "love",
      "personne": "person",
      "argent": "money",
      "servir": "serve",
      "apparaître": "appear",
      "route": "road",
      "carte": "map",
      "pluie": "rain",
      "règle": "rule",
      "gouverner": "govern",
      "tirer": "pull",
      "froid": "cold",
      "avis": "notice",
      "voix": "voice",
      "énergie": "energy",
      "chasse": "hunt",
      "probable": "probable",
      "lit": "bed",
      "frère": "brother",
      "œuf": "egg",
      "tour": "ride",
      "cellule": "cell",
      "croire": "believe",
      "peut-être": "perhaps",
      "choisir": "pick",
      "soudain": "sudden",
      "compter": "count",
      "carré": "square",
      "raison": "reason",
      "longueur": "length",
      "représenter": "represent",
      "art": "art",
      "sujet": "subject",
      "région": "region",
      "taille": "size",
      "varier": "vary",
      "régler": "settle",
      "parler": "speak",
      "poids": "weight",
      "général": "general",
      "glace": "ice",
      "question": "matter",
      "cercle": "circle",
      "paire": "pair",
      "inclure": "include",
      "fracture": "divide",
      "syllabe": "syllable",
      "feutre": "felt",
      "grandiose": "grand",
      "balle": "ball",
      "encore": "yet",
      "vague": "wave",
      "tomber": "drop",
      "cœur": "heart",
      "h": "am",
      "présent": "present",
      "lourd": "heavy",
      "danse": "dance",
      "moteur": "engine",
      "position": "position",
      "bras": "arm",
      "large": "wide",
      "voile": "sail",
      "matériel": "material",
      "fraction": "fraction",
      "forêt": "forest",
      "s’asseoir": "sit",
      "course": "race",
      "fenêtre": "window",
      "magasin": "store",
      "été": "summer",
      "train": "train",
      "sommeil": "sleep",
      "prouver": "prove",
      "seul": "lone",
      "jambe": "leg",
      "exercice": "exercise",
      "mur": "wall",
      "capture": "catch",
      "monture": "mount",
      "souhaiter": "wish",
      "ciel": "sky",
      "conseil": "board",
      "joie": "joy",
      "hiver": "winter",
      "sat": "sat",
      "écrit": "written",
      "sauvage": "wild",
      "instrument": "instrument",
      "conservé": "kept",
      "verre": "glass",
      "herbe": "grass",
      "vache": "cow",
      "emploi": "job",
      "bord": "edge",
      "signe": "sign",
      "visite": "visit",
      "passé": "past",
      "doux": "soft",
      "amusement": "fun",
      "clair": "bright",
      "gaz": "gas",
      "temps": "weather",
      "mois": "month",
      "million": "million",
      "porter": "bear",
      "finition": "finish",
      "heureux": "happy",
      "espoir": "hope",
      "fleur": "flower",
      "vêtir": "clothe",
      "étrange": "strange",
      "disparu": "gone",
      "commerce": "trade",
      "mélodie": "melody",
      "voyage": "trip",
      "bureau": "office",
      "recevoir": "receive",
      "rangée": "row",
      "bouche": "mouth",
      "exact": "exact",
      "symbole": "symbol",
      "mourir": "die",
      "moins": "least",
      "difficulté": "trouble",
      "cri": "shout",
      "sauf": "except",
      "écrit": "wrote",
      "semence": "seed",
      "ton": "tone",
      "joindre": "join",
      "suggérer": "suggest",
      "propre": "clean",
      "pause": "break",
      "dame": "lady",
      "cour": "yard",
      "augmenter": "rise",
      "mauvais": "bad",
      "coup": "blow",
      "huile": "oil",
      "sang": "blood",
      "toucher": "touch",
      "a augmenté": "grew",
      "cent": "cent",
      "mélanger": "mix",
      "équipe": "team",
      "fil": "wire",
      "coût": "cost",
      "perdu": "lost",
      "brun": "brown",
      "porter": "wear",
      "jardin": "garden",
      "égal": "equal",
      "expédié": "sent",
      "choisir": "choose",
      "est tombé": "fell",
      "s’adapter": "fit",
      "débit": "flow",
      "juste": "fair",
      "banque": "bank",
      "recueillir": "collect",
      "sauver": "save",
      "contrôle": "control",
      "décimal": "decimal",
      "oreille": "ear",
      "autre": "else",
      "tout à fait": "quite",
      "cassé": "broke",
      "cas": "case",
      "milieu": "middle",
      "tuer": "kill",
      "fils": "son",
      "lac": "lake",
      "moment": "moment",
      "échelle": "scale",
      "fort": "loud",
      "printemps": "spring",
      "observer": "observe",
      "enfant": "child",
      "droit": "straight",
      "consonne": "consonant",
      "nation": "nation",
      "dictionnaire": "dictionary",
      "lait": "milk",
      "vitesse": "speed",
      "méthode": "method",
      "organe": "organ",
      "payer": "pay",
      "âge": "age",
      "section": "section",
      "robe": "dress",
      "nuage": "cloud",
      "surprise": "surprise",
      "calme": "quiet",
      "pierre": "stone",
      "minuscule": "tiny",
      "montée": "climb",
      "frais": "cool",
      "conception": "design",
      "pauvres": "poor",
      "lot": "lot",
      "expérience": "experiment",
      "bas": "bottom",
      "clé": "key",
      "fer": "iron",
      "unique": "single",
      "bâton": "stick",
      "plat": "flat",
      "vingt": "twenty",
      "peau": "skin",
      "sourire": "smile",
      "pli": "crease",
      "trou": "hole",
      "sauter": "jump",
      "bébé": "baby",
      "huit": "eight",
      "village": "village",
      "se rencontrent": "meet",
      "racine": "root",
      "acheter": "buy",
      "augmenter": "raise",
      "résoudre": "solve",
      "métal": "metal",
      "si": "whether",
      "pousser": "push",
      "sept": "seven",
      "paragraphe": "paragraph",
      "troisième": "third",
      "doit": "shall",
      "en attente": "held",
      "cheveux": "hair",
      "décrire": "describe",
      "cuisinier": "cook",
      "étage": "floor",
      "chaque": "either",
      "résultat": "result",
      "brûler": "burn",
      "colline": "hill",
      "coffre-fort": "safe",
      "chat": "cat",
      "siècle": "century",
      "envisager": "consider",
      "type": "type",
      "droit": "law",
      "peu": "bit",
      "côte": "coast",
      "copie": "copy",
      "phrase": "phrase",
      "silencieux": "silent",
      "haut": "tall",
      "sable": "sand",
      "sol": "soil",
      "rouleau": "roll",
      "température": "temperature",
      "doigt": "finger",
      "industrie": "industry",
      "valeur": "value",
      "lutte": "fight",
      "mensonge": "lie",
      "battre": "beat",
      "exciter": "excite",
      "naturel": "natural",
      "vue": "view",
      "sens": "sense",
      "capital": "capital",
      "ne sera pas": "won’t",
      "chaise": "chair",
      "danger": "danger",
      "fruit": "fruit",
      "riche": "rich",
      "épais": "thick",
      "soldat": "soldier",
      "processus": "process",
      "fonctionner": "operate",
      "pratique": "practice",
      "séparé": "separate",
      "difficile": "difficult",
      "médecin": "doctor",
      "s’il vous plaît": "please",
      "protéger": "protect",
      "midi": "noon",
      "récolte": "crop",
      "moderne": "modern",
      "élément": "element",
      "frapper": "hit",
      "étudiant": "student",
      "coin": "corner",
      "partie": "party",
      "alimentation": "supply",
      "dont": "whose",
      "localiser": "locate",
      "anneau": "ring",
      "caractère": "character",
      "insecte": "insect",
      "pris": "caught",
      "période": "period",
      "indiquer": "indicate",
      "radio": "radio",
      "rayon": "spoke",
      "atome": "atom",
      "humain": "human",
      "histoire": "history",
      "effet": "effect",
      "électrique": "electric",
      "attendre": "expect",
      "os": "bone",
      "rail": "rail",
      "imaginer": "imagine",
      "fournir": "provide",
      "se mettre d’accord": "agree",
      "ainsi": "thus",
      "doux": "gentle",
      "femme": "woman",
      "capitaine": "captain",
      "deviner": "guess",
      "nécessaire": "necessary",
      "net": "sharp",
      "aile": "wing",
      "créer": "create",
      "voisin": "neighbor",
      "lavage": "wash",
      "chauve-souris": "bat",
      "plutôt": "rather",
      "foule": "crowd",
      "blé": "corn",
      "comparer": "compare",
      "poème": "poem",
      "chaîne": "string",
      "cloche": "bell",
      "dépendre": "depend",
      "viande": "meat",
      "rub": "rub",
      "tube": "tube",
      "célèbre": "famous",
      "dollar": "dollar",
      "courant": "stream",
      "peur": "fear",
      "vue": "sight",
      "mince": "thin",
      "triangle": "triangle",
      "planète": "planet",
      "se dépêcher": "hurry",
      "chef": "chief",
      "colonie": "colony",
      "horloge": "clock",
      "mine": "mine",
      "lien": "tie",
      "entrer": "enter",
      "majeur": "major",
      "frais": "fresh",
      "recherche": "search",
      "envoyer": "send",
      "jaune": "yellow",
      "pistolet": "gun",
      "permettre": "allow",
      "impression": "print",
      "mort": "dead",
      "place": "spot",
      "désert": "desert",
      "costume": "suit",
      "courant": "current",
      "ascenseur": "lift",
      "rose": "rose",
      "arriver": "arrive",
      "maître": "master",
      "piste": "track",
      "mère": "parent",
      "rivage": "shore",
      "division": "division",
      "feuille": "sheet",
      "substance": "substance",
      "favoriser": "favor",
      "relier": "connect",
      "poste": "post",
      "passer": "spend",
      "corde": "chord",
      "graisse": "fat",
      "heureux": "glad",
      "original": "original",
      "part": "share",
      "station": "station",
      "papa": "dad",
      "pain": "bread",
      "charger": "charge",
      "propre": "proper",
      "bar": "bar",
      "proposition": "offer",
      "segment": "segment",
      "esclave": "slave",
      "canard": "duck",
      "instant": "instant",
      "marché": "market",
      "degré": "degree",
      "peupler": "populate",
      "poussin": "chick",
      "cher": "dear",
      "ennemi": "enemy",
      "répondre": "reply",
      "boisson": "drink",
      "se produire": "occur",
      "support": "support",
      "discours": "speech",
      "nature": "nature",
      "gamme": "range",
      "vapeur": "steam",
      "mouvement": "motion",
      "chemin": "path",
      "liquide": "liquid",
      "enregistrer": "log",
      "signifiait": "meant",
      "quotient": "quotient",
      "dents": "teeth",
      "coquille": "shell",
      "cou": "neck",
      "oxygène": "oxygen",
      "sucre": "sugar",
      "décès": "death",
      "assez": "pretty",
      "compétence": "skill",
      "femmes": "women",
      "saison": "season",
      "solution": "solution",
      "aimant": "magnet",
      "argent": "silver",
      "merci": "thank",
      "branche": "branch",
      "rencontre": "match",
      "suffixe": "suffix",
      "particulièrement": "especially",
      "figue": "fig",
      "peur": "afraid",
      "énorme": "huge",
      "sœur": "sister",
      "acier": "steel",
      "discuter": "discuss",
      "avant": "forward",
      "similaire": "similar",
      "guider": "guide",
      "expérience": "experience",
      "score": "score",
      "pomme": "apple",
      "acheté": "bought",
      "LED": "led",
      "pas": "pitch",
      "manteau": "coat",
      "masse": "mass",
      "carte": "card",
      "bande": "band",
      "corde": "rope",
      "glissement": "slip",
      "gagner": "win",
      "rêver": "dream",
      "soirée": "evening",
      "condition": "condition",
      "alimentation": "feed",
      "outil": "tool",
      "total": "total",
      "de base": "basic",
      "odeur": "smell",
      "vallée": "valley",
      "ni": "nor",
      "double": "double",
      "siège": "seat",
      "continuer": "continue",
      "bloc": "block",
      "graphique": "chart",
      "chapeau": "hat",
      "vendre": "sell",
      "succès": "success",
      "entreprise": "company",
      "soustraire": "subtract",
      "événement": "event",
      "particulier": "particular",
      "accord": "deal",
      "baignade": "swim",
      "terme": "term",
      "opposé": "opposite",
      "femme": "wife",
      "chaussure": "shoe",
      "épaule": "shoulder",
      "propagation": "spread",
      "organiser": "arrange",
      "camp": "camp",
      "inventer": "invent",
      "coton": "cotton",
      "né": "born",
      "déterminer": "determine",
      "litre": "quart",
      "neuf": "nine",
      "camion": "truck",
      "bruit": "noise",
      "niveau": "level",
      "chance": "chance",
      "recueillir": "gather",
      "boutique": "shop",
      "tronçon": "stretch",
      "jeter": "throw",
      "éclat": "shine",
      "propriété": "property",
      "colonne": "column",
      "molécule": "molecule",
      "sélectionner": "select",
      "mal": "wrong",
      "gris": "gray",
      "répétition": "repeat",
      "exiger": "require",
      "large": "broad",
      "préparer": "prepare",
      "sel": "salt",
      "nez": "nose",
      "pluriel": "plural",
      "colère": "anger",
      "revendication": "claim",
      "continent": "continent"

    };

    const spanish = {

    };

    const german = {

    };

    let words = {};
    let incorrect = [];
    let correctcount = 0;
    let count = 0;
    let score = 0;
    let answers = [];
    let currentIndex = 0;

    function startQuiz() {
      const language = document.getElementById('language').value;
      if (language === 'french') {
        words = french;
      } else if (language === 'spanish') {
        words = spanish;
      } else if (language === 'german') {
        words = german;
      } else {
        alert("Invalid language selection.");
        return;
      }

      document.getElementById('quiz').style.display = 'block';
      showNextWord();
    }

    function showNextWord() {
      const keys = Object.keys(words);
      if (currentIndex < keys.length) {
        document.getElementById('question').textContent = `Word ${currentIndex + 1}: Do you know this word: ${keys[currentIndex]}?`;
      } else {
        endQuiz();
      }
    }

    function submitAnswer(answer) {
      const keys = Object.keys(words);
      if (answer === 'y') {
        correctcount++;
        answers.push('y');
      } else if (answer === 'n') {
        incorrect.push(keys[currentIndex]);
        answers.push('n');
      }
      count++;
      currentIndex++;
      score = (correctcount / count) * 100;
      document.getElementById('score').textContent = `Current score: ${score.toFixed(2)}%`;

      if (count > 10 && score <= 75) {
        alert(`COMPLETE. 75% at word ${currentIndex + 1}`);
        endQuiz();
      } else {
        showNextWord();
      }
    }

    function goBack() {
      if (currentIndex > 0) {
        currentIndex--;
        const lastAnswer = answers.pop();

        if (lastAnswer === 'n' && incorrect.length > 0) {
          incorrect.pop();
        } else if (lastAnswer === 'y') {
          correctcount--;
        }

        count--;
        score = (correctcount / count) * 100;
        document.getElementById('score').textContent = `Current score: ${score.toFixed(2)}%`;

        showNextWord();
      }
    }

    function endQuiz() {
      document.getElementById('question').textContent = `Final score: ${score.toFixed(2)}%`;
      document.getElementById('score').textContent = `Incorrect words: ${incorrect.join(', ')}`;
    }
  </script>
</body>

</html>
