<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ma Boutique</title>
    <script src="https://telegram.org"></script>
    <style>
        body { font-family: Arial, sans-serif; background: #f4f4f9; padding: 15px; text-align: center; color: #333; }
        .onglets { display: flex; justify-content: space-around; margin-bottom: 20px; }
        .onglet-btn { background: #ddd; border: none; padding: 10px; border-radius: 5px; width: 45%; font-weight: bold; }
        .onglet-btn.active { background: #0088cc; color: white; }
        .page { display: none; }
        .page.active { display: block; }
        .produit { background: white; padding: 15px; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.05); margin-bottom: 20px; text-align: left; }
        .prix { color: #2ecc71; font-weight: bold; font-size: 18px; margin: 5px 0; }
        .video-container { position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; background: #000; border-radius: 8px; margin-bottom: 10px; }
        .video-container iframe { position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none; }
        .btn-commander { background: #0088cc; color: white; border: none; padding: 12px; border-radius: 8px; font-size: 15px; width: 100%; font-weight: bold; width: 100%; }
        .btn-contact { background: #2ab200; color: white; text-decoration: none; display: block; padding: 12px; border-radius: 8px; margin-top: 10px; font-weight: bold; text-align: center; }
    </style>
</head>
<body>

    <!-- Menu de navigation -->
    <div class="onglets">
        <button class="onglet-btn active" onclick="changerPage('boutique')">🛍️ Articles</button>
        <button class="onglet-btn" onclick="changerPage('contact')">📞 Contacts</button>
    </div>

    <!-- PAGE BOUTIQUE -->
    <div id="page-boutique" class="page active">
        
        <!-- ARTICLE 1 AVEC VIDÉO -->
        <div class="produit">
            <div class="video-container">
                <!-- Vidéo d'exemple YouTube -->
                <iframe src="https://vm.tiktok.com/ZN8M1T23C/" allowfullscreen></iframe>
            </div>
            <h3>Premier Article (Avec Vidéo)</h3>
            <div class="prix">1G 50€</div>
            <p>Remise uniquement en main propre.</p>
            <button class="btn-commander" onclick="commander('Article 1', '50€')">🛒 Commander (Main propre)</button>
        </div>

        <!-- ARTICLE 2 AVEC VIDÉO -->
        <div class="produit">
           <iframe src="https://vm.tiktok.com/ZN8M1T23C/" allowfullscreen></iframe>
            </div>
            <h3>Deuxième Article</h3>
            <div class="prix">20,00 €</div>
            <p>Disponible immédiatement.</p>
            <button class="btn-commander" onclick="commander('Article 2', '20 €')">🛒 Commander (Main propre)</button>
        </div>

    </div>

    <!-- PAGE CONTACT -->
    <div id="page-contact" class="page">
        <div class="produit" style="text-align: center;">
            <h3>Une question ?</h3>
            <p>Cliquez ci-dessous pour m'écrire directement :</p>
            <a href="https://t.me" class="btn-contact">💬 M'écrire sur Telegram</a>
            <p style="margin-top: 20px; font-size: 14px; color: #666;">📍 Paiement en espèces lors de la remise en main propre.</p>
        </div>
    </div>

    <script>
        const tg = window.Telegram.WebApp;
        tg.expand();

        function changerPage(pageId) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            document.querySelectorAll('.onglet-btn').forEach(b => b.classList.remove('active'));
            document.getElementById('page-' + pageId).classList.add('active');
            event.currentTarget.classList.add('active');
        }

        function commander(nomArticle, prixArticle) {
            const commande = { article: nomArticle, prix: prixArticle };
            tg.sendData(JSON.stringify(commande));
        }
    </script>
</body>
</html>
