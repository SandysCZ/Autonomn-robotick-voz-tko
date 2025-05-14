# Autonomni roboticke vozitko

Představení pásového robota s více režimy řízení

Tento projekt univerzálního pásového robota vybaveného čtyřmi stejnosměrnými motory typu TT, rozmístěnými po dvou na každé straně podvozku. Motory jsou synchronizované tak, aby se otáčely ve shodě a zajišťovaly správný a plynulý pohyb robota. Konstrukce podvozku je uzpůsobena pro jízdu v různém terénu, přičemž pásy zajišťují dobrou stabilitu i na nerovném povrchu.

Robot je osazen ultrazvukovým senzorem umístěným v přední části pro detekci překážek, a dále šesti bílými LED diodami, po třech na každé straně předku robota, sloužícími pro osvětlení při práci ve zhoršených světelných podmínkách.

Uvnitř konstrukce se nacházejí čtyři samostatné plošné spoje (PCB). Každý z nich plní specifickou funkci a některé jsou vybaveny vlastním mikrokontrolérem. Následuje podrobný popis jednotlivých desek:

⸻

1. PCB – Ovládání světel na základě intenzity světla

První deska je osazena fotorezistorem, který snímá okolní světelné podmínky. Pokud senzor detekuje nízkou intenzitu světla (například vjezd do temného prostoru), dojde automaticky k rozsvícení LED diod na přední části robota. Tato část je hardwarově jednoduchá a nevyužívá mikrokontrolér.

⸻

2. PCB – Sledování čáry

Druhá deska zajišťuje funkci line followeru, tedy schopnost robota sledovat čáru na zemi. Obsahuje dvě infračervené LED diody a dvě fotodiody. Princip je založen na odrazu infračerveného záření od povrchu – světlý povrch odráží paprsek zpět do fotodiody, tmavý (např. černá čára) nikoliv. Pokud senzor zaznamená černý povrch, vyšle logickou 0 na vstup motorového driveru L293D, čímž dojde ke korekci směru jízdy. Deska rovněž neobsahuje mikrokontrolér.

⸻

3. PCB – Bluetooth ovládání

Třetí deska umožňuje manuální ovládání robota přes mobilní telefon. Je vybavena mikrokontrolérem Wemos D1 Mini, který komunikuje přes Bluetooth modul. Signály z mobilní aplikace (např. směr jízdy, otáčení) jsou přenášeny přes motorový driver L293D k pohonným motorům. Kromě pohybu bude možné prostřednictvím této desky rozsvěcet LED světla a ovládat ventilátor, který je umístěn na robotovi pro specifické účely (viz dále).

⸻

4. PCB – Detekce plamene a vyhýbání překážkám

Čtvrtý plošný spoj je nejkomplexnější a je osazen mikrokontrolérem Atmega328P, který zajišťuje pokročilou autonomní funkci robota. Tato deska je napojena na infračervené senzory plamene, pomocí kterých robot dokáže vyhledávat zdroj ohně. Po jeho nalezení se natočí směrem k plameni a následně aktivuje ventilátor, který se pokusí plamen uhasit.

Současně je tento mikrokontrolér propojen s ultrazvukovým senzorem, který umožňuje vyhýbání se překážkám. Robot tedy dokáže autonomně detekovat objekty v cestě a upravit svůj směr, aby nedošlo ke kolizi.

⸻

Závěr

Tento pásový robot kombinuje manuální i autonomní režimy řízení, včetně sledování čáry, detekce překážek, rozpoznání plamene, a osvětlení na základě okolních podmínek. Díky modulární konstrukci s více PCB deskami a různým řídicím systémům představuje komplexní projekt vhodný pro demonstrační i soutěžní účely v oblasti robotiky a automatizace.
