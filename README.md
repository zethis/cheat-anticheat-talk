# 🎙️ Talk : Cheat & Anticheat

**1. Introduction & Contexte** `(00:00 – 03:00)`
* **Présentation :** Mon Rôle chez FACEIT (EFG).
* **Le Mythe du "Silver Bullet" :** Il n'y a pas de solution miracle. C'est un "jeu du chat et de la souris" (*cat and mouse game*) infini.
* **L'Objectif :** L'anti-cheat ne sert pas juste à bannir, mais à augmenter la "friction" (rendre le coût du développement et l'achat de cheats trop élevé/complexe pour la majorité).

**2. L'Ère "Legacy" (Les Cheats Logiciels)** `(03:00 – 08:00)`
* **Comment ça marchait avant :**
    * *Internal :* On injecte une `.dll` dans le processus du jeu.
    * *External :* Un programme externe qui lit la mémoire (`ReadProcessMemory`).
* **La réponse Anti-Cheat :** C'était l'époque des signatures de fichiers et du scan de processus.
* **Pourquoi ça ne suffit plus :** Les AC ont gagné la bataille logicielle sur l'OS (User-mode), forçant les tricheurs à aller plus loin, vers le Kernel (Noyau) et le Hardware.

**3. L'Ère Moderne : Hardware, Firmware & DMA** `(08:00 – 16:00)`
* **Le "Nouveau" standard de triche :**
    * **DMA (Direct Memory Access) :** Utilisation d'une 2ème carte PC/PCIe qui lit la mémoire sans que le CPU principal ne le "sache".
    * **Firmware/EFI :** Les cheats cachés dans le BIOS/UEFI qui se chargent *avant* Windows.
* **La Réponse FACEIT/RIOT (Points clés de l'AMA) :**
    * Pourquoi on demande **Secure Boot**, **TPM 2.0** et l'**IOMMU**.
* **🏠 L'Analogie de la Maison :**
    * *TPM/Secure Boot :* On vérifie la maison avant que la fête commence (personne n'est caché sous le lit).
    * *IOMMU :* C'est le "vigile" à l'intérieur. Il empêche les périphériques (comme une carte DMA) d'entrer dans les pièces interdites (la mémoire du jeu).
* **Résultat :** Depuis ces protections, beaucoup de vendeurs DMA ne prétendent plus être "Undetected" sur FACEIT.

**4. Le Futur : L'IA contre L'IA** `(16:00 – 24:00)`
* **La Menace (Cheats IA / Computer Vision) :**
    * Ils ne lisent plus la mémoire (indétectable par DMA classique).
    * Ils "regardent" l'écran (YOLO, reconnaissance d'image) et simulent la souris.
* **La Solution (AC IA & Comportemental) :**
    * **Server-Side Analysis :** Analyser le résultat (mouvement curseur, temps de réaction humain vs machine).
    * **Réalité :** L'IA est un outil puissant pour *flagger* (détecter), mais elle génère des probabilités.
* **Pourquoi le Kernel reste nécessaire :** Pour bannir avec certitude, il faut vérifier si l'input vient d'une vraie souris ou d'un logiciel. L'approche hybride (Kernel + IA) est nécessaire.

**5. Conclusion : Identité & Confiance** `(24:00 – Fin)`
* **Au-delà du Cheat :** Le problème du Smurfing.
* **La Solution :** La Vérification d'Identité (ID Verification). Le but est de bannir les *personnes*, pas juste les comptes.
* **Message de fin :** FACEIT investit pour garantir l'intégrité compétitive. Si tu perds, c'est parce que l'autre était meilleur, pas parce qu'il avait un meilleur logiciel.
