print("Off Season = $50.00 per day /Peak Season = $150.00 per day /Standard Season = $100.00 per day")



while True:

    # Declare Variables and guatter inputs:


    strSeason = input("\nEnter The Season: (Off Season, Peak Season, Standard Season): ")
    strFirstName = input("Enter First Name: ")
    strLastName = input("Enter Last Name: ")
    strState = input("Enter State of Residence: ")
    shtnumofDays = int(input("Enter Number of Days you plan to stay: "))
    strMembership = input("Do you have AAA or AARP memberships? (Y or N): ")

    # Calculations

    #Calculate Season Price

    if strSeason == "Off Season":
        dblSeasonPrice = 50.00
    elif strSeason == "Peak Season":
        dblSeasonPrice = 150.00
    elif strSeason == "Standard Season":
        dblSeasonPrice = 100.00
    else:
        print("Invalid season entered. Defaulting to Standard Season.")
        dblSeasonPrice = 100.00

    # Calculate discount 

    dblDiscount = 0

    if shtnumofDays > 30:
        dblDiscount += 0.10
    elif shtnumofDays > 14:
        dblDiscount += 0.05

    if strMembership == "Y":
        dblDiscount += 0.025

    # Calculate Subtotal:
    dblSubTotal = dblSeasonPrice * shtnumofDays
    dblDiscountedSubTotal = dblSubTotal * (1 - dblDiscount)

    #Calculate Tax:
    if strState == "Florida":
        dblTax = 0.0
    else:
        dblTax = dblDiscountedSubTotal * 0.10

    #Calculate Final Total
    dblFinalTotal = dblDiscountedSubTotal + dblTax

    #Display:

    strSubtotal =  "${:,.2f}".format(dblDiscountedSubTotal)
    strTax =  "${:,.2f}".format(dblTax)
    strFinalTotal =  "${:,.2f}".format(dblFinalTotal)

    print("Subtotal: ",strSubtotal)
    print("Tax: ",strTax)
    print("Final Total: ", strFinalTotal)

    # Loop
    strAnotherRental = input("Another Rental? (Y or N): ")
    if strAnotherRental == "N":
        break
