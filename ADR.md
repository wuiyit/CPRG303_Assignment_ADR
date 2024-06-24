# Group 3 Assignment: Architectural Decisions
Project: Food Ordering Application

## Background 
Our mobile app development team is tasked with creating a new application for a client. 
This application will allow users to order food from local eateries, either for delivery or pick-up directly from the restaurant. 
Users will have the ability to set up personal accounts and store payment details for future transactions.

## Fundamental architectural decisions 
### Native, Web, or Hybrid App 
#### Context:
Choosing the correct architectural style for our food delivery app is crucial, as it impacts user experience, development efforts, and ongoing maintenance.
#### Options Considered:
1.	Native App: Develop distinct versions for iOS and Android using platform-specific technologies.
2.	Web App: Create a web-based application accessible by users via browsers on multiple devices.
3.	Hybrid App: Utilize a single codebase that can be deployed across multiple platforms using frameworks like React Native or Flutter.
#### Decision:
We decided to develop a native app for both iOS and Android. The factors influencing this decision include:
1.	Our target audience predominantly uses iOS and Android devices.
2.	Native apps offer optimal performance and user experience due to their tight integration with device features like GPS and push notifications.
3.	They offer better responsiveness, access to specific platform APIs, and enhanced security.

### UI Framework 
#### Context:
We need to select a UI framework that enables responsive design and provides an intuitive user interface. 
Framework provides us with a platform where we don't have to build everything from scratch. It saves time and also provides other features that can simplify the tasks.

#### Options Considered:
1.	React Native: Supports JavaScript and React, benefits from a large community, and allows integration with native code.
2.	Flutter: Known for UI consistency, performance, and providing a native-like experience using the Dart programming language.
#### Decision:
React Native has been chosen due to its extensive community support and compatibility with our team’s JavaScript expertise, facilitating efficient development.

### Backend language 
#### Context:
Choosing an appropriate backend language is vital for building the server-side features of our app, which should support scalability and performance.
#### Options Considered:
1.	Node.js: Known for its non-blocking I/O and JavaScript ecosystem.
2.	Python (Django): Suitable for handling complex data operations.
#### Decision:
Node.js is selected for its scalability and comprehensive libraries for building RESTful APIs.

### Permission 
#### Context:
It is essential for us to determine the permission model for the food delivery app. Permissions will govern access to sensitive user data, device features, and application functionality. 
#### Options Considered:
1.	Role-Based Access Control: Implement a role-based permission system, defining different user roles (e.g., customer, restaurant owner) and their associated permissions. 
2.	OAuth 2.0: Utilize OAuth 2.0 for granting and managing permissions, allowing for third-party integrations and secure access control. 
3.	Custom Permission System: Develop a custom permission management solution tailored to the specific needs of the app.
#### Decision:
Role-based access control has been adopted to clearly define permissions for different users, ensuring flexibility and ease of management.

### Data storage 
#### Context:
The food delivery app needs to manage user profiles, order data, location information, customer ratings and reviews of restaurants, and other critical data. Users should be able to view their order history and reorder their favourite items. Given the large volume of data and the need for efficient retrieval, it is important to select a data storage solution that ensures data safety.
#### Options Considered:
1.	Relational Database (e.g., PostgreSQL): Use a traditional relational database for structured data storage.
2.	NoSQL Database (e.g., MongoDB): Opt for a NoSQL database for flexibility and scalability, especially for semi-structured data.
3.	Cloud-Based Storage (e.g., Amazon S3): Utilize cloud-based storage services for handling images, media, and user-generated content.
#### Decision:
We choose using a relational database (PostgreSQL) for structured data storage due to its strong support for transactional data, data consistency, and complex queries. PostgreSQL offers robust features and has a solid track record for reliability.

## Related Architectural Decisions Related to User Requirements

### (1) & (2) Real-time Order Tracking and Location Tracking
#### Context: 
To provide accurate restaurant recommendations, estimate delivery times, and display nearby options, the app needs to implement real-time tracking and geolocation technologies. Additionally, the app should offer real-time order tracking to enhance the user experience, allowing users to monitor the status and progress of their orders.
#### Options Considered:
1. Google Map API: A comprehensive geospatial service known for its accuracy and developer-friendly tools. It accepts an HTTPS request with the cell tower and WiFi access points that a mobile client can detect
2. Mapbox API: Known for its mapping and location-based services, providing custom maps and navigation solutions.
#### Decision:
The team has decided to utilize the Google Map API for real-time tracking and geolocation. This choice is driven by Google Maps' extensive features, reliability, and developer-friendly interface, which are expected to contribute significantly to the operational effectiveness of our app. Also, the customization feature offered by Mapbox API is not the key feature for enhancing user experience 

### (3) Payment Handling
#### Context:
Secure and seamless transactions are critical for the food delivery app. To meet this requirement, the app must integrate multiple payment gateways.
#### Options Considered:
1.	Stripe: A developer-focused payment gateway known for its simplicity and flexibility. It enables businesses to easily accept online payments and offers a wide range of customization options and support for various payment methods.
2.	Paypal: Paypal offers a scalable and customizable payment processing solution. It supports both mobile and web payments, making it suitable for in-app transactions and ensuring a seamless user experience.
#### Decision:
The team has chosen Stripe as the payment gateway due to its strong security features, ease of integration, and its reputation for developer-friendly operations. Stripe’s robust APIs and customization options make it ideal for ensuring a smooth payment experience for users. In addition, Stripe is cheaper than PayPal if the payments do not require currency conversion.

### (4) Inventory Management System
#### Context:
To ensure accurate and up-to-date restaurant menus, the app should integrate with the restaurants' inventory management systems. The team needs to determine the most efficient and reliable method of synchronizing menu data, such as through APIs or web scraping techniques.
#### Options Considered:
1.	RESTful API Integration: Establish direct RESTful API connections with restaurant inventory management systems using technologies like Node.js and Express.js to retrieve and synchronize menu data. 
2.	GraphQL Integration: Implement GraphQL-based data queries to seamlessly fetch and synchronize menu data from restaurant systems 
3.	Web Scraping with Puppeteer: Utilize Puppeteer, a headless browser automation tool, to perform web scraping techniques on restaurant websites and synchronize the extracted menu data with the app's database
#### Decision:
GraphQL Integration has been selected for synchronizing menu data from the restaurant. This method offers enhanced data retrieval efficiency by reducing unnecessary data transfer and improving synchronization speeds. It allows clients to request only the data they need, which is particularly beneficial for dynamic and varied restaurant menu data.

### (5) Review and Ratings
#### Context:
To help users make informed decisions, the app should include a feature for users to leave reviews and ratings for restaurants and food items. The user-generated content related to reviews and ratings will be collected, displayed and moderated.
#### Options Considered:
1.	Built-in Rating System: Develop an in-house system for collecting and displaying ratings and reviews. This system would allow for customized features specific to the app's needs, such as filtering reviews, responding to feedback, and more detailed ratings (e.g., rating by food quality, service, cleanliness).
2.	Trustpilot: It is a consumer review website that enables customers to provide feedback on their shopping experiences and service encounters with various businesses, thus promoting transparency and trust in business-consumer relationships.
#### Decision: 
A Built-in Rating System will be developed for the app. This decision allows for greater customization and integration with the app’s other features, such as user profiles and order history. It also avoids reliance on external services, which can be critical for maintaining user data privacy and tailoring user experience specifically to the food delivery context.

### (6) User Profile
#### Context:
The app will provide users with access to their order history, allowing them to easily reorder their favourite items.
#### Options Considered:
1.	Local Storage on Device: Use device storage to keep essential user data, which ensures quick access and offline availability. This approach is limited by the data security concerns and the inability to synchronize across devices.
2.	Cloud-Based User Profiles: Store user data on a cloud server, enabling synchronization across multiple devices and ensuring data is backed up. This method uses services like Amazon Web Services (AWS) or Google Firebase for data management.
#### Decision: 
The Cloud-Based User Profiles approach will be implemented. This method offers the best balance between accessibility, security, and user convenience. By storing user data in the cloud, the app can provide a seamless experience across different devices and ensure that user data is always accessible and secure. Utilizing cloud services also facilitates scalability as the app's user base grows.

### (7) Notification
#### Context:
To keep users informed about order confirmations, delivery updates, and promotional offers, the app should include a notification system
#### Options Considered:
1.	Firebase Cloud Messaging: Google-based messaging service  
2.	OneSignal: A third-party push notification service known for its ease of use and integrations with other platforms
#### Decision: 
The team has decided to use OneSignal to implement push notifications. This selection is based on OneSignal's reputation as a user-friendly and feature-rich push notification service that is simple to integrate with a variety of platforms.

## STATUS
Pending - Jun 20th
Approved - Jun 21st


## CONSEQUENCES
This Architectural Decision Record (ADR) details the strategic choices made for the development of a food ordering application, focusing on essential aspects like application architecture, UI framework, backend language, permissions, and data storage. 
By opting for native app development, utilizing React Native, and leveraging Node.js for the backend, we  laid a foundation for a robust, responsive, and user-friendly application. 
The adoption of PostgreSQL for data storage, role-based access control for permissions, and the decision to implement specific APIs and frameworks ensures scalability, security, and high performance.

The inclusion of detailed user reviews and ratings through a custom-built system and the management of user profiles via cloud-based storage will enhance user engagement and trust. 
The choices made in this ADR are aligned with the project's goals to deliver a seamless user experience, maintain data integrity, and ensure the application's long-term viability in a competitive market. 
These decisions will drive the development process, aiming to achieve a successful launch and favorable reception of the food ordering app in its target market.
