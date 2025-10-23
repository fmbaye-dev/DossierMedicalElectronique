# Système XML/XSD de Gestion des Dossiers Médicaux d’un Hôpital

## Description du projet
Ce projet a pour objectif de concevoir un système XML/XSD complet et modulaire pour la gestion des dossiers médicaux d’un hôpital.  
Il permet de structurer et valider les données liées aux patients, au personnel médical, aux consultations, aux examens médicaux et aux hospitalisations.

Le système repose sur une architecture multi-schémas :  
un fichier principal (hopital.xsd) qui référence plusieurs schémas secondaires (patients.xsd, personnel.xsd, soins.xsd).

---

## Structure du projet

- hopital.xsd : Schéma principal (point d’entrée)  
- patients.xsd : Types liés aux patients  
- personnel.xsd : Types du personnel médical  
- soins.xsd : Consultations, examens et hospitalisations  

- patients-exemple.xml : Exemple de 5 patients  
- consultations-exemple.xml : Exemple de 4 consultations avec prescriptions  
- examens-exemple.xml : Exemple de 3 examens médicaux  
- hospitalisations-exemple.xml : Exemple de 2 hospitalisations  

---

## Architecture des schémas

| Fichier XSD   | Rôle                                                                          | Inclus dans |
|---------------|-------------------------------------------------------------------------------|-------------|
| hopital.xsd   | Schéma principal : racine du système et point d’entrée pour la validation XML |      —      |
| patients.xsd  | Définit la structure et les contraintes du type Patient                       | hopital.xsd |
| personnel.xsd | Définit les types pour le personnel médical                                   | hopital.xsd |
| soins.xsd     | Contient les définitions des consultations, examens et hospitalisations       | hopital.xsd |

Les schémas secondaires sont référencés dans hopital.xsd avec <xs:include>.

---

## Composants du système

### Patients
- Numéro patient : PAT-XXXXXXXX  
- Nom, prénom, date de naissance, sexe  
- CNI ou passeport  
- Groupe sanguin : A+, A-, B+, B-, AB+, AB-, O+, O-  
- Personne à contacter en cas d’urgence : nom, relation, téléphone  
- Allergies connues (optionnelles, 0..n)  
- Maladies chroniques (0..n)  

### Personnel médical
- Matricule : MED-XXXXX (médecins) ou INF-XXXXX (infirmiers)  
- Nom complet  
- Spécialité (pour médecins) : Généraliste, Cardiologue, Pédiatre, Chirurgien, etc.  
- Service  
- Téléphone professionnel  

### Consultations
- ID consultation : CONS-YYYYMMDD-XXXX  
- Date et heure  
- Numéro patient  
- Matricule médecin  
- Motif de consultation  
- Symptômes (1 à 10)  
- Diagnostic  
- Prescriptions (0..n) : médicament, dosage, posologie, durée  
- Examens demandés (optionnel)  
- Prochain rendez-vous (optionnel)  

### Examens médicaux
- ID examen : EXAM-XXXXXXXX  
- Type : Analyse de sang, Radiographie, IRM, Scanner, Échographie  
- Date de réalisation  
- Numéro patient  
- Résultats (texte libre ou structuré)  
- Commentaires technicien  
- Urgent (booléen)  

### Hospitalisations
- Numéro d’admission  
- Numéro patient  
- Date admission  
- Date sortie prévue/effective (optionnelle)  
- Service / Chambre  
- Médecin responsable  
- Motif hospitalisation  
- Notes quotidiennes (0..n)    

---

## Auteurs
- Fatou Gaye Mbaye
- Ndeye Amy Ciss 
- Projet académique : Gestion des dossiers médicaux hospitaliers avec XML/XSD  
- Développement Backend
