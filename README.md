# ansible-lab

Baseline-roll för Linux-servrar, byggd som labb.

Rollen gör följande:
- installerar basverktyg
- skapar användare och sätter rätt admingrupp beroende på OS
- sätter lösenord från en krypterad Ansible Vault-fil
- skapar /opt/app med rätt behörigheter
- genererar en inloggningsbanner från en Jinja2-mall
- härdar SSH (PermitRootLogin no, MaxAuthTries 3) med validering innan filen skrivs
- startar om SSH via en handler, men bara när konfigurationen ändrats

Körs med:

    ansible-playbook site.yml -K --ask-vault-pass

Testas med --syntax-check, ansible-lint och --check --diff före skarp körning.
