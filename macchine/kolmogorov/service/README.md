# LDAP

Esempi e documentazione su LDAP.

- `$ ldapsearch -x -LLL "cn=<username>"`
  
  La prima sezione corrisponde al _gruppo_ dell'utente, mentre la seconda è il vero e proprio account dell'utente. 
  
  ```
  dn: cn=<username>,ou=Group,dc=phc,dc=unipi,dc=it
  cn: <username>
  objectClass: posixGroup
  objectClass: top
  gidNumber: <uid>

  dn: uid=<username>,ou=People,dc=phc,dc=unipi,dc=it
  sn: <cognome>
  objectClass: person
  objectClass: organizationalPerson
  objectClass: inetOrgPerson
  objectClass: posixAccount
  objectClass: shadowAccount
  objectClass: top
  uidNumber: <uid>
  givenName: <nome>
  description: <descrizione: "studente|dottorando|esterno|...">
  gecos: <nome_completo>
  uid: <username>
  mail: <email>
  homeDirectory: /home/<username>
  loginShell: /bin/bash
  cn: <username>
  gidNumber: <uid>
  ```
  
  | Label | Descrizione |
  |-------|-------------|
  | `<username>` | Username dell'utente |
  | `<nome>` | Nome dell'utente |
  | `<cognome>` | Cognome dell'utente |
  | `<uid>` | ID unico dell'utente |
  | `<email>` | Email dell'utente |
  | `<nome_completo>` | Nome completo dell'utente |
  
  
