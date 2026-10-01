# Introduzione a Huawei VRP

## Cos'è VRP

VRP (**Versatile Routing Platform**) è il sistema operativo di rete sviluppato da Huawei e utilizzato su numerose famiglie di router e switch.

VRP fornisce funzionalità per:

- switching Ethernet
- routing IPv4 e IPv6
- OSPF
- IS-IS
- BGP
- MPLS
- Segment Routing
- VPN
- QoS
- DHCP Client e Server
- PPPoE
- sicurezza
- gestione e monitoraggio

La disponibilità delle singole funzionalità dipende dalla piattaforma hardware, dalla versione VRP e dalle licenze installate.

Esistono principalmente due versioni di sistema operativo VRP:
- VRP 5.x
- VRP 8.x

La principale differenza che noterai usando queste due versioni di VRP è che VRP 5.x non richiede (**commit**) per applicare il comando inserito, mentre per VRP 8.x è necessario applicare i comandi inseriti con (**commit**) al termine delle operazioni.

---

## Interfaccia CLI

La configurazione degli apparati Huawei può essere effettuata tramite **Command Line Interface (CLI)**. Esistono altre modalità, tra cui pagina web, con cui è possibile impostare molti comandi (ma non tutti).

In questo corso Zero Huawei tratterò solo i comandi tramite la CLI.

La (**CLI**) è accessibile tramite:
- porta console fisica seriale RS232
- connessione SSH sicura via IP
- connessione Telnet in chiaro via IP

Per accedere tramite **porta console** è necessario utilizzare un cavo terminale, il quale da una parte ha un connettore RS232 (o una porta USB che funge da convertitore USB-RS232) e dall'altra parte da un connettore RJ45 8 poli con i contatti elettrici con i segnali TX, RX, GND necessari per la comunicazione full duplex con l'apparato.

Ecco un esempio di cavo console da poter acquistare:
[https://amzn.eu/d/003kn2gm](https://amzn.eu/d/003kn2gm)

I parametri da impostare sulla porta di comunicazione sono:
```text
9600 bps
8 bit di dati
N nessun bit di parità
1 bit di stop
```

Un software emulatore di terminale per poter aprire una sessione è **Putty**
Particolarmente utile per me è stato aver impostato il carattere **Backspace key** con l'opzione **Control-?**.

In questo corso useremo il software di emulazione **eNSP di Huawei**, per cui non ti servirà avere questa intrefaccia fisica per seguire il corso Zero Huawei.
Tuttavia è importante conoscere questi aspetti quando metterai le mani su un apparato fisico.

Dopo l'accesso al dispositivo viene normalmente visualizzata la **User View**:

```text
<Huawei>
```

Nella **User View** è principalmente possibile visualizzare informazioni diagnostiche, ma non è possibile applicare configurazioni. Per applicare configurazioni è necessario passare nella **System View** tramite il comando:

```text
<Huawei>system-view
[Huawei]
```

La System View permette di modificare la configurazione del dispositivo.
Per tornare alla view precedente, in questo caso alla User View, si usa il comando **quit**:

```text
[Huawei]quit
<Huawei>
```

Se ti trovi all'interno di un altra pagina di configurzione, ad esempio quella di un'interfaccia (interface-view), il comando **quit** ti riporta alla **system-view**.

In questo caso puoi usare il comando **quit** due volte:

```text
[Huawei]interface GigabitEthernet 0/0/0
[Huawei-GigabitEthernet0/0/0]quit
[Huawei]quit
<Huawei>
```

Un'altro modo per ritornare alla user-view da qualsiasi vista in cui ti trovi, e tramite il comando **return**:

```text
[Huawei-GigabitEthernet0/0/0]return
<Huawei>
```

Esiste anche una scorciatoia da tastiera per eseguire il returna alla **user-view** ed è **CTRL+Z**.
