Laboratorio Basi di Dati 2023/2024

Progetto di piattaforma di food delivery

Si deve progettare la base di dati per Cibora (Figura 1(a)), un innovativo servizio di food delivery per gestire i dati dei ristoranti aderenti, degli utenti con i loro relativi ordini e dei fattorini che effettuano le consegne in bicicletta.
Per beneficiare del servizio, ogni utente deve registrarsi inserendo nome, email, password, numero di telefono, indirizzo di recapito. Una volta registratosi, l’utente deve inserire un mezzo di pagamento (es.: carta di credito, paypal, satispay) e ricaricare il proprio borsellino elettronico. Il borsellino ha un saldo che viene aggiornato ad ogni ordinazione e l'utente può ricaricare il proprio borsellino in qualsiasi momento. Inoltre, gli utenti possono sottoscrivere la modalità premium che garantisce una priorità sugli ordini.
L’utente può collezionare codici di sconto da utilizzare al momento dell'ordine in base al numero di ordini effettuati in passato.
Ogni ristorante (Figura 1(b)) è rappresentato da un nome, una descrizione, un indirizzo, il costo della spedizione, un’immagine di profilo e un numero di stellette aggiornato ogni lunedì sulla base della percentuale di recensioni positive dell’ultima settimana. Ogni ristorante appartiene a una o più categorie in base al tipo di cibo offerto (ad esempio: fast food, vegetariano, ...).
I ristoranti che dimostrano di saper garantire un ottimo servizio (almeno 20 ordini consegnati correttamente, una valutazione clienti maggiore o uguale a 4.5 stelline su cinque, una percentuale massima di ordini annullati dal ristorante dell’1.5%, una percentuale massima di ordini con reclami del 2.5%) sono considerati Top Partner. I Top Partner compaiono in sezioni dedicate all’interno dell’app mobile Cibora e ricevono uno speciale badge che attesta il loro servizio eccellente, aiutando ad aumentare la credibilità e ottenere la fiducia dei clienti. Per i Top Partner si vuole tenere traccia della data in cui sono entrati a far parte della categoria.
I ristoranti propongono agli utenti una lista di piatti da ordinare. Ogni portata ha un titolo, un’immagine, una lista di ingredienti, una lista di allergeni, il prezzo e un eventuale sconto. Inoltre, ogni piatto appartiene ad una o più liste (es. i più venduti, promozioni, dolci, salato, ecc.).

 Ogni utente può selezionare una lista di pietanze ed effettuare l’ordine. Finché non sono affidati ad un rider per la consegna, gli ordini possono essere annullati sia dai clienti, sia dai ristoratori. Nel profilo dell’utente si possono ispezionare gli ordini passati ed eventualmente effettuare dei reclami inviando un messaggio al ristorante.

Figura 1 (a) La lista dei ristoranti con filtro “Hamburger”. (b) I dettagli di un ristorante.
Il sistema gestisce un numero arbitrario di riders dove ogni rider è identificato da un codice, dallo stato (occupato/disponibile/fuori servizio), dalla posizione aggiornata in tempo reale tramite GPS. I riders sono classificati in base al tipo di mezzo che utilizzano (bicicletta normale, bicicletta elettrica, monopattino). I riders che utilizzano il monopattino devono indicare quanti km possono effettuare prima che si scarichi la batteria.
Al momento dell'ordine, il sistema trova il rider libero con la somma minima della distanza dal ristorante più la distanza dall’utente. Tuttavia, per ordini che prevedano un tragitto “posizione corrente del rider-> ristorante-> cliente” superiore ai 10 km, solo i rider con bici elettrica vengono interpellati. Per monitorare le prestazioni dei ciclofattorini, si vuole tenere traccia del numero di consegne effettuate da ognuno, del momento in cui il cibo da consegnare viene affidato ad un rider e, per le consegne già completate, anche dell’ora in cui l’ordine è stato recapitato al cliente.
Dopo che l’ordine è stato effettuato l’utente ha la possibilità di chattare sia con il ristorante che con il rider in caso ci fossero dei problemi con l’ordine come mancata consegna o netto ritardo.
Quando l’ordine è consegnato l’utente può recensire il ristorante e il rider con una valutazione da 1 a 5 e un commento testuale. Il commento testuale è facoltativo.
Inoltre è anche presente la possibilità di dare una mancia al rider per la consegna.
Una volta al mese, vengono aggiornate le seguenti classifiche:

● Riders più veloci nel consegnare gli ordini
● Cibi più popolari
● Ristoranti con più recensioni positive
● Clienti che hanno speso di più



Schema guida per la consegna 
La consegna del progetto deve consistere in un file pdf redatto secondo il seguente schema:

1. Progettazione concettuale
1.1. Requisiti iniziali.
1.2. Glossario dei termini.
1.3. Requisiti rivisti e strutturati in gruppi di frasi omogenee.
Consiglio: verificare la coerenza dei requisiti ristrutturati rispetto al glossario.
1.4. Schema E-R + business rules.
Consiglio: verificare la bontà dello schema E-R (+ business rules) sulla base delle qualità
descritte in tabella.

Qualità Verifica Suggerimenti
Correttezza Controllare che i costrutti siano usati
propriamente, sia dal punto di vista
sintattico, sia dal punto di vista
semantico.

Nella stesura dello schema E-R non bisogna considerare come verrà
tradotto in relazionale. Evitare errori come:
• Omettere gli identificatori delle entità.
• Aggiungere identificatori alle associazioni.
• Aggiungere alle associazioni gli identificatori delle entità
coinvolte.
• Non indicare il tipo di generalizzazione (totale o parziale,
esclusiva o sovrapposta).
• Dare lo stesso nome a due entità o associazioni.
• Riportare come business rule un’informazione che può
essere rappresentata nello schema E-R.
• Usare un identificatore esterno basato su associazioni non
(1,1) o un identificatore basato su attributi opzionali o
multivalore.

2. Progettazione logica
2.1. Tavola dei volumi (con motivazione delle scelte effettuate).
2.2. Tavola delle operazioni.
Consiglio: includere le operazioni ritenute più rilevanti, basandosi anche sui requisiti e motivare
le scelte effettuate.
2.3. Ristrutturazione dello schema E-R:
2.3.1. Analisi delle ridondanze: elencare tutte le ridondanze rilevate ed effettuare la
seguente analisi dettagliata solo per una delle ridondanze individuate, producendo, per
ogni operazione significativa su cui la presenza/assenza della ridondanza può avere effetto:
• Schema di navigazione relativo all’operazione in presenza e in assenza di
ridondanza.
• Tavola degli accessi in presenza e in assenza di ridondanza.
• Confronto in spazio e tempo tra presenza e assenza di ridondanza.
• Scelta se introdurre o non introdurre la ridondanza con motivazione.
2.3.2. Eliminazione delle generalizzazioni (con motivazione delle scelte effettuate).
2.3.3. Eventuale partizionamento/accorpamento di entità e associazioni (con motivazione
delle scelte effettuate).
2.3.4. Eventuale scelta degli identificatori principali (con motivazione delle scelte
effettuate).
2.4. Schema E-R ristrutturato + business rules.
2.5. Schema relazionale (con indicazione dei vincoli di integrità referenziale).

3. Implementazione
3.1. DDL di creazione del database.
3.2. DML di popolamento di tutte le tabelle del database.
Consiglio: se popolate il database con dati verosimili potreste rendervi conto di errori commessi
nella fase di progettazione concettuale e di cui avreste dovuto rendervi conto prima.
3.3. Qualche operazione di cancellazione e modifica per verificare i vincoli e gli effetti causati da
operazioni su chiavi esterne.