# External Messages Traffic Light Rules (ExMsgTLR) (Exchange Mail Flow Rules and Templates)

Copyright (c) 2021-2023 Michal Zobec, ZOBEC Consulting. All Rights Reserved.  
web: www.michalzobec.cz, email: michal@zobec.cz

Jazyk | Language: Česky | English


## Úvod

**External Messages Traffic Light Rules**, zkráceně **ExMsgTLR**, či **MsgTLR** česky **Pravidla semaforu pro externí zprávy**, nebo **Pravidla semaforu pro externě doručené emaily**, je soubor pravidel, který byl vytvořen s cílem usnadnit uživatelům snadnější identifikaci doručených zpráv zaslaných externě (z internetu). Díky pravidlům založených na třech rozlišovacích identifikátorech (značkách) se mohou uživatelé snadněji rozhodovat jaké riziko vyplývá z právě přijaté zprávy.

MsgTLR poskytuje jednoduché a intuitivní pravidla pro určení odesilatele a rozhodnutí jaká rizika vyplývají z otevření přílohy, či klepnutí na odkazy ve zprávě obsažených.

## Použití

Štítky MsgTLR jsou MsgTLR:GREEN, MsgTLR:AMBER a MsgTLR:RED. V psané formě NESMÍ tyto štítky obsahovat mezery a MĚLY by být psány v přesně daném formátu "MsgTLR:\<BARVA>".  
Štítky MsgTLR MUSÍ zůstat ve své původní podobě i když jsou použity v textu v jiných jazycích: obsah může být přeložený, avšak štítky být překládány nesmějí.

## Definice pojmů MsgTLR

| Označení | Shrnutí | Podrobnosti |
| --------------------------------- | --------------------- | --------------------- |
| <span style="color: green;">**MsgTLR:GREEN**</span> | Zpráva přišla od známého kontaktu. | Odkazy a přílohy v této zprávě by měly být bezpečné.<br/>Zpráva byla doručena od neznámého kontaktu, u kterého bylo úspěšně ověřeno, že se jedná o oprávněného odesilatele zprávy. |
| <span style="color: orange;">**MsgTLR:AMBER**</span> | Varování: Zpráva přišla od neznámého kontaktu. | Odkazy a přílohy v této zprávě mohou být nebezpečné.<br/>Zpráva byla doručena od neznámého kontaktu, u kterého bylo úspěšně ověřeno, že se jedná o oprávněného odesilatele zprávy. |
| <span style="color: red;">**MsgTLR:RED**</span> | Nebezpečí: Zpráva přišla od neznámého kontaktu a neprošla ověřením. | Odkazy a přílohy v této zprávě jsou téměř jistě nebezpečné.<br/>Zpráva byla doručena od neznámého kontaktu, u kterého selhalo ověření s pomocí SPF/DKIM, čímž nebylo možné ověřit, zda je odesilatel oprávněný odesilatel zprávy. |

## Implementace

Implementace 


### Systémové požadavky

* Microsoft Exchange Server 2016
* Microsoft Exchange Server 2019
* Microsoft Exchange Online (jako součást služeb Microsoft 365, či Office 365)

### Ostatní požadavky

**Microsoft Exchange Server.** Oprávnění s právy správce, či jinými právy pro vytvoření Mail Flow.  
**Microsoft Exchange Online.** Oprávnění s právy Global Administrator, či jinými právy pro vytvoření Mail Flow.

### Implementace Mail Flow

Popis bude zaměřen pouze na službu Exchange Online, postup pro Exchange Server je podobný.




## Známé problémy


### "Zabalení" digitálně podepsané zprávy jako přílohy

Pokud budete používat oznámení pro externí zprávy a bude vám doručena zpráva s digitálním podpisem, Exchange tuto digitálně podepsanou zprávu přiloží do emailu s oznámením o externí zprávě jako přílohu.

Jedná se o vlastnost nikoli chybu, digitálně podepsanou zprávu nelze upravit, protože by se tím narušila její integrita, proto ji Exchange přesune do přílohy, aby mohl do emailu vložit oznámení o externí zprávě.

