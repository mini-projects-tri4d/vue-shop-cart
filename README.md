# vue-shop-cart

### Mini projekt neve: 
#### vue-shop-cart

### Mini projekt célja: 
Vue-ban reszponzív bevásárlókosár funkció megvalósítása. A termékeket hozzá lehet adni a kosárhoz, növelni, csökkenteni lehet a kosárban lévő mennyiségeket, a termékek megadott áraival a program kiszámolja a kosár végösszegét.

### Technológiák:
HTML, CSS, Vue.js, Bootstrap

### Használat:
Futtatáshoz nyiss egy terminál ablakot, lépj bele a mini projekt mappájába, majd add ki az alábbi parancsot:

```bash
npm run dev
```

A terminál ablakban meg fog jelenni egy URL, amelyre kattintva (CTRL + klikk) vagy az URL-t egy böngésző címsorába másolva elindíthatod a programot. 

A program indulása után, a termékek megjelennek az oldal törzsében, mindegyik termék egy-egy kártyán. A termékkártyákon található egy-egy gomb, "Kosárba" felirattal, ha erre kattintunk, akkor a termék hozzáadódik a "Kosár"-hoz, ami megjelenik az oldal jobb oldalán. A "Kosár" megjeleníti a hozzáadott termékeket, a hozzáadott darabszámokat, valamint az egyes termékek áraival számolt összegeket. A "Kosár"-ban lévő termékek darabszámai a plusz és minusz gombokkal növelhetőek, illetve csökkenthetőek, aminek hatására az összegek újraszámolódnak. A fejlécben lévő "Kosár" feliratnál megjelenik a hozzáadott termékek darabszáma. A "Kosár" elrejthető/megjeleníthető a fejlécben lévő feliratra kattintva.

### Termékek hozzáadása:

A termékek listáját a '/src/data/' mappában található 'products.js' fájl tartalmazza, a kártyákon megjelenő képek a '/src/assets/images' mappában találhatóak. Mindkettő bővíthető további elemekkel.

