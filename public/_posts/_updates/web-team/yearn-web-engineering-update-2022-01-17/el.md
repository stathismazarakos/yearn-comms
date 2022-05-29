---
layout: post
title: "Web Engineering Update: Jan. 17th"
categories: [Updates]
image: ./Jan-17/logo.png
author: f0xTheSin
translator: giosereth
publish: true
---

Πηγή: https://yearnweb.substack.com/p/yearn-web-engineering-update-7d7

# Ενημερώσεις του Ιστότοπου του Yearn

### Για την εβδομάδα που ξεκινάει στις 17 Ιανουαρίου 2022

## **Περίληψη**

Παρουσιάζουμε μια μεγάλη έκδοση αυτή την εβδομάδα με τις εργαλειοθήκες APY να κάνουν την εμφάνισή τους. Μπορείτε τώρα να βλέπετε πιο λεπτομερείς πληροφορίες όταν περνάτε το ποντίκι σας πάνω από το APY ενός θησαυροφυλακίου. Η οριστικοποίηση των βελτιώσεων ασφαλείας παραμένει το βασικό μας μέλημα, με την προσθήκη των θησαυροφυλακίων στο Arbitrum να είναι το επόμενο βήμα, καθώς και περισσότερη η βελτίωση του UI/UX στις διάφορες αλυσίδες που υποστηρίζουμε.

Άλλες ενημερώσεις περιλαμβάνουν την εξάλειψη των μικρών υπολοίπων που συχνά προέκυπταν μετά από αναλήψεις από τα θησαυροφυλάκια, την υποστήριξη ενός νέου θησαυροφυλακίου LINK στο Fantom και διορθώσεις στο UI για το yvBOOST και την Iron Bank.

## **Πεπραγμένα ✅**

### **Web Release 1.0.8 (17 Jan 2022)**

- επίτευγμα: βελτιωμένες οδηγίες στο readme 📚
- επίτευγμα: APY tooltips για θησαυροφυλάκια και εργαστήρια

  - Περνώντας με το ποντίκι πάνω από το APY ενός θησαυροφυλακίου στη σελίδα των θησαυροφυλακίων ή στη σελίδα των λεπτομερειών θα παρέχει τώρα μια παρόμοια ανάλυση όπως αυτή που φαίνεται στον ιστότοπο v2, με επιπλέον πληροφορίες για τα θησαυροφυλάκια Curve LP.

- επίτευγμα: προσθήκη διαδρομής για την διενέργεια health status 🏘️
- επίτευγμα: προσθήκη εντολής απόσυρση όλων από τα θησαυροφυλάκια

  - Προηγουμένως, κατά την ανάληψη, το περιβάλλον εργασίας μετέτρεπε την εισαγωγή του υποκείμενου υπολοίπου των token από τον χρήστη σε token του θησαυροφυλακίου και στη συνέχεια τα μετέφερε στο συμβόλαιο του θησαυροφυλακίου μέσω της εντολής `withdraw(shares)`. Ωστόσο, εάν η τιμή των token αυξανόταν μετά από μια συγκομιδή, αυτό θα μπορούσε να αφήσει στο χρήστη σκόνη (ένα μικρό, κλασματικό ποσό σε token του θησαυροφυλακίου). Τώρα, το UI ανιχνεύει αν ένας χρήστης προσπαθεί να αποσύρει όλη τη θέση του από το θησαυροφυλάκιο, και αντ' αυτού περνάει το `withdraw(max_uint)`, το οποίο θα κάψει όλες τις συμμετοχές στο θησαυροφυλάκιο του χρήστη και δεν θα αφήσει καθόλου σκόνη ακόμα και αν η τιμή της συμμετοχής αυξάνεται σε κάθε μπλοκ.

- διόρθωση: υπολογισμός μεριδίου απόσυρσης στα labs

  - Υπήρχε ένα πρόβλημα με την εμφάνιση του ποσού yveCRV που θα λάμβανε ένας χρήστης από μια ανάληψη yvBOOST λόγω του ειδικού χειρισμού του token του θησαυροφυλακίου (yvBOOST) ως token εμφάνισης. Αυτό έχει διορθωθεί.

- στυλ: κανόνας eslint για εντολή εισαγωγής 📝

### **Έκδοση SDK 1.0.15 (19 Jan 2022)**

- επίτευγμα: προσθήκη λίστας αδειών
- chore(deps): αύξηση του shelljs από 0.8.4 σε 0.8.5
- επίτευγμα: ενεργοποίηση των ci tests σε pull requests
- διόρθωση(account.summaryof): αγνοήσε labs θησαυροφυλάκια για τον υπολογισμό των χαρτοφυλακίων
- διόρθωση: επίλυση της έλλειψης εισαγωγής fetch

### **Διάφορα**

- επίτευγμα: ζωντανό πλαίσιο παρακολούθησης του ιστότοπου
- διόρθωση: ενημέρωση του ορίου δανεισμού των χρηστών

  - Αυτή η διόρθωση του UI λαμβάνει υπόψη το ανώτατο όριο ασφάλειας ενός περιουσιακού στοιχείου όταν εμφανίζει το όριο δανεισμού ενός χρήστη για την Iron Bank

- διόρθωση: ενημέρωση των υπολογισμών για τις νέες δεξαμενές ρευστότητας του curve
- διόρθωση: σφάλμα εμφάνισης του yvBoost
- επίτευγμα: αφαίρεση της παράκαμψης νέου τύπου για θησαυροφυλάκια καμπύλης
- διόρθωση: εμφάνιση συνολικού ενεργητικού
- διόρθωση:σφάλμα απόσυρσης για το yvBoost
- επίτευγμα: εισαγωγή συνδέσμου για το logo στο fantom 
- επίτευγμα: εισαγωγή link για τις πληροφορίες του θησαυροφυλακίου
- διόρθωση: αγνόηση των θησαυροφυλακίων lab στον υπολογισμό των χαρτοφυλακίων
- διόρθωση: επίληση της εισαγωγής missing fetch

## **Συνεχής ανάπτυξη και εκκρεμή ζητήματα**

- **Κύκλος εστίασης 🎯 **

  - Ολοκλήρωση και αποστολή βελτιώσεων ασφαλείας, με μια πλήρη δημοσίευση που θα εμβαθύνει περισσότερο σύντομα.
  - Το Arbitrum έρχεται! Σε αυτόν τον κύκλο, η ομάδα για την ανάπτυξη της ιστοσελίδας φέρνει το Arbitrum στο προσκήνιο, καθώς ξεκινάμε τις δοκιμές και την ενσωμάτωση των θυσαυροφυλακίων.
  - Με τα θησαυροφυλάκια να λανσάρονται σύντομα στην τρίτη αλυσίδα που υποστηρίζουμε, το Yearn σχεδιάζει ένα UI/UX για πολλές ακόμα αλυσίδες, ώστε να επιτρέπει στους χρήστες να βλέπουν πιο εύκολα τις τρέχουσες θέσεις τους και τις νέες ευκαιρίες σε όλες τις υποστηριζόμενες αλυσίδες του οικοσυστήματος της Yearn.
  
- **Τρέχοντα θέματα 🐛**

  - Σφάλμα μετανάστευσης Vault: Μετά τη μετάβαση, ορισμένοι χρήστες πρέπει να ανανεώσουν τη σελίδα πριν εμφανιστεί το νέο θησαυροφυλάκιο και να εξαφανιστεί το παλιό. Δύσκολο να αναπαραχθεί με συνέπεια (2/16 προσπάθειες στο Fantom), αυτό το σφάλμα φαίνεται να οφείλεται σε μια εσφαλμένη ευθυγράμμιση των δεδομένων μεταξύ του RPC πορτοφολιού και του SDK μας.
  - Σφάλμα JSON-RPC: Αυτό φαίνεται να εμφανίζεται συχνότερα στο Fantom. Η βελτιωμένη αποστολή μηνυμάτων σφάλματος στο frontend θα βοηθήσει καλύτερα τους χρήστες να προσδιορίσουν αν αντιμετωπίζουν ένα πραγματικό σφάλμα RPC ή κάτι άλλο.

## **Ελάτε να χτίσετε μαζί μας!  :man_mechanic:**

- Προσθέτουμε συνεχώς δημόσια θέματα στο GitHub μας και καλωσορίζουμε πάντα νέες συνεισφορές σε οποιοδήποτε από τα repos μας

  - https://github.com/yearn/yearn-finance-v3
  - https://github.com/yearn/yearn-sdk
  - https://github.com/yearn/yearn-exporter
  - https://github.com/yearn/yearn-lens
  - https://github.com/yearn/yearn-meta