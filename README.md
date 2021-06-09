# Git prikazy a ich vysvetlenie  


## STATUS ADD COMMIT
set username and email (better github username and email)
```
git config --global user.name 'username'

git config --global user.email 'username@gmail.com'
```

nastav funkcie git-u do tvojho adresara (terminalu)
```
git init
```

checkuj si svoj git status o svojich adresaroch
```commandline
git status
```

zaeviduj si svoj projekt  
ked si zmenil tvoj adresar musis ho pripravit na uplnu zmenu  
musis ho oznacit ze je pripraveny do novej verzie
```commandline
git add <nazov_suboru>
```

po add, musis tie zmenit uskutocnit apply-nut, commit-nut  
po add zmeny su STAGED a su pripravene sa ocitnut v novej verzii  
```commandline
git commit -m 'komentar co som spravil'
# -m --> chces rovno pridat komentar, popisok
```

ADD --> oznacis tym subor v git-e, ktory bol zmeneny, ze je pripraveny na to byt zmeneny  
COMMIT --> oznaceny subor (po add-nuti) je zmeneny  

1. zmenis subor a nasledne ho pripravis k zmene --> git add <nazov_suboru>  
2. apply zmeny, ktore si v nom spravil --> git commit -m 'komentar'  

Informacie o zmenach, kedy boli vykonane a kym
```commandline
git log
```

Oznacit vsetky subory, kotre boli zmenene
```commandline
git add .
# . --> vsetko

git add *.png
# *.png --> vsetky subory konciace na .png
# * --> vsetko konciace na
```

Ked si dal add, add-ol si nejake tie subory, ale rozhodol si sa ze ich nechces commit-nut, zmenit nadalej  
```
git restore --staged <meno_suboru>
# staged --> ked je subor add-nut je staged

git restore --staged .
# . --> vsetky ktore su add-nute --> staged
```

Nemusis davat add ., nemusis davat prvo add vsetko a nasledne commit
Mozes dat kod, ktory add vsetky zmenene subory a hned ich aj commitne s komentarom
```commandline
git commit -am "komentar"
# -a --> funguje len pre upravene subory (ktore existovali, a len boli pozmenene)
```

## DIFF CHECKOUT
