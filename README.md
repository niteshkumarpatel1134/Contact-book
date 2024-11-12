contact_list = []

def menu():
    while True:
        print("1. View Contacts")
        print("2. Add Contact")
        print("3. Search Contact")
        print("4. Update Contact")
        print("5. Delete Contact")
        print("6. Exit")
        choice = input("Select an option: ")

        if choice == "1":
            view_contacts()
        elif choice == "2":
            name = input("Enter name: ")
            phone = input("Enter phone number: ")
            email = input("Enter email: ")
            address = input("Enter address: ")
            print(add_contact(name, phone, email, address))
        elif choice == "3":
            search_term = input("Enter name or phone number to search: ")
            results = search_contact(search_term)
            if results:
                for result in results:
                    print(f"Name: {result['name']}, Phone: {result['phone']}")
            else:
                print("No contacts found.")
        elif choice == "4":
            name = input("Enter name of the contact to update: ")
            updated_name = input("Updated name (leave blank to keep current): ")
            updated_phone = input("Updated phone (leave blank to keep current): ")
            updated_email = input("Updated email (leave blank to keep current): ")
            updated_address = input("Updated address (leave blank to keep current): ")

            updated_details = {
                "name": updated_name if updated_name else None,
                "phone": updated_phone if updated_phone else None,
                "email": updated_email if updated_email else None,
                "address": updated_address if updated_address else None
            }
            print(update_contact(name, updated_details))
        elif choice == "5":
            name = input("Enter name of the contact to delete: ")
            print(delete_contact(name))
        elif choice == "6":
            break
        else:
            print("Invalid option. Please try again.")

menu()
