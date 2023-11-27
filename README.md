// 1. Sélectionnez le premier fils de l'élément body et modifiez son contenu
document.body.firstElementChild.textContent = "Rick Astley - Never Gonna Give You Up";

// 2. Sélectionnez tous les éléments possédant la classe "couplet" et supprimez la première ligne en double
var couplets = document.querySelectorAll('.couplet');
couplets.forEach(function(couplet) {
    var lines = couplet.innerHTML.split('<br />');
    lines = lines.filter(function(line, index, self) {
        return index === self.indexOf(line);
    });
    couplet.innerHTML = lines.join(' ');
});

// 3. Le refrain s'est dupliqué à cause de l'écho. Supprimez les occurrences en double
var refrain = document.querySelector('.refrain');
var refrainLines = refrain.innerHTML.split('<br />');
refrainLines = refrainLines.filter(function(line, index, self) {
    return index === self.indexOf(line);
});
refrain.innerHTML = refrainLines.join(' ');

// 4. Supprimer l'élément ayant pour id "erreur"
var erreurElement = document.getElementById('erreur');
if (erreurElement) {
    erreurElement.remove();
}

// 5. Ajoutez un <footer> en bas de la page
var footer = document.createElement('footer');
footer.textContent = '© Copyright 2020 - Nom';
document.body.appendChild(footer);
