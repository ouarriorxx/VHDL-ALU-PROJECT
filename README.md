
# Projet ALU VHDL 🛠️

Ce projet consiste en la conception d'une Unité Logique et Arithmétique (ALU) en VHDL. L'ALU est une partie essentielle de nombreux processeurs, responsable de l'exécution des opérations arithmétiques et logiques.

## Description du Projet 📝

L'ALU prend deux entrées A et B, chacune étant un vecteur de 8 bits, ainsi qu'un code d'opération de 3 bits (Op) pour spécifier l'opération à effectuer. Les opérations supportées sont : addition, soustraction, ET logique, OU logique, et XOR. L'ALU produit un résultat de 8 bits ainsi qu'un signal Zero pour indiquer si le résultat est zéro.

## Architecture 🏗️

L'architecture de l'ALU est implémentée de manière comportementale en VHDL. Elle utilise la bibliothèque IEEE et les types de données standard fournis par NUMERIC_STD pour effectuer les opérations arithmétiques.

## Utilisation 💻

1. Déclarez l'entité ALU dans votre conception VHDL.
2. Connectez les signaux d'entrée A, B et Op ainsi que les signaux de sortie Result et Zero.
3. L'ALU effectuera l'opération spécifiée par le signal Op sur les entrées A et B, produisant un résultat et un signal Zero correspondant.

Exemple de déclaration :

```vhdl
entity top_level is
    Port ( A, B : in  std_logic_vector(7 downto 0);
           Op    : in  std_logic_vector(2 downto 0);
           Result: out std_logic_vector(7 downto 0);
           Zero  : out std_logic);
end top_level;
