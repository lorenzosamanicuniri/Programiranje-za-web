**3D Printanje**

Naša grupa se sastoji od 3 člana i to su: Lorenzo Šamanić, Bruno Grbac i Luka Raičević.
Tema koju smo zajednički izabrali je tema 3D Printanje.
U aplikaciji će se moći pregledavati dostupne 3D printere, njihove specifikacije i mogućnosti, te ponuda plastika i njihove specifikacije i namjene. Glavni cilj je omogućiti lagano pretraživanje printera i plastika kako bi klijent mogao pronaći najjeftinije opcije na internetu. 
U aplikaciji ćemo imati 3 modela. Proizvodjac, Plastika,  Printer. 

Sadržaj datoteke models.py:

```
from django.db import models

class Proizvodjac(models.Model):
    name = models.CharField(max_length=100)
    country = models.CharField(max_length=50)
    email = models.EmailField()
    website = models.URLField()

    def __str__(self):
        return self.name

class Plastika(models.Model):
    plastika_proizvodjac = models.ForeignKey(Proizvodjac, default=1, on_delete=models.CASCADE)
    name = models.CharField(max_length=100)
    type = models.CharField(max_length=20)
    temperature = models.CharField(max_length=20)

    def __str__(self):
        return self.name    

class Printer(models.Model):
    printer_proizvodjac = models.ForeignKey(Proizvodjac, default=1, on_delete=models.CASCADE)
    model = models.CharField(max_length=100)
    type = models.CharField(max_length=20)
    price = models.CharField(max_length=20)
    printer_plastika = models.ManyToManyField(Plastika)
    website = models.URLField()

    def __str__(self):
        return self.model
```
