# Tudnivalók

## VirtualBox importálás
### Korábbi virtuális gép törlése
Óvatosan, nehogy más virtuális gépét töröljétek ki!

1. A workstation-n VirtualBox-ban a CentOS7-et kiválasztva Delete/Törlés, Delete All files választása
2. Ellenőrizd a VirtualBox->File->Virtual Media Manager pontban, hogy nem létezik a CentOS7-es disk, ha ott van, akkor töröld.

### Virtuális gép importálása
1. Hozd létre a D:\Work\VirtualBox könyvtárat (ha ott van már és nincs másnak a virtuális gépe benne, akkor törölj belőle mindent)
2. VirtualBox-ban:

- File->Preferences->General->Default Machince folder beállítása: D:\Work\VirtualBox
- Import Appliance: D:\VPCImages\PAAS\student2018.ova 
- Ellenőrizd a wizard utolsó lépésénél, hogy jó útvonal került-e be

## VirtualBox CentOS információk
- VirtualBox-ban indítsd el a CentOS image-et és ebben dolgozz!
- itt aláljátok meg az image-et, amit importáljatok VirtualBox-ba:D:\VPCImages\PAAS
- CentOS Login: **BME Paas user / jelszó: paaslabor**
- sudo használható (óvatosan azért :))
- ha szükséged van esetleg a Linuxon valami package-re: sudo yum install -y XXXXXXXX
- host gép könyvtárának mountolása: 
1. hozz létre a VirtualBox-ban Devices/Shared Folders -ben egy foldert (géphez tartozó megosztások alá) pl. host néven, 
2. majd a CentOS-ben ezt mountolhatod: sudo mount -t vboxsf host /media  (host a share neve)
- Firefox a böngésző
- érdemes beállítani VirtualBox-ban a bidirectional clipboard-ot hogy a copy-paste működjön
- service-ek statusa, újraindítása pl.: sudo systemctl restart NetworkManager
- készítsetek magatoknak egy munkakönyvtárat és abban dolgozzatok

## GitHub

Mindenkinek készítenie kell egy GitHub-os account-ot, vagy a meglévőt használjátok!

1. https://github.com/
2. Sign Up
3. username pl. alerantbmexy, stb...., meg kell erősíteni a regisztrációt emailben kapott linken
4. GitHub-on start project, pl. gyakorlat2

A CentOS image-ben a ~/git könyvtárban tudtok dolgozni (több projekt is lesz)

Git fontos parancsok:
```shell
echo "# gyakorlat2" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/alerantbmexy/gyakorlat2.git
git push -u origin master
```

Gyakorlatokban így klónozz le példákat:
```shell
# példa Java OpenShift Wildfly alkalmazás klónozása
git clone https://github.com/bparees/openshift-jee-sample gyakorlat2
git pull https://github.com/bparees/openshift-jee-sample gyakorlat2

# ne az eredeti helyre tegyük vissza
git remote set-url origin https://github.com/alerantbmenz/gyakorlat2.git

# módosítások
git commit -a -m 'Some commit message'
# feltöltjük az új helyre a saját accountunk alá
git push origin master
```
Ekkor a saját GitHub URL alapján már lehet saját kódbázison új proktet létrehozni.

Ilyen a könyvtárstruktúra:
```shell
[bmepaasuser@localhost ~]$ tree git/
git/
└── gyakorlat2
    ├── pom.xml
    ├── README.md
    └── src
        └── main
            ├── java
            ├── resources
            └── webapp
                ├── images
                │   └── jbosscorp_logo.png
                ├── index.html
                └── snoop.jsp

```


## DNS és hosts fájl
- Az openshift-es alkalmazások core komponensek alapvetően IP-vel érhetőek el, de az /etc/hosts fájlban fel vannak véve a FQDN-ek
- A gépeken dnsmasqd is telepítve van, amely segítségével működik a wildcard DNS is, tehát pl. az XXX.apps.openshift.local is feloldódik a megfelelő IP-re

dnsmasq config fájl: /etc/NetworkManager/dnsmasq.d

## IP-k
```shell
192.168.30.11	bmepaas-master.openshift.local
192.168.30.12	bmepaas-node1.openshift.local
192.168.30.13	bmepaas-node2.openshift.local
```


## Elérések

## Docker témához
- Vannak már Docker image-ek a lokális gépen, azt próbáljátok használni elsősorban és ne újakat töltsetek le!

## OpenShift témához
- OpenShift dashboard: https://bmepaas-master.openshift.local:8443
- Lokális OpenShift elindítása: oc cluster up (kiírja az indítás után, hogyan érhető el)

## Jegyzőkönyv

**A jegyzőkönyvhöz menet közben gyűjtsd az anyagokat (külön jelölve van, hogy mikor mit), hogy a kitöltésnél már minden infó meglegyen.**

# Otthon hogyan próbálhatom ki?
Linuxon egyszerűbb, de nem kizárólagos platform!
## Virtuális gép
A gyakorlaton használt virtuális gépet is elvihetitek!
## Docker
- Telepítsd fel és játsz vele (Linuxokra a csomagkezelőn keresztül vagy [innen](https://store.docker.com/search?offering=community&type=edition) mindenféle platformra) 
- Vagy játsz vele [online](http://training.play-with-docker.com/)!
## Kubernetes
- Natív Kubernetes telepítés Linuxon
- [Minikube](https://github.com/kubernetes/minikube)
## Openshift
- oc cluster up [itt](https://github.com/openshift/origin/blob/master/docs/cluster_up_down.md)
- [Minishift](https://github.com/minishift/minishift)
