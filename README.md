
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

           API Security
   1. Authentication
What it is: Verifying the identity of users through secure login/signup (e.g., password hashing, session or token-based authentication).
Why it's important: Ensures only legitimate users access their accounts, protecting sensitive user data such as contact info, booking history, and payment details.

2. Authorization
What it is: Controlling access to resources and actions based on user roles (e.g., guest vs. host vs. admin).
Why it's important: Prevents unauthorized access to critical features—e.g., a guest editing someone else's property, or a user accessing admin-only pages.

3. Rate Limiting
What it is: Limiting the number of requests a user or IP address can make in a given timeframe.
Why it's important: Protects against brute-force attacks on login pages and helps mitigate spam or DDoS-style abuse of public endpoints.

4. Input Validation and Sanitization
What it is: Ensuring all user input is validated and sanitized before being processed or stored.
Why it's important: Prevents common web vulnerabilities such as SQL injection and XSS (cross-site scripting), which could compromise data integrity or expose user sessions.

5. Secure Payment Handling
What it is: Using HTTPS, secure payment gateways (e.g., Stripe), and never storing raw credit card data.
Why it's important: Ensures financial transactions are encrypted and trusted, reducing the risk of fraud and complying with data protection regulations (e.g., PCI-DSS).

6. Data Protection and Encryption
What it is: Encrypting sensitive data at rest and in transit (e.g., passwords, personal info).
Why it's important: Safeguards user privacy and prevents data breaches that could harm users and damage platform credibility.

7. CSRF and XSS Protection
What it is: Django's built-in CSRF tokens and template auto-escaping to prevent cross-site request forgery and scripting attacks.
Why it's important: Ensures user sessions and browser-based actions are secure and cannot be hijacked or spoofed.











