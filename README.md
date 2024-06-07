def main():
    dress_today = input("Do you want to know how to dress today? (Yes/No): ")

    if dress_today.lower() == "yes":
        askQuestions()
    else:
        print("We hope you don't get caught in the rain.")
        print("END OF PROGRAM")
        
def askQuestions():
    first_name = input("Enter your first name: ")

    while True:
        num_locations_input = input("How many locations do you want to check? ")
        if num_locations_input.isdigit():
            num_locations = int(num_locations_input)
            break
        else:
            print("You did not enter a valid number.")

    print("Hello, " + first_name + "! You want to check " + str(num_locations) + " locations.")
    checkLocations(num_locations)

def checkLocations(num_locations):
    valid_locations = {
        "London": "It's Spring. Dress for mild weather.",
        "Chicago": "It's Winter. Bundle up.",
        "India": "It's really hot! Put on some sunscreen.",
        "New York": "It's Fall. A light jacket should be fine.",
        "Sydney": "It's Summer. Wear something light and airy."
    }

    print("Valid locations: " + ", ".join(valid_locations.keys()))

    location_count = 0

    while location_count < num_locations:
        location = input("What location should I check? ")

        if location.lower() == "bye":
            print("END OF PROGRAM")
            return

        if location in valid_locations:
            print(valid_locations[location])
        else:
            print("Location Not Found")

        location_count += 1

    print("You may not check any other locations!")
    print("END OF PROGRAM")

if __name__ == "__main__":
    main()
