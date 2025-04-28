```markdown
# SQL : Commandes et Concepts Fondamentaux

Ce document présente une synthèse des commandes SQL essentielles et des concepts clés, structurés de manière professionnelle et claire.

---

## **Commandes de Définition de Données (DDL)**

### 1. **Suppression d'une Table**
- **Commande**: `DROP TABLE`
- **Description**: Supprime définitivement une table et ses données.
- **Syntaxe**:
  ```sql
  DROP TABLE nom_table;
  ```

### 2. **Vidage d'une Table**
- **Commande**: `TRUNCATE TABLE`
- **Description**: Supprime toutes les données d'une table tout en conservant sa structure.
- **Syntaxe**:
  ```sql
  TRUNCATE TABLE nom_table;
  ```

### 3. **Modification d'une Table (Ajout de Colonne)**
- **Commande**: `ALTER TABLE`
- **Description**: Ajoute une nouvelle colonne à une table existante.
- **Syntaxe**:
  ```sql
  ALTER TABLE nom_table ADD nom_colonne TYPE_DONNEES(255);
  ```
  **Exemple**:
  ```sql
  ALTER TABLE PAYMENT ADD hichem VARCHAR(255);
  ```

---

## **Commandes de Manipulation de Données (DML)**

### 4. **Insertion de Données**
- **Commande**: `INSERT INTO`
- **Description**: Insère des données dans une table.
- **Syntaxes**:
  ```sql
  -- Insertion sans préciser les colonnes
  INSERT INTO nom_table VALUES (valeur1, valeur2, ...);
  
  -- Insertion en spécifiant les colonnes
  INSERT INTO nom_table (colonne1, colonne2) VALUES (valeur1, valeur2);
  ```

### 5. **Mise à Jour de Données**
- **Commande**: `UPDATE`
- **Description**: Modifie des données existantes dans une table.
- **Syntaxe**:
  ```sql
  UPDATE nom_table
  SET colonne = 'nouvelle_valeur'
  WHERE condition;
  ```
  **Exemple**:
  ```sql
  UPDATE PAYMENT SET hichem = 'ikram' WHERE Load_number = 23;
  ```

### 6. **Suppression de Lignes**
- **Commande**: `DELETE`
- **Description**: Supprime des lignes spécifiques d'une table.
- **Syntaxe**:
  ```sql
  DELETE FROM nom_table WHERE condition;
  ```

---

## **Contraintes de Table**

### 7. **Valeurs Non Nullables**
- **Description**: Garantit qu'une colonne ne contient pas de valeurs `NULL`.
- **Syntaxe**:
  ```sql
  CREATE TABLE nom_table (
      colonne INTEGER NOT NULL
  );
  ```

### 8. **Valeurs Uniques**
- **Description**: Assure que toutes les valeurs d'une colonne sont distinctes.
- **Syntaxe**:
  ```sql
  CREATE TABLE nom_table (
      colonne INTEGER UNIQUE
  );
  ```

### 9. **Contrainte Unique Composite**
- **Description**: Combine plusieurs colonnes pour garantir l'unicité.
- **Syntaxe**:
  ```sql
  CREATE TABLE nom_table (
      colonne1 TYPE,
      colonne2 TYPE,
      CONSTRAINT nom_contrainte UNIQUE (colonne1, colonne2)
  );
  ```

### 10. **Clé Primaire**
- **Description**: Identifie de manière unique chaque ligne (non nullable et unique).
- **Syntaxe**:
  ```sql
  CREATE TABLE nom_table (
      colonne1 TYPE,
      colonne2 TYPE,
      PRIMARY KEY (colonne1, colonne2)
  );
  ```

### 11. **Auto-incrémentation**
- **Description**: Génère automatiquement des valeurs uniques pour une colonne.
- **Syntaxe**:
  ```sql
  CREATE TABLE nom_table (
      id INTEGER PRIMARY KEY AUTOINCREMENT
  );
  ```

### 13. **Clé Étrangère**
- **Description**: Lie une colonne à une autre table pour maintenir l'intégrité référentielle.
- **Syntaxe**:
  ```sql
  CREATE TABLE nom_table (
      colonne TYPE,
      FOREIGN KEY (colonne) REFERENCES autre_table(colonne_cible)
  );
  ```

---

## **Concepts Avancés**

### 12. **Super Clé vs Clé Candidate**
- **Super Clé**: Ensemble de colonnes identifiant de manière unique une ligne (ex: `{id, nom, prénom}`).
- **Clé Candidate**: Super clé minimale (ex: `id` seul si unique).

### 15. **Vues**
- **Description**: Représentation virtuelle de données issues d'une ou plusieurs tables.
- **Syntaxe**:
  ```sql
  CREATE VIEW nom_vue AS
  SELECT colonne1, colonne2
  FROM nom_table;
  ```

### 16. **Clause CASE**
- **Description**: Exécute des conditions pour retourner des valeurs spécifiques.
- **Syntaxe**:
  ```sql
  SELECT 
      CASE
          WHEN condition1 THEN resultat1
          WHEN condition2 THEN resultat2
          ELSE resultat_par_defaut
      END
  FROM nom_table;
  ```

---

## **Requêtes et Clauses**

### 14. **GROUP BY**
- **Description**: Regroupe des lignes partageant les mêmes valeurs.
- **Exemple**:
  ```sql
  SELECT colonne, COUNT(*)
  FROM nom_table
  GROUP BY colonne;
  ```

### 15. **HAVING**
- **Description**: Filtre les groupes résultants de `GROUP BY`.
- **Exemple**:
  ```sql
  SELECT colonne, COUNT(*)
  FROM nom_table
  GROUP BY colonne
  HAVING COUNT(*) > 5;
  ```

### 17. **Produit Cartésien**
- **Description**: Combine toutes les lignes de deux tables.
- **Syntaxe**:
  ```sql
  SELECT * FROM table1, table2;
  ```

---

## **Notes Finales**
- Utilisez `DROP TABLE` avec précaution, car elle supprime définitivement les données.
- Préférez `TRUNCATE` à `DELETE` pour un vidage complet plus rapide.
- Les vues optimisent les requêtes complexes et renforcent la sécurité des données.
``` 
