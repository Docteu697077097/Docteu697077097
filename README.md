import math


# Fonction pour calculer le discriminant
def calculer_discriminant():

    def discriminant(a, b, c):
        delta = b**2 - 4 * a * c
        return delta

    def obtenir_coefficient(message):
        while True:
            try:
                coeff = float(input(message))
                return coeff
            except ValueError:
                print("\nVeuillez entrer un nombre valide SVP!!!")

    while True:
        a = obtenir_coefficient("Entrez le coefficient a : ")
        b = obtenir_coefficient("Entrez le coefficient b : ")
        c = obtenir_coefficient("Entrez le coefficient c : ")

        delta = discriminant(a, b, c)
        print("Le discriminant est :", delta)

        if delta > 0:
            x1 = (-b + math.sqrt(delta)) / (2 * a)
            x2 = (-b - math.sqrt(delta)) / (2 * a)
            print(
                "Delta est supérieur à 0, elle admet 2 racines réelles distinctes :"
            )
            print("X1 :", x1)
            print("X2 :", x2)
        elif delta == 0:
            x = -b / (2 * a)
            print("Delta est égal à 0, elle admet une racine double : X =", x)
        else:
            print("L'équation n'a pas de racine réelle.")
            reponse = input(
                "\nVoulez-vous entrer de nouveaux coefficients ? (oui ou non) : "
            )
            if reponse.lower() != "oui":
                break


# Fonction pour la calculatrice
def calculatrice():
    operations = {
        "+": lambda x, y: x + y,
        "-": lambda x, y: x - y,
        "*": lambda x, y: x * y,
        "/": lambda x, y: x / y if y != 0 else "\nErreur : Division par zéro",
    }

    def obtenir_nombre(message):
        while True:
            try:
                nombre = float(input(message))
                return nombre
            except ValueError:
                print("\nVeuillez entrer un nombre valide.")

    def calculer(nombre1, nombre2, operateur):
        if operateur in operations:
            return operations[operateur](nombre1, nombre2)
        else:
            return "Opérateur invalide"

    while True:
        print("\nChoisissez une opération :")
        for operateur in operations:
            print(f"{operateur}")

        operateur = input("Entrez l'opérateur : ")

        nombre1 = obtenir_nombre("Entrez le premier nombre : ")
        nombre2 = obtenir_nombre("Entrez le deuxième nombre : ")

        resultat = calculer(nombre1, nombre2, operateur)
        print(f"Le résultat est : {resultat}")

        continuer = input(
            "Voulez-vous faire un autre calcul ? (oui ou non) : ")
        if continuer.lower() != 'oui':
            break


# Boucle principale
while True:
    choix = input(
        "Quelle opération voulez-vous effectuer ? \n\n(DISCRIMINANT)= 1 \nOu \n(CALCULATRICE)= 2 : \n\nEntre👉: "
    )
    if choix.lower() == "1":
        print(
            '\nVoici la table du discriminant. \nVous pouvez entrer les coefficients pour que calcule le discriminant!!',
            calculer_discriminant())
    elif choix.lower() == "2":
        print('\nVoici la table de la calculatrice!!', calculatrice())
    else:
        print("\n😢😢Choix invalide!!.  Veuillez choisir entre le chiffre 《 1 》 et 《 2 》.")
        print('\nSVP!! RÉESSAYER!! LE 1 est pour le DISCRIMINANT et 2 pour la CALCULATRICE😇😇😇😇\n\n\n')
