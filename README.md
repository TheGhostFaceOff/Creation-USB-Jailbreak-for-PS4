diff --git a/README.md b/README.md
index 349bdb027f52217dce3e5f8659789bd5bfede154..88d384bb0642bfbf096ff6b18bc8f72b1338bf8e 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,60 @@
 # Creation Installation USB Jailbreak for PS4
+
+## Script inclus
+
+Ce dépôt contient le script Python `usb_exfat_downloader.py` compatible **Linux et Windows**.
+
+Il permet de :
+
+1. Détecter les clés USB branchées.
+2. Te laisser choisir la clé USB à utiliser.
+3. Formater la clé USB sélectionnée en **exFAT uniquement**.
+4. Télécharger des fichiers depuis des URLs que tu fournis.
+5. Copier directement les fichiers téléchargés sur la clé USB.
+
+## Prérequis
+
+- Python 3
+
+### Linux
+
+- `lsblk`
+- `mkfs.exfat` (souvent fourni par `exfatprogs`)
+- `sudo` avec droits de formatage/montage
+
+### Windows
+
+- Lancer le terminal **en administrateur**
+- PowerShell disponible (`Format-Volume`)
+- Clé USB amovible avec lettre de lecteur assignée (ex: `E:`)
+
+## Utilisation
+
+### Option 1 : URLs en ligne de commande
+
+```bash
+python3 usb_exfat_downloader.py \
+  --url "https://release-assets.githubusercontent.com/github-production-release-asset/1119867494/ece38ac4-10a7-45f1-9ad4-b68cec3d82ab?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-02-25T10%3A48%3A48Z&rscd=attachment%3B+filename%3DVueSystemBackup.7z&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-9515b896b4de&skt=2026-02-25T09%3A48%3A13Z&ske=2026-02-25T10%3A48%3A48Z&sks=b&skv=2018-11-09&sig=uIHsLCWP2MJpdZRVg%2BkGGgUTwJ3k64XLAlfob7nIDc0%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc3MjAxNjc0OSwibmJmIjoxNzcyMDEzMTQ5LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.Vx7tFtmVj4scyMWgF4wLb4ILjXi6FoyQSIBSr-iMpSI&response-content-disposition=attachment%3B%20filename%3DVueSystemBackup.7z&response-content-type=application%2Foctet-stream" \
+  --url "https://storage.ko-fi.com/shopitemassets/b1b8698b-7ee7-4f9a-9e3a-e5b0e3c6a3c4_goldhen_v2.4b18.9.7z?sv=2020-04-08&ss=b&srt=o&se=2026-02-16T15%3A52%3A30Z&sp=r&sig=k1qZ2lsMze%2Bt62ObNspgLFTEvw%2BOSPbOA9IAiDSZpS4%3D"
+```
+
+### Option 2 : URLs dans un fichier
+
+Créer un fichier `urls.txt` :
+
+```txt
+https://release-assets.githubusercontent.com/github-production-release-asset/1119867494/ece38ac4-10a7-45f1-9ad4-b68cec3d82ab?sp=r&sv=2018-11-09&sr=b&spr=https&se=2026-02-25T10%3A48%3A48Z&rscd=attachment%3B+filename%3DVueSystemBackup.7z&rsct=application%2Foctet-stream&skoid=96c2d410-5711-43a1-aedd-ab1947aa7ab0&sktid=398a6654-997b-47e9-b12b-9515b896b4de&skt=2026-02-25T09%3A48%3A13Z&ske=2026-02-25T10%3A48%3A48Z&sks=b&skv=2018-11-09&sig=uIHsLCWP2MJpdZRVg%2BkGGgUTwJ3k64XLAlfob7nIDc0%3D&jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmVsZWFzZS1hc3NldHMuZ2l0aHVidXNlcmNvbnRlbnQuY29tIiwia2V5Ijoia2V5MSIsImV4cCI6MTc3MjAxNjc0OSwibmJmIjoxNzcyMDEzMTQ5LCJwYXRoIjoicmVsZWFzZWFzc2V0cHJvZHVjdGlvbi5ibG9iLmNvcmUud2luZG93cy5uZXQifQ.Vx7tFtmVj4scyMWgF4wLb4ILjXi6FoyQSIBSr-iMpSI&response-content-disposition=attachment%3B%20filename%3DVueSystemBackup.7z&response-content-type=application%2Foctet-stream
+https://storage.ko-fi.com/shopitemassets/b1b8698b-7ee7-4f9a-9e3a-e5b0e3c6a3c4_goldhen_v2.4b18.9.7z?sv=2020-04-08&ss=b&srt=o&se=2026-02-16T15%3A52%3A30Z&sp=r&sig=k1qZ2lsMze%2Bt62ObNspgLFTEvw%2BOSPbOA9IAiDSZpS4%3D
+```
+
+Puis lancer :
+
+```bash
+python3 usb_exfat_downloader.py --urls-file urls.txt
+```
+
+## Important
+
+- Le script demande une confirmation explicite (`OUI`) avant de formater.
+- **Tout le contenu de la clé USB sélectionnée est supprimé.**
+- Vérifie bien le disque sélectionné avant de confirmer.
