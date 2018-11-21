# 102
Hänga gubben

import random

def gissning():
    for bok in gissningar:
        if bok == bokstav:
            print("Du har redan gissat på " + str(bokstav) + ".")
            return True

def matchar():
    gissning = False

    for bok in range(len(gubbe)):
        if bokstav == gubbe[bok]:
            res[bok] = gubbe[bok]
            gissning = True

    if gissning == True:
        print("\nHurra! Ordet innehåller " + str(bokstav) + ".\n")
    else:
        print("\nAttans! Ordet innehåller inte något " + str(bokstav) + ".")

    return gissning

def spela_igen():
    mera = input("Vill du spela igen?")
    if mera == "ja":
        print("Nytt ord genererat!\n")
        return 1
    elif mera == "nej":
        print("Tack för den här gången!")
        return 0
    else:
        print("Mata in ja eller nej")
        spela_igen()


print("Välkommen till hänga gubben! För att se tidigare gissningar, mata in 112.")
spela_mera = 1

while spela_mera == 1:
    ord = ["paranoid", "pass", "peptalk", "polemik", "pondus", "populist", "praxis", "precisering", "princip", "profan", "profit", "profylax", "prognos", "prominent", "protektionistisk"]
    gubbe = random.choice(ord)
    res = ["_"]*len(gubbe)
    gissningar_kvar=7
    gissningar=[]
    ratt_svar = 0

    for b in res:
        print(b, end=" ")
    print("")

    while gissningar_kvar >= 1 and ratt_svar == 0:
        bokstav = input("Gissa på en bokstav:")
        if bokstav.isalpha() == True and len(bokstav) == 1:
            if not gissning() == True:
                gissningar.append(bokstav)
                if matchar() == False:
                    gissningar_kvar -=1
                    print("Du har " + str(gissningar_kvar)+ " gissningar kvar innan du blir hängd.\n")
            for b in res:
                print(b, end=" ")
            print("")
            if res.count("_") == 0:
                ratt_svar = 1
        elif bokstav == "112":
            print("Du har tidigare gissat på ", end="")
            for b in range(len(gissningar)):
                if not b == len(gissningar)-1:
                    print(gissningar[b], end=", ")
                else:
                    print(gissningar[b],end=".\n\n")
        else:
            print("Ogiltig inmatning. Försök igen.\n")

    if gissningar_kvar == 0:
        print("Du lyckades inte gissa rätt och är nu hängd. Rätt svar var " + str(gubbe) + ".")
        spela_mera = spela_igen()

    if ratt_svar == 1:
        print("Grattis! Du gissade rätt och lever för att hängas en annan dag!\n")
        spela_mera = spela_igen()
