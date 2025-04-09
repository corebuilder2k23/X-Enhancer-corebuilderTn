# X-Enhancer-corebuilderTn
/ ==UserScript==
// @name         Amélioration visionnage X - Mes publications
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  Met en surbrillance mes publications sur X pour un meilleur suivi
// @author       corebuilderTn
// @match        https://x.com/*
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    // Votre pseudo X
    const myUsername = "corebuilderTn";

    // Fonction pour mettre en surbrillance vos publications
    function highlightMyPosts() {
        const tweets = document.querySelectorAll('article');
        tweets.forEach(tweet => {
            const username = tweet.querySelector('a[href*="/' + myUsername + '"]');
            if (username) {
                tweet.style.backgroundColor = '#e6f3ff'; // Fond bleu clair
                tweet.style.border = '2px solid #1da1f2'; // Bordure bleue
            }
        });
    }

    // Exécute la fonction au chargement initial
    highlightMyPosts();

    // Surveille les nouveaux tweets chargés dynamiquement
    const observer = new MutationObserver(highlightMyPosts);
    observer.observe(document.body, { childList: true, subtree: true });
})();
