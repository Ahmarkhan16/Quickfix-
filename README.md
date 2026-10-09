# Quickfix-
import customtkinter as ctk

class QuickFixApp(ctk.CTk):

    def __init__(self):
        super().__init__()

        self.title("QuickFix")
        self.geometry("900x600")
        self.minsize(800, 500)

        ctk.set_appearance_mode("dark")
        ctk.set_default_color_theme("blue")

        self.show_home()

    # ---------------- HOME ----------------

    def clear_screen(self):
        for widget in self.winfo_children():
            widget.destroy()

    def show_home(self):
        self.clear_screen()

        # Create a centered container for a cleaner layout
        center_frame = ctk.CTkFrame(self, fg_color="transparent")
        center_frame.pack(expand=True)

        title = ctk.CTkLabel(
            center_frame,
            text="QuickFix",
            font=("Helvetica", 48, "bold"),
            text_color="#FC8019"
        )
        title.pack(pady=(0, 5))

        subtitle = ctk.CTkLabel(
            center_frame,
            text="On-Demand Skilled Service Booking",
            font=("Helvetica", 16),
            text_color="gray"
        )
        subtitle.pack(pady=(0, 40))

        # Primary Button
        customer_button = ctk.CTkButton(
            center_frame,
            text="I need a Service",
            font=("Helvetica", 16, "bold"),
            width=280,
            height=55,
            corner_radius=10,
            command=self.customer_page
        )
        customer_button.pack(pady=10)

        # Secondary Button (Outlined style)
        provider_button = ctk.CTkButton(
            center_frame,
            text="I am a Provider",
            font=("Helvetica", 16, "bold"),
            width=280,
            height=55,
            corner_radius=10,
            fg_color="transparent",
            border_width=2,
            border_color="#FC8019",
            text_color="#FC8019",
            command=self.provider_page
        )
        provider_button.pack(pady=10)

    # ---------------- CUSTOMER (SWIGGY STYLE) ----------------

    def customer_page(self):
        self.clear_screen()

        title = ctk.CTkLabel(
            self,
            text="QuickFix Services",
            font=("Arial", 36, "bold"),
            text_color="#FC8019"
        )
        title.pack(pady=(30, 5))

        subtitle = ctk.CTkLabel(
            self,
            text="Book skilled professionals instantly.",
            font=("Arial", 18)
        )
        subtitle.pack(pady=(0, 20))

        search_entry = ctk.CTkEntry(
            self,
            placeholder_text="Search for a service (e.g., Electrician, Mechanic)",
            width=500,
            height=40,
            font=("Arial", 14)
        )
        search_entry.pack(pady=(0, 40))

        container = ctk.CTkFrame(self, fg_color="transparent")
        container.pack(pady=10)

        home_card = ctk.CTkFrame(container, width=260, height=180, corner_radius=15)
        home_card.grid(row=0, column=0, padx=15, pady=10)
        home_card.pack_propagate(False)
        
        ctk.CTkLabel(home_card, text="🏠", font=("Arial", 40)).pack(pady=(20, 5))
        ctk.CTkLabel(home_card, text="HOME SERVICE", font=("Arial", 18, "bold")).pack()
        ctk.CTkLabel(home_card, text="Repairs & Maintenance", font=("Arial", 12), text_color="gray").pack(pady=(0, 15))
        ctk.CTkButton(home_card, text="Book Now", width=120, command=self.home_service).pack()

        road_card = ctk.CTkFrame(container, width=260, height=180, corner_radius=15)
        road_card.grid(row=0, column=1, padx=15, pady=10)
        road_card.pack_propagate(False)
        
        ctk.CTkLabel(road_card, text="🚗", font=("Arial", 40)).pack(pady=(20, 5))
        ctk.CTkLabel(road_card, text="ROADSIDE ASSIST", font=("Arial", 18, "bold")).pack()
        ctk.CTkLabel(road_card, text="Towing & Mechanics", font=("Arial", 12), text_color="gray").pack(pady=(0, 15))
        ctk.CTkButton(road_card, text="Book Now", width=120, command=self.road_service).pack()

        back_button = ctk.CTkButton(self, text="← Back", width=150, command=self.show_home)
        back_button.pack(pady=40)

    # ---------------- HOME SERVICE ----------------

    def home_service(self):
        self.clear_screen()

        title = ctk.CTkLabel(self, text="Home Services", font=("Arial", 32, "bold"))
        title.pack(pady=40)

        subtitle = ctk.CTkLabel(self, text="Select the service you need", font=("Arial", 18))
        subtitle.pack()

        ctk.CTkButton(self, text="⚡ Electrician", width=300, height=55).pack(pady=20)
        ctk.CTkButton(self, text="🔧 Appliance Repair", width=300, height=55).pack(pady=10)

        back_button = ctk.CTkButton(self, text="← Back", width=150, command=self.customer_page)
        back_button.pack(pady=30)

    # ---------------- ROAD SERVICE ----------------

    def road_service(self):
        self.clear_screen()

        title = ctk.CTkLabel(self, text="Roadside Services", font=("Arial", 32, "bold"))
        title.pack(pady=40)

        subtitle = ctk.CTkLabel(self, text="Select the service you need", font=("Arial", 18))
        subtitle.pack()

        ctk.CTkButton(self, text="🔧 Motor Mechanic", width=300, height=55).pack(pady=20)
        ctk.CTkButton(self, text="🚗 Vehicle Breakdown", width=300, height=55).pack(pady=10)

        back_button = ctk.CTkButton(self, text="← Back", width=150, command=self.customer_page)
        back_button.pack(pady=30)

    # ---------------- PROVIDER ----------------

    def provider_page(self):
        self.clear_screen()

        label = ctk.CTkLabel(self, text="Service Provider Dashboard", font=("Arial", 30, "bold"))
        label.pack(pady=50)

        status_label = ctk.CTkLabel(self, text="Active Jobs: 0", font=("Arial", 18))
        status_label.pack(pady=10)

        back_button = ctk.CTkButton(self, text="← Back", width=150, command=self.show_home)
        back_button.pack(pady=30)


if __name__ == "__main__":
    app = QuickFixApp()
    app.mainloop()
