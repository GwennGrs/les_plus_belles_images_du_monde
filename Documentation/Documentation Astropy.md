# Documentation Astropy

Astropy est une bibliothèque Python destinée à faciliter les opérations liées à l'astronomie. Elle propose de nombreux modules pour traiter des tâches courantes dans le domaine de l'astronomie, telles que la manipulation des unités, la gestion des coordonnées célestes, la lecture/écriture de fichiers FITS (Flexible Image Transport System) et bien plus encore.

# Installation :

```bash
pip install astropy
```

Dans notre cas à faire dans le terminal VScode pour pouvoir l’utiliser.

## Manipulation des unités :

```bash
from astropy import units as u

# Créer une quantité avec une unité
distance = 42 * u.lightyear

# Convertir la distance en kilomètres
distance_km = distance.to(u.kilometer)

print(distance_km)
```

## Lecture/Ecriture de fichiers FITS :

```bash
from astropy.io import fits

# Lire un fichier FITS
hdul = fits.open('exemple.fits')
data = hdul[0].data

# Afficher les données du fichier FITS
print(data)

# Écrire dans un nouveau fichier FITS
new_hdul = fits.HDUList([fits.PrimaryHDU(data)])
new_hdul.writeto('nouvel_exemple.fits', overwrite=True)
```

La base pour pouvoir commencer à travaille sur des données du JSWT.

## Astropy X Matplotlib :

```bash
import matplotlib.pyplot as plt
from astropy.io import fits

# Lire une image FITS
hdul = fits.open('image.fits')
image_data = hdul[0].data

# Afficher l'image
plt.imshow(image_data, cmap='gray')
plt.colorbar()
plt.show()
```

La plupart des fonctionnalités que l’on a fait avec astropy nécessite matplotlib pour pouvoit représenter des données de manière graphique.