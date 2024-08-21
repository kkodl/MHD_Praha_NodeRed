# MHD_Praha_NodeRed
This is a example of extracting data from public transport servers in Prague. The goal is to querry server for departure times and line numbers at given public transport stop. The extract is performed via Node Red. The rest of document is in Czech, as far as it is a local content...

flow_with_filters.json contain:
- filter of departutres - not all departing lines might be of interest
- time offset for querry ("time to walk to stop") - this has to be added / edited at the end of the golemio querry URL in first node.

NEW: flow_with_ac.json
  - In case the vehicle is equipped with air condition, there is an asterisk in front of the line number
  - Excessive backslashes removed from Golemio API querry, as per Golemio support note

Querry
as was:

/v2/pid/departureboards/?ids=U693Z2P&total=3&preferredTimezone=Europe%2FPrague&minutesBefore=-9

as it is now:

/v2/pid/departureboards?ids=U693Z2P&total=3&preferredTimezone=Europe%2FPrague&minutesBefore=-9

  - Regarding backslash see below the short note in CZ:


(REST specifikace sama o sobě není standardem, který by formálně definovat zacházení s lomítky na konci URL. REST (Representational State Transfer) je architektonický styl navržení síťových aplikací, zejména webových služeb, a zatímco má určité obecně přijímané principy, neexistují pro něj žádné striktní pravidla či specifikace podobné těm, jaké má například W3C pro HTML. Nicméně, v praxi se doporučuje zacházet s URL konzistentně, což zahrnuje i zacházení s lomítky na konci URL. Obecně:

Lomítko na konci URL může indikovat, že odkazovaný zdroj je "adresář" nebo kontejner, který může obsahovat další zdroje. V tomto kontextu je URL s lomítkem na konci (/path/to/resource/) někdy interpretováno jako odkaz na adresář, zatímco URL bez lomítka (/path/to/resource) jako odkaz na konkrétní zdroj.

Tady asi vadilo že url se dá do cache 2x pod různým klíčem (jednou pod /v2/pid/departureboards a podruhé pod /v2/pid/departureboards/))



Ostatní města?

Nevím. Snažil jsem se najít Brno a Plzeň a pak jsem toho nechal, podle dostupných aplikací ta data existují, ale jsou za zdí. Pokud někdo najdete někde něco, ozvěte se, rád budu spolupracovat. Pokud něco objevím, bude to tady.

