# Cricket-World-Cup-Nations-and-Records
import customtkinter as ctk  

# Dataset
world_cup_data = {
    "India": {"Wins": 2, "Finals": 3, "Run Scorer": "Sachin Tendulkar", "Wicket Taker": "Zaheer Khan", "Captain": "MS Dhoni"},
    "Australia": {"Wins": 5, "Finals": 7, "Run Scorer": "Ricky Ponting", "Wicket Taker": "Glenn McGrath", "Captain": "Ricky Ponting"},
    "West Indies": {"Wins": 2, "Finals": 3, "Run Scorer": "Chris Gayle", "Wicket Taker": "Joel Garner", "Captain": "Clive Lloyd"},
    "England": {"Wins": 1, "Finals": 4, "Run Scorer": "Joe Root", "Wicket Taker": "Chris Woakes", "Captain": "Eoin Morgan"},
    "Pakistan": {"Wins": 1, "Finals": 2, "Run Scorer": "Javed Miandad", "Wicket Taker": "Wasim Akram", "Captain": "Imran Khan"},
    "Sri Lanka": {"Wins": 1, "Finals": 3, "Run Scorer": "Kumar Sangakkara", "Wicket Taker": "Muttiah Muralitharan", "Captain": "Aravinda de Silva"},
    "New Zealand": {"Wins": 0, "Finals": 2, "Run Scorer": "Martin Guptill", "Wicket Taker": "Trent Boult", "Captain": "Kane Williamson"},
    "South Africa": {"Wins": 0, "Finals": 3, "Run Scorer": "Jacques Kallis", "Wicket Taker": "Dale Steyn", "Captain": "Graeme Smith"},
    "Bangladesh": {"Wins": 0, "Finals": 0, "Run Scorer": "Shakib Al Hasan", "Wicket Taker": "Mashrafe Mortaza", "Captain": "Mashrafe Mortaza"},
    "Zimbabwe": {"Wins": 0, "Finals": 1, "Run Scorer": "Andy Flower", "Wicket Taker": "Heath Streak", "Captain": "Alistair Campbell"}
}

# Function to display results based on user's query
def display_result():
    # Retrieve the country selected
    selected_country = country_var.get()
    query_choice = query_var.get()

    # Access the data for the selected country
    data = world_cup_data[selected_country]

    # Handle the query selection and display the result
    if query_choice == 1:
        result_label.configure(text=f"{selected_country} has won {data['Wins']} World Cups.")
    elif query_choice == 2:
        result_label.configure(text=f"{selected_country} has played {data['Finals']} finals.")
    elif query_choice == 3:
        result_label.configure(text=f"The leading run scorer for {selected_country} is {data['Run Scorer']}.")
    elif query_choice == 4:
        result_label.configure(text=f"The leading wicket taker for {selected_country} is {data['Wicket Taker']}.")
    elif query_choice == 5:
        result_label.configure(text=f"The most successful captain for {selected_country} is {data['Captain']}.")
    else:
        result_label.configure(text="Invalid choice. Please select a valid option.")

# Create the main window using customtkinter
root = ctk.CTk()
root.title("World Cup Information")

# Set window size
root.geometry("600x400")

# Create a label to prompt for country selection
ctk.CTkLabel(root, text="Select a country:", font=("Arial", 14)).pack(pady=10)

# Create a variable to hold the selected country
country_var = ctk.StringVar(value="India")

# Create a dropdown to select country
country_dropdown = ctk.CTkOptionMenu(root, values=list(world_cup_data.keys()), variable=country_var, font=("Arial", 12))
country_dropdown.pack(pady=10)

# Create a label for the query prompt
ctk.CTkLabel(root, text="What would you like to know?", font=("Arial", 14)).pack(pady=10)

# Create a variable to hold the query choice
query_var = ctk.IntVar(value=1)

# Create radio buttons for the user to select what they want to know
ctk.CTkRadioButton(root, text="Number of World Cups won", variable=query_var, value=1, font=("Arial", 12)).pack(pady=5)
ctk.CTkRadioButton(root, text="Number of finals played", variable=query_var, value=2, font=("Arial", 12)).pack(pady=5)
ctk.CTkRadioButton(root, text="Leading run scorer", variable=query_var, value=3, font=("Arial", 12)).pack(pady=5)
ctk.CTkRadioButton(root, text="Leading wicket taker", variable=query_var, value=4, font=("Arial", 12)).pack(pady=5)
ctk.CTkRadioButton(root, text="Most successful captain", variable=query_var, value=5, font=("Arial", 12)).pack(pady=5)

# Create a button to display the result
submit_button = ctk.CTkButton(root, text="Show Result", command=display_result, font=("Arial", 12))
submit_button.pack(pady=20)

# Label to display the result
result_label = ctk.CTkLabel(root, text="", font=("Arial", 12), wraplength=500)
result_label.pack(pady=10)

# Run the application
root.mainloop()
