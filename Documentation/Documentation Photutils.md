# Documentation Photutils

**Photutils est un package affilié à Astropy qui fournit principalement des outils pour détecter et effectuer la photométrie de sources astronomiques.**

```python
pip install photutils
from photutils.detection import DAOStarFinder
```

## **`DAOStarFinder`**

→ Lire l’image ←

```python
from astropy.io import fits
image_data = fits.getdata('votre_image.fits')
```

→ Créer une instance DAOStarFinder ←

```python
daofind = DAOStarFinder(fwhm=3.0, threshold=5.*std)
```

- **`fwhm`** : La largeur totale à mi-hauteur des sources dans l'image.
- **`threshold`** : Le seuil de détection en unités d'écart type du bruit de fond

→ **Exécuter la détection sur l'image ←**

```python
sources = daofind(image_data)
```