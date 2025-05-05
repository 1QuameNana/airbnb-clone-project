
# airbnb-clone-project
This project features the development of an airbnb platform for easy management of rental propetiesus
Implimentation of MOdels and Api for easy access and security with Django, restAPI, mySQL for the modelling.

                     Team Roles
                     
             Project manager (PM)
Makes sure a product or its part is delivered on time and within budget
Manages and motivates the software development team 

           UI/UX designer
Transforms a product vision into user-friendly designs
Creates user journeys for the best user experience and highest conversion rates

          Software architect
Designs a high-level software architecture
Selects appropriate tools and platforms to implement the product vision
Sets up code quality standards and performs code reviews

            Software developer
Engineers and stabilizes the product
Solves any technical problems emerging during the development lifecycle

              Database Design
  The Database design takes into account the Costumer , Properties, Bookings, Reviews, and Payments.
  
              1. User
(Assume extending Django's default AbstractUser or using User model)
Fields:
username (inherited)
email
is_host (BooleanField: to distinguish between guests and hosts)
first_name
last_name

Relationships:
A User can own multiple Properties (if is_host is True).
A User can make multiple Bookings.
A User can leave multiple Reviews.

2. Review
Fields:
user (ForeignKey to User)
property (ForeignKey to Property)
rating (IntegerField: e.g., 1–5)
comment (TextField)
created_at (DateTimeField)

Relationships:
A Review is made by a User for a specific Property.
A Property can have many Reviews.

3. Booking
Fields:
user (ForeignKey to User)
property (ForeignKey to Property)
check_in (DateField)
check_out (DateField)
status (e.g., pending, confirmed, cancelled)

Relationships:
A Booking is made by a User for a Property.
A Property can have many Bookings.
A User can have many Bookings.

       Payment
Fields:
booking (OneToOneField to Booking)
amount (DecimalField)
payment_date (DateTimeField)
status (e.g., success, failed, pending)
payment_method (CharField or ChoiceField)

Relationships:
A Payment is linked to exactly one Booking.
A Booking must have one Payment (depending on your app's flow).

Entity Relationship Summary:
User ⟶ can be a guest or host.
User ⟶ has many Bookings, many Reviews.
Property ⟶ belongs to a User (host), has many Bookings, has many Reviews.
Booking ⟶ made by a User, for a Property, has one Payment.
Payment ⟶ for one Booking.

      Feature Breakdown

1. User Management
Allows users to register, log in, and manage their profiles. Hosts and guests can be differentiated, with hosts able to list properties and guests able to book them. This system ensures secure access and personalized experiences.

2. Property Management
Hosts can create, update, and manage property listings with details like location, description, price, and images. This is central to the platform, as it enables hosts to offer accommodations and display them to potential guests.

3. Booking System
Guests can search for available properties, select check-in/check-out dates, and make reservations. The system prevents double-bookings and manages reservation statuses (pending, confirmed, cancelled), facilitating a smooth booking experience.

4. Payment Integration
Processes payments securely for confirmed bookings, often using third-party gateways (e.g., Stripe or PayPal). It ensures transactions are completed before a booking is finalized, providing financial security for both hosts and guests.

5. Review & Rating System
Allows guests to leave feedback on their stay, rating the property and host. This builds trust in the platform, helps maintain quality standards, and guides future guests in making informed booking decisions.









