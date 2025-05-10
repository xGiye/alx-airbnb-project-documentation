## 👥 Use cases

The Airbnb Clone backend supports the following use cases. Each case is assigned specific permissions and responsibilities to ensure a smooth interaction with the system's features and functionalities.

---

![Use case Diagram](./Airbnb%20Clone%20-%20Use-case%20.png)

_Airbnb Use case diagram_

---

### 1. 🧍 Guest (User/Customer)

A Guest is a regular user who visits the platform to search for and book properties.

- 🔐 Register and log in securely
- 🔍 Search and view property listings
- 🛏️ Book properties and make payments
- ✍️ Leave reviews after stays

### 2. 🏠 Host

A Host is a user who lists and manages rental properties on the platform. Users can be both Guests and Hosts, depending on their activities.

- 🔐 Register and log in securely
- 🏘️ Create, update, and delete property listings
- 📅 View and manage bookings
- 📨 Communicate with guests

### 3. 🛡️ Admin

Admins are internal system users responsible for managing the platform and ensuring it operates securely and efficiently.

- 👤 Manage Guest and Host accounts
- 🏠 Approve or monitor property listings
- 💳 Monitor bookings and payments
- 🚫 Enforce rules, block listings or users if necessary

> 💡 **Note**: Role-based access control (RBAC) is implemented to ensure that each user type only accesses features relevant to their role.
