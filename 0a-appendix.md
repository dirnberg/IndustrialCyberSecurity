# Plant Security (in Work)
## Policies
% Passwort Richtlinie

## Physical Security
% Physikalischer Zugriff - USB Schnittstellen minimalst verwenden

# Network Security (in Work)

##  Microsegmentation with Industrial Firewalls 
% Netzwerkeinstellungen: IP-Adressen, Netzwerknamen, Hardware Firewall werden vom Betreiber zur Verfügung gestellt.

## Secure Communication
% - Sichere Kommunikation
% smbv2+ oder FTPs Fileshares inkl. Einhaltung Betreiber Password Richtlinie

## Secure Remote Access 
% Fernwartung, -diagnose, -Fehlerbehebung
% VNC, RDP, MSRA
% Anlagenfernwartung durch Freischaltung seitens Betreiber nur für „named User“ von externe Dienstleister

# System Integrity (in Work)

## System Hardening
%Deaktivierung von nicht benötigen Funktionen, Users
%Keine Defaultpasswörter laut Handbuch etc.
%Rechteverwaltung User local minimieren, wenn möglich LDAP verwenden

## Access Control and User Management

## Security Logging and Monitoring

% Restrikter Zugang zum Internet für Devices, ausgenommen Proxy Zugang für ausgehende Fernwartung

## Patchability
%- Im Zuge von Anlagenservices (min. 1x pro Jahr) sollten sicherheitsrelevante Patches und Upgrades eingespielt werden können.
% Security patching

## Backup and Restore
%Backup und  Recovery von PCs (wenn vorhanden) - Datensicherung wird bei jeder Änderung auf den Device durchgeführt und auf sicheren Laufwerkshares dem Betreiber übertragen Weiters wird ein Konzept überlegt wenn ein PCs ausfällt -  Entweder Ersatzhardware vor Ort oder Schnelle Ersatzhardwarelieferung innerhalb der tolerierbaren Ausfallszeit inkl. Anleitung wie Deivce wiederhergestellt oder intergriert werden kann

## Malware Protection
%d