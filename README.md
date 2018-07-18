# Snippets, it's fast it's fun.

Taupom laiką ir pratinamės naudoti snippetus. Labai naudinga ypač sudetingesniems kodo gabalams kuriuos labai dažnai naudojate, vis kopinate iš kur nors ar kuriuose yra daug simbolių. Nepaisant kaip greitai rašote (@G) vistiek parašyti tris raides ir paspaudus 'tab' gausis greičiau.

Pvz parašai 'txt' spaudi 'tab' ir gauni 'echo $gTxt->get('key', 'text');'
'ne' -> 'if (!empty()){ ...'
'db' -> '$db = & load_class('DB');'
ir t.t.

Svarbu tai kad net nebūtina parašyti visos frazės ar galima su klaida dėl fuzzy search.
Pvz parašę 'lomo' ir pasaudę 'tab' vistiek gausite '$gModule = & load_class('Module');' nors ir trigeris yra 'load_class-module'

## Kaip susisetupinti code snippets, kad vis gaučiau atnaujinimus iš GIT?

 1. Uždarote visus Sublime langus.
 2. Atsidarote AppData folderį. windows+r rašote '%appdata% > enter
 3. Einate 'Sublime Text 3/Packages'.
 4. Pakeičiate folderio 'User' pavadinimą į 'bc_User' (čia bus jūsų nustatymų backup'as)
 5. Nusikopinate kelią iki folderio 'bc_User'. Right click ant 'bc_User' > Properties > right click ant teksto šalia 'Location' > Copy. Reikšmė turėtų būti panaši į C:\Users\Linas\AppData\Roaming\Sublime Text 3\Packages (žioma gali būti ir Sublime Text 2)
 6. Atsidarote https://github.com/sonarolt/Snippets, spaudžiate 'Clone or download' > 'Open in desktop'.
 7. Iššoka GitHub Desktop appse langas. Jame į 'Local path' paste'inate nukopijuotą kelią iki '_User' foderio. Turėtų iššokti klaida, kad toks folderis jau naudojame. Prie įpastintos reikšėms prirrašote '\User'. Turi gautias kažkas C:\Users\Linas\AppData\Roaming\Sublime Text 3\Packages\User. Klaida turi išnykti. 
 8. Spaudžiate 'Clone' ir kantriai laukiate.
 9. Atsidarote direktoriją C:\Users\Linas\AppData\Roaming\Sublime Text 3\Packages iš iš backupfolderio 'bc_User' nukopinate failus į naujai sukurtą 'User' folderį. Jei seniau neturėjote jokių snippetų - konfilktų neturi būti. Jei yra - pasitikrinate ką perrašo ir nuspredžiate patys ką daryti. 
10. Atsidarote Sublime ir rašote 'txt' ir spaudžiate tab. Jei atsirado tekstas 'echo $gTxt->get('key', 'text');' - you are one lucky dev.
 
## Kaip susisetupinti code snippets, dzin man tie atnaujinimai.

Nedaryk taip, nėra prasmės.

## Du skirtingi tipai

### Snipet failai. 
Extension .sublime-snippet. Gyvena User/snipets folderyje (labai keista bet tikriausiai dev padarę klaidą nes turi būti double p?). Viename faile vienas snippetas. WKM snippetai padaryti per ten.

### Completion failai. 
Extension .sublime-completions. Gyvena tiesiai User folderyje. Juose gali būti sudėta daug skirtinų snipetų. Bendri core snipetai sudėti į core.sublime-completions.

Matysime ateityje kuris būdas patogesnis ir gal pasiliksime prie vieno.

## Kaip žinoti kokius sippetus galiu naudoti?

### Completion failai
Atsidarote failą core.sublime-completions ir jame matote JSON su code snipeetais. trigger - ką reikia parašyti, kad paspaudus 'tab' atsirastų reikšmė iš contents. Jei contents turi kintamuosius kaip ${1:className} tai reiškia, kad čia atsistos kursorius kai dar kartą paspausite 'tab'. Skaičius pradžioje nurodo seką kuri kursorius toliau šokinės spaudant tab (pvz ${2:className} bus antra pozicija).

Jei rašote savo snippetus ir norite panaudoti simbolį $ tai prie jį reikia escapinti dedant \\ (JSON bajeriukas).

Galite kurti kiek norite completion failų, pvz vieną padaryti css reikmėms, kitą wkm ir t.t.

### Snippet failai
Folderyje guli atskiri failai. Jų struktūra sudėta į XML tagus. <tabTrigger> - ką reikia parašyti, kad paspaudus tekstą gautumėte reikšmę iš <content>

Naują snippet labai patogu kurti tiesiai iš sublime, Tools > Developer > New snippet (ant sublime 2 Tools > New snippet).

Šitame formate nereikia escapinti $.


