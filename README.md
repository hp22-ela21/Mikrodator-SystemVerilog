# Mikrodator-SystemVerilog
Implementering av en 8-bitars mikrodator i SystemVerilog, som kan användas för referens vid CPU-konstruktion i VHDL i kursen Hårdvarunära programmering.
Denna CPU skall sedan kunna sammankopplas med en Raspberry Pi för enkel kommunikation som en del av projekt II (grupprojekt för er som siktar på högre betyg). 

Syftet med denna referensmodell är att ni skall få ett litet hum om hur en CPU kan byggas upp. Samtidigt är koden skriven i SystemVerilog i stället för VHDL så att ni
inte kan kopiera denna rakt av. Ni kommer nog märka att mycket av det vi gick igenom i Inbyggda system 1 (RAM- och ROM-minne, programräknare, instruktionsregister,
ALU, stacken, CPU:ns instruktionscykel med mera) är implementerat här.

Ett litet program för att blinka en lysdiod vid nedtryckning av en tryckknapp är implementerad via maskinkod. Dock används konstanter som passeras till en funktion
döpt assemble för att sammansätta detta till en 24-bitars instruktion skriven i maskinkod, vilket medför att en instruktion såsom LDI R16, (1 << LED) passeras via
funktionsanropet assemble(LDI, R16, (1 << LED)), vilket översätts till 24'h011001.

Det finns två befintliga klockkällkor, en 50 MHz systemklocka för reguljär användning samt en manuell klocka implementerad via nedtryckning av en tryckknapp.
När den manuella klockkällan används, så skrivs aktuell OP-kod samt innehållet i CPU-register R16 ut via fem 7-segmentdisplayer.
Adressen som programräknaren pekar på skrivs också ut på binär form via åtta lysdioder på FPGA-kortet.

Samtliga PINs har tilldelats för FPGA-kort Altera DE0 (enhet Cyclone V - 5CEBA4F23C7).
Koden skrevs mellan 2022-07-13 - 2022-07-15 med Intel Quartus Prime 18.1.
Ladda ned arkivfilen mcu.qar för att öppna hela projektet direkt i Quartus.
