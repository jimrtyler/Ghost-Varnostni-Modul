# 👻 Ghost Varnostni Modul
**PowerShell Temelječe Orodje za Krepitev Varnosti Windows in Azure**

> **Proaktivna krepitev varnosti za Windows končne točke in Azure okolja.** Ghost zagotavlja funkcije krepitve, ki temeljijo na PowerShell, ki lahko pomagajo zmanjšati pogosta vektorja napadov z onemogočanjem nepotrebnih storitev in protokolov.

## ⚠️ Pomembna Opozorila

**TESTIRANJE OBVEZNO**: Vedno najprej testirajte Ghost v ne-produkcijskih okoljih. Onemogočanje storitev lahko vpliva na legitimne poslovne funkcije.

**BREZ GARANCIJ**: Čeprav Ghost cilja na pogoste vektorje napadov, nobeno varnostno orodje ne more preprečiti vseh napadov. To je ena komponenta v celoviti varnostni strategiji.

**OPERACIJSKI VPLIV**: Nekatere funkcije lahko vplivajo na funkcionalnost sistema. Pred razporeditvijo pazljivo preglejte vsako nastavitev.

**STROKOVNA OCENA**: Za produkcijska okolja se posvetujte z varnostnimi strokovnjaki, da zagotovite, da so nastavitve usklajene s potrebami vaše organizacije.

## 📊 Varnostna Pokrajina

Škoda zaradi ransomware je dosegla **57 milijard dolarjev leta 2025**, raziskave kažejo, da mnogi uspešni napadi izkoriščajo osnovne Windows storitve in napačne konfiguracije. Pogosti vektorji napadov vključujejo:

- **90% incidentov ransomware** vključuje izkoriščanje RDP
- **Ranljivosti SMBv1** so omogočile napade kot sta WannaCry in NotPetya
- **Makri dokumentov** ostajajo primarni način dostavljanja malware
- **Napadi, ki temeljijo na USB** še naprej ciljajo na omrežja z zračno vrzeljo
- **Zloraba PowerShell** se je v zadnjih letih močno povečala

## 🛡️ Ghost Varnostne Funkcije

Ghost zagotavlja **16 funkcij krepitve Windows** plus **integracija varnosti Azure**:

### Krepitev Windows Končnih Točk

| Funkcija | Namen | Razmisleki |
|----------|---------|----------------|
| `Set-RDP` | Upravlja dostop Remote Desktop | Lahko vpliva na oddaljeno administracijo |
| `Set-SMBv1` | Nadzoruje zastarel protokol SMB | Potreben za zelo stare sisteme |
| `Set-AutoRun` | Nadzoruje AutoPlay/AutoRun | Lahko vpliva na udobje uporabnika |
| `Set-USBStorage` | Omejuje USB pomnilniške naprave | Lahko vpliva na legitimno uporabo USB |
| `Set-Macros` | Nadzoruje izvajanje Office makrov | Lahko vpliva na dokumente z omogočenimi makri |
| `Set-PSRemoting` | Upravlja PowerShell remoting | Lahko vpliva na oddaljeno upravljanje |
| `Set-WinRM` | Nadzoruje Windows Remote Management | Lahko vpliva na oddaljeno administracijo |
| `Set-LLMNR` | Upravlja protokol razreševanja imen | Običajno varno za onemogočitev |
| `Set-NetBIOS` | Nadzoruje NetBIOS preko TCP/IP | Lahko vpliva na podedovane aplikacije |
| `Set-AdminShares` | Upravlja administrativne delitve | Lahko vpliva na oddaljeni dostop do datotek |
| `Set-Telemetry` | Nadzoruje zbiranje podatkov | Lahko vpliva na diagnostične zmožnosti |
| `Set-GuestAccount` | Upravlja račun gosta | Običajno varno za onemogočitev |
| `Set-ICMP` | Nadzoruje ping odzive | Lahko vpliva na omrežno diagnostiko |
| `Set-RemoteAssistance` | Upravlja Remote Assistance | Lahko vpliva na operacije pomoči |
| `Set-NetworkDiscovery` | Nadzoruje odkrivanje omrežja | Lahko vpliva na brskanje po omrežju |
| `Set-Firewall` | Upravlja Windows Firewall | Kritično za omrežno varnost |

### Azure Oblačna Varnost

| Funkcija | Namen | Zahteve |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Omogoča osnovno Azure AD varnost | Microsoft Graph dovoljenja |
| `Set-AzureConditionalAccess` | Konfigurira politike dostopa | Azure AD P1/P2 licenciranje |
| `Set-AzurePrivilegedUsers` | Revidira privilegirane račune | Global Admin dovoljenja |

### Možnosti Poslovne Razporeditve

| Metoda | Primer Uporabe | Zahteve |
|--------|----------|--------------|
| **Neposredno Izvajanje** | Testiranje, majhna okolja | Lokalne admin pravice |
| **Group Policy** | Domenova okolja | Domenski admin, GP upravljanje |
| **Microsoft Intune** | Oblačno upravlja naprave | Intune licenciranje, Graph API |

## 🚀 Hiter Start

### Varnostna Ocena
```powershell
# Naložite modul Ghost
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Preverite trenutno varnostno držo
Get-Ghost
```

### Osnovna Krepitev (Najprej Testirajte)
```powershell
# Bistvena krepitev - najprej testirajte v laboratorijskem okolju
Set-Ghost -SMBv1 -AutoRun -Macros

# Preglejte spremembe
Get-Ghost
```

### Poslovna Razporeditev
```powershell
# Razporeditev Group Policy (domenova okolja)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Razporeditev Intune (oblačno upravljane naprave)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Metode Namestitve

### Možnost 1: Neposredno Prenašanje (Testiranje)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Možnost 2: Namestitev Modula
```powershell
# Namestite iz PowerShell Gallery (ko je na voljo)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Možnost 3: Poslovna Razporeditev
```powershell
# Kopirajte na omrežno lokacijo za razporeditev Group Policy
# Konfigurirajte Intune PowerShell skripte za oblačno razporeditev
```

## 💼 Primeri Primerov Uporabe

### Majhno Podjetje
```powershell
# Osnovna zaščita z minimalnim vplivom
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Zdravstveno Okolje
```powershell
# HIPAA osredotočena krepitev
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Finančne Storitve
```powershell
# Konfiguracija visoke varnosti
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Cloud-First Organizacija
```powershell
# Intune upravljana razporeditev
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Podrobnosti Funkcij

### Ključne Funkcije Krepitve

#### Omrežne Storitve
- **RDP**: Blokira dostop do oddaljenega namizja ali randomizirata vrata
- **SMBv1**: Onemogoči zastarel protokol za deljenje datotek
- **ICMP**: Prepreči ping odzive za reconnaissance
- **LLMNR/NetBIOS**: Blokira zastarele protokole razreševanja imen

#### Varnost Aplikacij
- **Makri**: Onemogoči izvajanje makrov v Office aplikacijah
- **AutoRun**: Prepreči samodejno izvajanje z odstranljivih medijev

#### Oddaljeno Upravljanje
- **PSRemoting**: Onemogoči oddaljene PowerShell seje
- **WinRM**: Ustavi Windows Remote Management
- **Remote Assistance**: Blokira povezave oddaljene pomoči

#### Nadzor Dostopa
- **Admin Shares**: Onemogoči C$, ADMIN$ delitve
- **Guest Account**: Onemogoči dostop računa gosta
- **USB Storage**: Omeji uporabo USB naprav

### Azure Integracija
```powershell
# Povežite se z Azure najemnikom
Connect-AzureGhost -Interactive

# Omogočite varnostne privzete nastavitve
Set-AzureSecurityDefaults -Enable

# Konfigurirajte pogojni dostop
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Revidirajte privilegirane uporabnike
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune Integracija (Novo v v2)
```powershell
# Povežite se z Intune
Connect-IntuneGhost -Interactive

# Razporedite preko Intune politik
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Pomembni Razmisleki

### Zahteve za Testiranje
- **Laboratorijsko Okolje**: Najprej testirajte vse nastavitve v izoliranem okolju
- **Postopna Razporeditev**: Postopno razporedite za identifikacijo problemov
- **Načrt Vračanja**: Zagotovite, da lahko povrnete spremembe, če je potrebno
- **Dokumentacija**: Zabeležite, katere nastavitve delujejo za vaše okolje

### Možen Vpliv
- **Produktivnost Uporabnikov**: Nekatere nastavitve lahko vplivajo na dnevne delovne tokove
- **Podedovane Aplikacije**: Starejši sistemi morda potrebujejo določene protokole
- **Oddaljeni Dostop**: Razmislite o vplivu na legitimno oddaljeno administracijo
- **Poslovni Procesi**: Preverite, da nastavitve ne pokvarijo kritičnih funkcij

### Varnostne Omejitve
- **Obramba v Globino**: Ghost je ena plast varnosti, ne popolna rešitev
- **Stalno Upravljanje**: Varnost zahteva stalno spremljanje in posodobitve
- **Usposabljanje Uporabnikov**: Tehnični nadzor mora biti seznanjen z varnostno ozaveščenostjo
- **Evolucija Groženj**: Nove metode napada lahko zaobidejo trenutno zaščito

## 🎯 Primeri Scenarijev Napada

Čeprav Ghost cilja na pogoste vektorje napadov, specifična preprečevanje je odvisno od pravilne implementacije in testiranja:

### Napadi v Slogu WannaCry
- **Ublažitev**: `Set-Ghost -SMBv1` onemogoči ranljiv protokol
- **Razmisleki**: Zagotovite, da noben podedovan sistem ne potrebuje SMBv1

### RDP Temelječ Ransomware
- **Ublažitev**: `Set-Ghost -RDP` blokira dostop do oddaljenega namizja
- **Razmisleki**: Morda potrebuje alternativne metode oddaljenega dostopa

### Malware, ki Temelji na Dokumentih
- **Ublažitev**: `Set-Ghost -Macros` onemogoči izvajanje makrov
- **Razmisleki**: Lahko vpliva na legitimne dokumente z omogočenimi makri

### USB Dostavljene Grožnje
- **Ublažitev**: `Set-Ghost -USBStorage -AutoRun` omeji USB funkcionalnost
- **Razmisleki**: Lahko vpliva na legitimno uporabo USB naprav

## 🏢 Poslovne Značilnosti

### Podpora Group Policy
```powershell
# Aplicirajte nastavitve preko Group Policy registra
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Nastavitve se aplicirajo po celotni domeni po GP osvežitvi
gpupdate /force
```

### Microsoft Intune Integracija
```powershell
# Ustvarite Intune politike za Ghost nastavitve
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Politike se samodejno razporedijo na upravljane naprave
```

### Poročanje o Skladnosti
```powershell
# Generirajte poročilo varnostne ocene
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure poročilo varnostne drže
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Najboljše Prakse

### Pred Razporeditvijo
1. **Dokumentirajte Trenutno Stanje**: Zaženite `Get-Ghost` pred spremembami
2. **Skrbno Testirajte**: Validirajte v ne-produkcijskem okolju
3. **Načrtujte Rollback**: Vedite, kako povrniti vsako nastavitev
4. **Pregled Zainteresiranih Strani**: Zagotovite, da poslovne enote odobrijo spremembe

### Med Razporeditvijo
1. **Postopen Pristop**: Najprej razporedite v pilotne skupine
2. **Spremljajte Vpliv**: Pazite na pritožbe uporabnikov ali sistemske probleme
3. **Dokumentirajte Probleme**: Zabeležite kakršne koli probleme za prihodnjo referenco
4. **Komunicirajte Spremembe**: Obvestite uporabnike o varnostnih izboljšavah

### Po Razporeditvi
1. **Redna Ocena**: Periodično zaženite `Get-Ghost` za preverjanje nastavitev
2. **Posodobite Dokumentacijo**: Vzdržujte trenutne varnostne konfiguracije
3. **Preglejte Učinkovitost**: Spremljajte varnostne incidente
4. **Stalno Izboljševanje**: Prilagodite nastavitve na podlagi pokrajine groženj

## 🔧 Odpravljanje Težav

### Pogoste Težave
- **Napake Dovoljenj**: Zagotovite povišano PowerShell sejo
- **Odvisnosti Storitev**: Nekatere storitve morda imajo odvisnosti
- **Kompatibilnost Aplikacij**: Testirajte s poslovnimi aplikacijami
- **Omrežna Povezljivost**: Preverite, da oddaljeni dostop še vedno deluje

### Možnosti Obnovitve
```powershell
# Ponovno omogočite specifične storitve, če je potrebno
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 O Avtorju

**Jim Tyler** - Microsoft MVP za PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ naročnikov)
- **Glasilo**: [PowerShell.News](https://powershell.news) - Tedensko varnostno obveščanje
- **Avtor**: "PowerShell for Systems Engineers"
- **Izkušnje**: Desetletja PowerShell avtomatizacije in Windows varnosti

## 📄 Licenca in Zavrnitev Odgovornosti

### MIT Licenca
Ghost je zagotovljen pod MIT licenco za brezplačno uporabo, modificiranje in distribucijo.

### Varnostna Zavrnitev Odgovornosti
- **Brez Garancije**: Ghost je zagotovljen "kot je" brez garancije kakršne koli vrste
- **Testiranje Potrebno**: Vedno najprej testirajte v ne-produkcijskih okoljih
- **Strokovno Vodstvo**: Posvetujte se z varnostnimi strokovnjaki za produkcijske razporeditve
- **Operacijski Vpliv**: Avtorji niso odgovorni za kakršne koli operacijske motnje
- **Celovita Varnost**: Ghost je ena komponenta v popolni varnostni strategiji

### Podpora
- **GitHub Issues**: [Prijavite napake ali zahtevajte funkcije](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentacija**: Uporabite `Get-Help <function> -Full` za podrobno pomoč
- **Skupnost**: PowerShell in varnostni forumi skupnosti

---

**🔒 Okrepite svojo varnostno držo z Ghost - vendar vedno najprej testirajte.**

```powershell
# Začnite z oceno, ne s predpostavkami
Get-Ghost
```

**⭐ Označite ta repozitorij z zvezdico, če Ghost pomaga izboljšati vašo varnostno držo!**