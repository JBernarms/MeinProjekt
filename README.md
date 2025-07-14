1. Einrichtung des GitHub-Repositories

- Ein neues Repository mit dem Namen MeinProjekt auf GitHub erstellt



2. SSH-Schlüssel erstellen (falls noch nicht vorhanden)


```
	bash


	ssh-keygen -t rsa -b 4096 -C "jonathan.bernhardt@gmail.com"
```

- Den Anweisungen folgen (Enter drücken für Standardpfad, optional Passphrase)



- Öffentlichen Schlüssel anzeigen:


```
	bash


	cat ~/.ssh/id\_rsa.pub
```


- Schlüssel bei GitHub unter Settings - SSH and GPG keys hinzufügen



3. Repository lokal klonen \& konfigurieren


```
	bash


	git clone git@github.com:JBernarms/MeinProjekt.git

	cd MeinProjekt

	git config user.name "JBernarms"

	git config user.email "jonathan.bernhardt@gmail.com"
```

4. Initiale Datei erstellen \& Commit

```
	bash


	echo 'print("Hallo Welt")' > main.py

	git add main.py

	git commit -m "Initialer Commit"
```

5. Feature-Branch erstellen \& neue Datei hinzufügen


```
	bash

	
	git checkout -b feature

	mkdir -p utils

	echo '# Datenbankfunktionen' > utils/database.py

	git add utils/database.py

	git commit -m "Neue Funktion hinzugefügt"
```

6. Änderungen an main.py auf feature-Branch


```
	bash

	
	echo 'print("Feature-Version")' >> main.py

	git add main.py

	git commit -m "Hauptdatei aktualisiert"
```

7. Zurück zum Hauptbranch (main) \& Änderung dort

```

	bash



	git checkout main

	echo 'print("Main-Version")' >> main.py

	git add main.py

	git commit -m "Hauptdatei aktualisiert"
```

8. Merge-Versuch & Konflikt

```
	bash


	git merge feature
```

Erwarteter Fehler:


```
	pgsql


	Auto-merging main.py

	CONFLICT (content): Merge conflict in main.py

	Automatic merge failed; fix conflicts and then commit the result.
```

9. Merge-Konflikt manuell gelöst in main.py:

```
	python


	print("Hallo Welt")
	print("Main-Version")
	print("Feature-Version")
```

Dann:


```
	bash

	
	git add main.py

	git commit -m "Konflikt beim Merge gelöst"
```

10. Repository auf GitHub pushen

```
	bash
	
	git push -u origin main
```

