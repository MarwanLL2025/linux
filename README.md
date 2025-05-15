🟨 Script Shell — check_suspicious.sh

#!/bin/bash
# Script d'audit rapide de sécurité Linux
# Auteur : EXE System

echo "=============================="
echo "🔍 Connexions réseau établies"
echo "=============================="
ss -tupln | grep ESTABLISHED

echo -e "\n=============================="
echo "🔥 Top 10 processus CPU"
echo "=============================="
ps aux --sort=-%cpu | head -10

echo -e "\n=============================="
echo "🛠️  Fichiers modifiés dans /etc (7 derniers jours)"
echo "=============================="
find /etc -type f -mtime -7 -ls

echo -e "\n=============================="
echo "🚫 IP avec échecs SSH (auth.log)"
echo "=============================="
grep "Failed password" /var/log/auth.log 2>/dev/null | awk '{print 98 EUR}' | sort | uniq -c | sort -nr

echo -e "\n=============================="
echo "📡 Ports ouverts et services"
echo "=============================="
sudo lsof -i -P -n | grep LISTEN


👉 Transform into executable file  :

chmod +x check_suspicious.sh
./check_suspicious.sh
