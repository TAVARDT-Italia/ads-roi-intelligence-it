<p align="center">
  <a href="https://ag.tavardt.com/it/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Intelligenza e Modellazione Matematica del ROI nelle Campagne a Pagamento

[![Calcolatore ROI](https://img.shields.io/badge/TAVARDT-Calcolatore%20ROI-5b3cf5.svg)](https://tools.tavardt.com/it/calcolatore-roi-campagne-a-pagamento/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Motore matematico deterministico per l'analisi di ROAS, ROI e proiezioni di scala non lineari con fattori di rendimenti decrescenti negli investimenti pubblicitari.

Lo strumento fornisce a responsabili del traffico a pagamento, ingegneri di crescita e analisti di dati un modello econometrico rigoroso per simulare l'incremento di budget senza presumere rendimenti lineari irrealistici. Sviluppato senza alcuna dipendenza esterna, opera nativamente in ambienti Python e JavaScript.

***

## Fondamenti Algoritmici e Modellazione Matematica

Le proiezioni puramente lineari negli investimenti pubblicitari generano gravi distorsioni finanziarie e aspettative di profitto infondate. Nelle aste pubblicitarie reali, l'aumento della spesa provoca saturazione del pubblico, affaticamento degli annunci e un incremento sistematico dei costi marginali.

* **Calcolo del ROAS Base**: Rapporto diretto tra ricavi lordi e spesa pubblicitaria (`revenue / spend`), che misura l'efficienza operativa immediata.
* **Calcolo del ROI Base**: Rendimento percentuale netto sul capitale pubblicitario allocato (`((revenue - spend) / spend) * 100`), evidenziando la redditività reale.
* **Proiezione Non Lineare con Rendimenti Decrescenti**: Applica un esponente di decadimento `(decay_factor - 1)` al rapporto di spesa `(target_spend / current_spend)` per stimare la flessione del ROAS.
* **Perdita di Efficienza Marginale**: Quantifica la riduzione percentuale di efficienza determinata dall'espansione del budget verso una nuova soglia obiettivo.
* **Architettura Isomorfa Doppia**: Formule matematiche identiche implementate nella libreria standard Python (`roi_engine.py`) e in JavaScript puro (`calculator.js`).

***

## Matrice delle Metriche e Modellazione Matematica

<table>
  <thead>
    <tr>
      <th align="left">Metrica / Parametro</th>
      <th align="left">Formula Algoritmica</th>
      <th align="left">Comportamento Matematico</th>
      <th align="left">Utilità per la Decisione Strategica</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>ROAS Base</strong></td>
      <td><code>revenue / spend</code></td>
      <td>Quoziente lineare diretto arrotondato a due cifre decimali.</td>
      <td>Valuta l'efficienza operativa immediata prodotta per ogni unità monetaria investita.</td>
    </tr>
    <tr>
      <td><strong>ROI Base</strong></td>
      <td><code>((revenue - spend) / spend) * 100</code></td>
      <td>Margine percentuale netto ottenuto dalla spesa pubblicitaria.</td>
      <td>Conferma la generazione di utile netto dopo il recupero integrale del capitale speso.</td>
    </tr>
    <tr>
      <td><strong>Rapporto di Spesa</strong></td>
      <td><code>target_spend / current_spend</code></td>
      <td>Moltiplicatore di espansione orizzontale del budget durante i test di scala.</td>
      <td>Indica l'ampiezza relativa dell'incremento di liquidità immesso nelle aste.</td>
    </tr>
    <tr>
      <td><strong>ROAS Proiettato</strong></td>
      <td><code>current_roas * (spend_ratio ** (decay_factor - 1))</code></td>
      <td>Degradazione non lineare indotta dalla saturazione delle audience di riferimento.</td>
      <td>Evita di sovrastimare i ricavi lordi durante fasi di accelerazione della spesa.</td>
    </tr>
    <tr>
      <td><strong>Ricavi Proiettati</strong></td>
      <td><code>target_spend * projected_roas</code></td>
      <td>Fatturato lordo stimato tenendo conto della legge dei rendimenti decrescenti.</td>
      <td>Verifica se i ricavi marginali supplementari compensano i costi operativi associati.</td>
    </tr>
    <tr>
      <td><strong>Perdita di Efficienza</strong></td>
      <td><code>(1 - (projected_roas / current_roas)) * 100</code></td>
      <td>Contrazione percentuale del ROAS base al crescere dell'investimento complessivo.</td>
      <td>Misura con precisione il costo di efficienza sostenuto per conquistare nuovo volume.</td>
    </tr>
  </tbody>
</table>

***

## Installazione e Guida Rapida all'Uso

Richiede Python 3.8 o superiore utilizzando esclusivamente librerie standard (`sys`, `json`, `argparse`). Non è richiesta alcuna installazione aggiuntiva tramite pip.

Clonare il repository ed eseguire l'analisi iniziale nel terminale:

```bash
git clone https://github.com/TAVARDT-Italia/ads-roi-intelligence-it.git
cd ads-roi-intelligence-it
python roi_engine.py -s 10000 -r 50000 -ts 25000
```

Per esportare i risultati in formato strutturato JSON:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 25000 -j
```

Regolare il fattore di decadimento in mercati caratterizzati da forte competizione:

```bash
python roi_engine.py -s 10000 -r 50000 -ts 30000 -d 0.78
```

Per applicazioni Node.js o dashboard nel browser, utilizzare il modulo `calculator.js`:

```javascript
const ROI_Calculator = require('./calculator.js');

const base = ROI_Calculator.calculateBaseMetrics(10000, 50000);
console.log('ROAS Base:', base.roas, 'ROI Base:', base.roi);

const proiezione = ROI_Calculator.projectScale(10000, 25000, base.roas, 0.85);
console.log('ROAS Proiettato:', proiezione.projectedROAS);
console.log('Perdita di Efficienza:', proiezione.efficiencyLoss + '%');
```

Esempio di payload JSON restituito:

```json
{
  "currency": "EUR",
  "current_spend": 10000.0,
  "current_revenue": 50000.0,
  "base_metrics": {
    "roas": 5.0,
    "roi": 400.0
  },
  "scaling_projection": {
    "target_spend": 25000.0,
    "decay_factor": 0.85,
    "projection": {
      "projected_roas": 4.36,
      "projected_revenue": 109000.0,
      "efficiency_loss": 12.8
    }
  }
}
```

***

## Domande Frequenti (FAQ Tecnico)

### In che modo il fattore di decadimento modella i rendimenti decrescenti nella scala pubblicitaria?
Il fattore di decadimento (`-d`, valore predefinito 0.85) funge da esponente `(decay_factor - 1)` applicato al rapporto di crescita del budget. All'aumentare dell'investimento, le impressioni marginali risentono della saturazione delle audience e di aste più competitive, contraendo il ROAS secondo modelli econometrici consolidati.

### Quali sono le differenze operative tra lo script Python e il modulo JavaScript?
Entrambi i componenti eseguono le medesime formule matematiche e regole di arrotondamento decimale. Lo script Python (`roi_engine.py`) è ideato per esecuzioni da riga di comando e flussi di automazione, mentre `calculator.js` si integra nativamente in backend Node.js e interfacce web lato client.

### Come può essere integrato l'output JSON nelle pipeline di BI e data warehouse?
Specificando il parametro `-j`, lo script invia una stringa JSON valida direttamente sullo standard output. Tale flusso può essere processato mediante utility come jq o importato senza conversioni in ambienti come BigQuery, Snowflake o warehouse aziendali.

### Per quale motivo lo strumento non include librerie di terze parti o chiamate API esterne?
L'assenza di librerie esterne assicura esecuzione deterministica, azzera i rischi di sicurezza derivanti dalla supply chain del software e garantisce velocità di calcolo istantanea. Ciò permette il funzionamento in ambienti CI/CD protetti o container privi di accesso a internet.

### Come protegge la metrica di perdita di efficienza marginale dalla crescita non redditizia?
La perdita di efficienza marginale quantifica la riduzione percentuale tra il ROAS iniziale e quello proiettato. Se la flessione calcolata colloca il rendimento al di sotto del punto di pareggio economico, gli operatori possono bloccare l'incremento di spesa prima di generare perdite nette.

***

## Consulenza in Ingegneria dei Ricavi

Per l'ottimizzazione del budget pubblicitario, la modellazione econometrica e la crescita del business B2B in Italia, contattare gli esperti di **TAVARDT Italia**.

***

## Link Utili

* **Portale Aziendale:** https://ag.tavardt.com/it/
* **Suite di Diagnostica:** https://tools.tavardt.com/it/
* **Contatto Tecnico:** https://ag.tavardt.com/it/contatto/

***

### Licenza
Rilasciato sotto Licenza MIT.

***

© 2026 TAVARDT. Tutti i diritti riservati.
