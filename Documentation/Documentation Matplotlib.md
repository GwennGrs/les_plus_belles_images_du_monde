# Documentation Matplotlib

## Astropy

fits : import de astropy.io

[fits.open](http://fits.open) permet d’ouvrir un fichier

cela nous donne une liste de données qui sont soit des images, des tables de données… Certaines sont donc inutilisable comme nous avons pu faire le test juste avant.

### Pour les fichiers images

Nous pouvons les récupérer avec

```python
fits_file = fits.open('fichier.fits')

image_data = fits_file[0].data
```

On prend le premier élément car fits open rend une liste.

Ca nous donne alors une liste de liste donnant tout les pixel de l’image fits. Avec leur niveau de luminosité en float

## Matplotlib

```python
import matplotlib.pyplot as plt
from matplotlib.colors import LogNorm

plt.figure()
plt.imshow(image_data, origin = "lower",norm=LogNorm(),cmap='Greys')
plt.colorbar()
plt.show()
```

On prend matplotlib pour afficher l’image.

“imshow” permet d’afficher des images et de rajouter des option pour mieux voir certaines caractéristiques de ces images. Il prend seulement des images sous formes de matrices carré.

On utilise une color map ou cmap, la ‘Greys’ pour afficher en différentes nuances de gris. Il en existe de nombreux autres, “Greys” est utile pour pouvoir bien distinguer les objets lumineux.

Chaque valeur dans la matrice est mappée (mis à sa place) à une nuance de gris en fonction de son intensité.

L’échelle de couleur ou norm est le traitement des couleurs de l’image pour mieux comprendre celles-ci, elle permette souvent de pouvoir gérer l’intensité des couleurs pour rendre des choses plus visibles. La fonction LogNorm() est souvent utilisé sur des images possèdant une grande plage de couleurs, ce qui sera plus lumineux par exemple sera plus simple a voir. 

Les différentes valeurs montre la luminosité des pixels, ont change alors simplement la façon dont on les vois et la couleurs qu’ils ont de base. 

### Sections

On peut alors maintenant créer des sections pour faire la meme chose mais en prenant une zone particulière.

```python
section1 = [1000:2000,1000:2000]

plt.figure()
plt.imshow(section1, origin = "lower",norm=LogNorm(),cmap='Greys')
plt.colorbar()
plt.show()
```

Les fichiers ont une taille plutôt conséquente, nous avons besoin de les segmentés pour bien les analyser. On peut alors faire des sections.

### Superposition d’image

Pour l’astronomie, superposé plusieurs images permet de pouvoir voir des éléments que l’on aurait pas vu avec une image simple.
C’est une des utilités de Matplotlib où on peut simplement afficher 2 images qui se superposeront toutes seul.

```python
import matplotlib.pyplot as plt
from astropy.io import fits
from matplotlib.colors import LogNorm

# Charger les fichiers FITS
hdulist1 = fits.open('image1.fits')
hdulist2 = fits.open('image2.fits')

data1 = hdulist1[0].data
data2 = hdulist2[0].data

# Créer une figure
plt.figure()

# Afficher la première image avec colormap 'viridis'
plt.imshow(data1, origin='lower', norm=LogNorm(), cmap='viridis', alpha=0.7)

# Afficher la deuxième image avec colormap 'plasma'
plt.imshow(data2, origin='lower', norm=LogNorm(), cmap='plasma', alpha=0.7)

# Ajouter une barre de couleur pour référence
plt.colorbar(label='Intensity')

# Afficher la figure
plt.show()
```