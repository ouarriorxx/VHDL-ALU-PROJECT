
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
![WhatsApp Image 2024-05-18 à 22 43 45_75708208](https://github.com/ouarriorxx/VHDL-ALU-PROJECT/assets/143946046/19c7e222-bb6c-4e95-b496-68caf61dbb2a)

```vhdl
entity top_level is
    Port ( A, B : in  std_logic_vector(7 downto 0);
           Op    : in  std_logic_vector(2 downto 0);
           Result: out std_logic_vector(7 downto 0);
           Zero  : out std_logic);
end top_level;
```
Pour la partie architecture :
![WhatsApp Image 2024-05-18 à 22 43 59_c25454eb](https://github.com/ouarriorxx/VHDL-ALU-PROJECT/assets/143946046/cc867eba-5829-409d-8ce3-9c138a1128de)

```vhdl
architecture Behavioral of alu is
begin
    process(A, B, Op)
        variable Temp: signed(7 downto 0); 
    begin
        -- Effectue l'opération arithmétique ou logique appropriée en fonction de Op
        Temp := signed(A) + signed(B);         -- Addition par défaut
        case Op is
            when "000" => Result <= std_logic_vector(Temp);         -- Addition
            when "001" => Temp := signed(A) - signed(B); Result <= std_logic_vector(Temp);          -- Soustraction
            when "010" => Result <= A AND B;        -- ET logique
            when "011" => Result <= A OR B;       -- OU logique
            when "100" => Result <= A XOR B;     -- XOR
            when others => Result <= (others => 'X'); -- Résultat indéterminé pour d'autres opcodes
        end case;
        
        -- Détermine si le résultat est zéro
        if Temp = 0 then
            Zero <= '1';  -- Résultat est zéro
        else
            Zero <= '0';  -- Résultat n'est pas zéro
        end if;
    end process;
end Behavioral;
```
![WhatsApp Image 2024-05-18 à 22 44 56_034b00e3](https://github.com/ouarriorxx/VHDL-ALU-PROJECT/assets/143946046/64aae75e-1cea-4590-9ace-62c2441dcdb9)
