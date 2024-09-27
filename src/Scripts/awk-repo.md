# Repositori d'exercicis

Aquesta secció conté els exercicis realitzats pels estudiants de l'assignatura d'Administració i Manteniment de Sistemes i Aplicacions (AMSA).

## Exercicis

### Bàsics
awk -F, '($6 > 120) && ($3 == "Grass" || $3 == "Electric") { print $2, $6 }' pokemon.csv
awk -F, '$5 > 600 && $3 != "Dragon" { print $2 }' pokemon.csv


### Intermedis
awk -F, '{ if ($11 > $8) { print $2 " has more Speed (" $11 ") than Defense (" $8 ")"; } else { print $2 " has more Defense (" $8 ") than Speed (" $11 ")"; }}' pokemon.csv
awk -F, '$12 == 3 { total_hp += $6; total_attack += $7; total_defense += $8; total_spatk += $9; total_spdef += $10; total_speed += $11; n++ } END { print "Promedis de la Generació 3:\nHP:", total_hp/n, "\nAttack:", total_attack/n, "\nDefense:", total_defense/n, "\nSp. Atk:", total_spatk/n, "\nSp. Def:", total_spdef/n, "\nSpeed:", total_speed/n }' pokemon.csv


### Avançats
awk -F, '
NR > 1 {
    atac_especial[$2] = $9;
}
END {
    n = asorti(atac_especial, ordenat, "@val_num_desc");
    print "Els 5 Pokémon amb el major Sp. Atk són:";
    for (i = 1; i <= 5; i++) {
        print ordenat[i], atac_especial[ordenat[i]];
    }
}' pokemon.csv


awk -F, '
NR > 1 {
    totals[$12] += $5;
}
END {
    print "Punts totals per cada generació:";
    for (gen in totals) {
        printf "Generació %d: %d punts\n", gen, totals[gen];
    }
}' pokemon.csv
