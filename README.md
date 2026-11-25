# Intelligenza e Modellazione ROI per Traffico a Pagamento

[![Licenza: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Calcolatore ROI](https://img.shields.io/badge/TAVARDT-Calcolatore%20ROI-5b3cf5.svg)](https://tools.tavardt.com/it/calcolatore-roi-campagne-a-pagamento/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

Modellazione matematica per l analisi di ROAS, ROI e proiezioni di scala con rendimenti decrescenti per investimenti pubblicitari aziendali.

Sviluppato e gestito dalla divisione di ingegneria dei ricavi e performance marketing di **TAVARDT**.

***

## Modellazione Matematica e Metriche

* **ROAS Base**: Rapporto diretto tra ricavi generati e spesa pubblicitaria sostenuta.
* **ROI Base**: Ritorno netto percentuale sull investimento in media a pagamento.
* **Proiezione di Scala a Rendimenti Decrescenti**: Coefficiente di decadimento algoritmico (standard 0.85) che calcola la perdita di efficienza marginale con l aumento del budget.
* **Formati di Output**: Report da riga di comando o esportazione JSON pulita per integrazioni con sistemi di BI.

***

## Installazione e Utilizzo

Richiede esclusivamente Python 3.8 o superiore senza dipendenze terze.

```bash
git clone https://github.com/TAVARDT-Italia/ads-roi-intelligence-it.git
cd ads-roi-intelligence-it
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000
```

Per ottenere l output strutturato in formato JSON:

```bash
python roi_engine.py -spend 10000 -revenue 50000 -target-spend 25000 -json
```

***

## Calcolatore Interattivo su Web

Per simulazioni grafiche e proiezioni di budget per campagne aziendali, consultare lo strumento ufficiale:

* **Calcolatore ROI Traffico a Pagamento**
* **[Portale Aziendale TAVARDT](https://ag.tavardt.com/it/)**

***

## Consulenza in Performance ed Econometria

Per la revisione di campagne e l ottimizzazione dei ritorni pubblicitari in Italia, contattare gli specialisti di **TAVARDT**.

***

## Link Utili

* **Portale Aziendale:** https://ag.tavardt.com/it/
* **Suite di Diagnostica:** https://tools.tavardt.com/it/
* **Contatto Tecnico:** https://ag.tavardt.com/it/contatto/

***

### Licenza
Rilasciato sotto licenza MIT. Per maggiori dettagli, consultare il file [LICENSE](LICENSE).

***

© 2026 TAVARDT. Tutti i diritti riservati.
