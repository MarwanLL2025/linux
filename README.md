Quand on administre des serveurs Linux, il faut pouvoir détecter rapidement une activité suspecte. Voici 5 commandes simples mais puissantes pour un audit rapide de sécurité ⤵️


🔍 1. Connexions réseau établies :


ss -tupln | grep ESTABLISHED

→ Surveillez les connexions vers des IP ou ports inhabituels.

🔥 2. Processus les plus gourmands en CPU


ps aux --sort=-%cpu | head -10

→ Un malware ou cryptomineur se cache souvent derrière une consommation CPU excessive, a utilisé sur le GPU également


🛠️ 3. Modifications récentes dans les fichiers système


find /etc -type f -mtime -7 -ls

→ Un fichier modifié récemment dans /etc sans justification = drapeau rouge 🚩


🚫 4. Tentatives d’authentification échouées


grep "Failed password" /var/log/auth.log | awk '{print 98 EUR}' | sort | uniq -c | sort -nr

→ Des IP qui échouent plusieurs fois ? Probable brute force 👀


📡 5. Ports ouverts et services associés

sudo lsof -i -P -n | grep LISTEN

→ Des ports ouverts inconnus ? Peut-être une backdoor...


👤 Bonus : Détecter les commandes passées par un autre root avec history

     cat /root/.bash_history | less

 ✅ Ce que ça fait : Affiche l’historique des commandes utilisées par le compte root.


     ls -l /root/.bash_history

→ Si la dernière modification ne correspond pas à ton dernier login root, c’est louche.
