# [EN] Command lines for incident response cheat sheet // [FR] Memento de lignes de commande utiles en réponse à incident

# Linux 

## [EN] Find IP address within log lines, using GREP (or any REGEX compatible tool) // [FR] Trouver des adresses IP dans des lignes de journaux, en utilisant Grep (ou un autre outil compatible REGEX) :

### [EN] Search within plaintext log files, in /var/log/ // [FR] Recherche dans les fichiers journaux .log texte dans /var/log/ :
 > grep -ohE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])' /var/log/\*.log\* |sort -n -k 1 |uniq -c |sort -n

### [EN] Search within compressed log files // [FR] Recherche dans les fichiers journaux compressés :
> zgrep -ohE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])' /var/log/\*.log\* |sort -n -k 1 |uniq -c |sort -n

### [EN] Count number of unique IP addresses that were blocked using Fail2Ban // Compter le nombre d'adresses IP uniques qui ont été bloquées par Fail2Ban
> zgrep "Ban " /var/log/fail2ban.log* |  zgrep -ohE '((1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])\.){3}(1?[0-9][0-9]?|2[0-4][0-9]|25[0-5])'   |sort -n -k 1 |uniq -c |wc -l