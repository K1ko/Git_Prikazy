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
Ake zmeny sa specificky udiali
```commandline
git diff
# - |--> pre kazdy riadok nejaka zmena tym, ze nieco bolo vymazane
# + |--> pre kazdy riadok nejaka zmena tym, ze nieco bolo pridane
```

Ked nejaky svoj subor ulozis, das save ALE nebol commitnuty  
Mozes sa vratit naspat k povodnemu suboru, k suboru ktoru mas ulozenu v gite (k poslednemu commit-u)
```commandline
git checkout -- <meno_suboru>
```

Ked das git log, kazdy commit ma vlastny unikatny hash (text vedla commit oznaceny oranzovou farbou), napr. commit adwad19802 --> hash = adwad19802  
Mozes si skopirovat kludne cely alebo len prvych niekolko znakov toho hashu  
Potom ked das checkout s tym hashom, tak sa vsetko da do stavu, kedy bol ten commit spraveny, akokeby cestujes spat v case  
Tym si odskocis do starej verzie kodu
```commandline
git checkout <hash>
```

Kebyze sa chces dostat naspat, do casu predtym nez si napisal git checkout <hash>  
Vratis sa do povodnej-najnovsej verzie tvojho projektu  
```commandline
git checkout master
# master/main --> hlavna vetva tvojho projektu
```

## VIM mode
Ked das git commit bez ziadneho komentara, tak to ta da do tzv. VIM modu  
```commandline
git commit
```
Zobrazi sa ti lista, ale nedokazes v nej pisat, musis sa prepnut do pisacieho rezimu  
stlacenie --> i |--> tym tam mozes napisat svoj komentar

Ked das Enter, tak sa vratis spat do modu COMMAND, kde ta to dalo na zaciatku  
Ked nefunguje Enter alebo ESC sprav --> CTRL + C  
Ked chces ulozit tie zmeny a vypnut sa z VIM modu
```commandline
:wq
# w --> ulozenie suboru
# q --> quit VIM mode
# ked nefunguje napis --> :wq!
```

## CLONE PUSH PULL
Z Github-u mozes zklonovat hocijaky hocikoho kod/projekt, kliknes na  zelene tlacitko kod a skopirujes HTTPS  
priklad takeho linku --> https://github.com/yablko/hemingwayovatoro-rotator.git  
Tym si naklonujes projeky a mozes na nom pracovat a menit ho jak chces 
```commandline
git clone <link_skopceny> <daj_hoc_meno_suboru>
git clone https://github.com/yablko/hemingwayovatoro-rotator.git
```

Ked chces vytvorit novy repository, novy projekt na Githube  
Ked si nezacal este ani jeden riadok kodu, a ides uplne od nuly rob pokyny podla --> ...create a new repository on the command line  
Ked uz si napisal nejaky ten kod, ale chces ho dat do github-u, chces ho tam natlacit 'push-nut', rob pokyny podla --> ...push an existing repository from the command line  
Postupne kazdy riadok skopcis a zadas do terminalu  

Kod pod hovori, ze chces vytvorit spojenie zo serverom s takymto HTTPS linkom
```
git remote add origin https://github.com/MAPE-15/skuska_git.git
```

Kod pod hovori, ze natlac 'push' tie zmeny na tvoj Github server  
#### bude to chciet prihlasovacie udaje k githubu, ked to nepojde, maj git na najnovsej verzii !!! --> git update-git-for-windows
```commandline
git push -u origin main
```

Teraz ked mas svoj projekt na Github-e, a budes ho chciet menit  
Nestaci dat commit, ta zmena sa musi odrazit, musi sa ukazat aj na Github-e, musis pridat dalsi prikaz
```commandline
git push origin main
# origin --> dany server na Github-e kde ten projekt sa nachadza
# main --> natlac 'push' tam ten kod tvojej master/main vetvy, tvojej hlavnej vetvy ktoru si pomenil

# alebo git push, lebo ne ziaciatku vytvorenia projektu git push -u origin main -->
# -u |--> po -u ide akokeby default co znamena ze staci napisat git push a automaticky tam prida origin main
```

Ked nastanu zmeny vo vasom projekte ktory je vo vasom Github servery, ale ty konkretne si ich nepspravil, spravil ich niekto iny  
Tie zmeny sa ti nedaju automaticky, musis ten kod pozmeneny pritiahnut 'pull' k sebe
```commandline
git pull origin main
```

Vzdy ked spravis nejake tie zmeny a chces aby sa ukazali aj na Github-e tak vzdy musis ten projekt vtlacit 'push-nut' tam
```commandline
git push origin main
```

git push --> natlacis 'push' zmeny ktore si spravil na tvoj server aby tam tiez boli vidno  
git pull --> vytiahned/pritiahnes 'pull' zmeny zo servera, ktore spravil niekto iny

## REMOTE-UPDATE WHATCHANGED  
Skontrolovat ci vlastne niekto tie zmeny spravil vo vasom projekte na Github-e
```commandline
git remote update
# nasledne hned po tom
git status

# vypise ti to, ze ci si o niekolko commitov pozadu alebo nie
# ak si pozadu potrebujes pritiahnut tie zmeny k sebe --> git pull origin main 
```

Ak chces zistit tiez ci sa nezmenilo daco na servery, ale dostat k tomu viac info, napr. o case, kym to bolo zmenene atd...
```commandline
git whatchanged origin/main -n 1
```

**Vzdy ked su zmeny spravene a praujes so starym kodom (nedal si pull) tak vzdy daj git pull origin main, potom mozes ten kod menit a davat git push origin main**  

## VETVY MERGE  

Tvoj hlavny kod (projekt), tvoja hlavna vetva sa vola main, kde je tvoj najhlavnejsi kod  
Tymto dostanes mena vsetkych vetiev, ktore sa nachadzaju v tvojom git projekte
```commandline
git branch
# main --> je tvoja hlavna
# * --> znamena, ze prave v tej danej vetve sa nachadzas
```

Vytvorit novu vetvu, sekundarnu
```commandline
git branch <meno_novej_vetvy>
```

Prepnut sa do danej vetvy a robit v nej zmeny
```commandline
git checkout <meno_existujucej_vetvy>
```

Ked menis tvoju sekundarnu vetvu, tak tvoja hlavna main vetva zostane neposkvrnena, nepozmenena  
Tak mozes prepinat medzi vetvami git checkout <meno_vetvy> bez toho, aby si zanechal zmeny v druhych vetvach  

Rychlejsi zapis, ktory rovno vytcori tvoju novy vetvu a rovno sa k nej aj pripoji
```commandline
git checkout -b <meno_vetvy>

# kod nad je vlastne kod 1. a 2. dokopy
# 1. git branch <meno_vetvy>
# 2. git checkout <meno_vetvy>
```

Ked chces spojit tvoje zmeny v sekundarnej vetve s tvojom hlavnou main vetvou  
Tak ich potrebujes zlucit 'merge'  
Prvo sa prepni na hlavnu vetvu git checkout main  
A potom zluc tu hlavnu vetvu s tou sekundarnou
```commandline
git merge <meno_sekundarnej_vetva>
```

Existuje merge a rebase  
Merge --> nie je destruktivny, mas stale tvoju main vetvu aj tvoje sekundarne vetvy untouched, nijako sa sekundarna nevymaze, ked je merge-nuta s main vetvou    
Rebase --> je destruktivny, hlavnu main vetvu nalepi na sekundarnu vetvu s tym, ze bude v main vetva v tej sekundarnej uz existovat a ta sekundarna sa akokeby vytrati, vymaze  


## DISABLE GIT INIT IN YOUR DIRECTORY  
To disable git init in your directory and all .git things
```commandline
rmdir /s .git
```

## MIT MARKDOWN .GITIGNORE
**Pri vyrabani repository na Github-e, license je najlepsie si vybrat MIT License**  


**.GITIGNORE** je nato, ze niektore adresare a subory su ti uplne zbytocne, tak ich git bude ignorovat  
Je to sposob gitu povedat, ktore subory a adresare ma ignorovat (napr. .env subory vobec nepotrebujes)  


**MARKDOWN**, README.md --> .md --> markdown  
Do README.md napises pre uzivatela tvojho projektu alebo pre seba, co sa v danom projekte nachadza, jak ho pouzivat atd., ma informacny ucel  

Format Markdown-u
```commandline
'#' --> nadpis; '##' --> mensi nadpis; '###' este mensi nadpis atd... 
**slovo** --> text 'slovo' bude tucnym pismenom lebo **

[hypertextove prepojenie] --> tak sa znaci hypertextove prepojenie [text]

Ked chces ist na dalsi riadok/line na konci vety daj 2x Space a potom Enter na dalsi riadok
Alebo daj 2x Enter

Oznacit nejaku cast kodu vdaka ' ``` ' (triple `) -->
' ``` ' 
kod 1
kod 2
' ``` '
```
  
