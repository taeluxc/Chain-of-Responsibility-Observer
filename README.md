# Chain-of-Responsibility-Observer
# Emergency Alert System Using Observer Pattern

## 1. Problem Analysis & Trade-off Report

# Real-World Software Problem

Emergency response systems require fast and reliable communication between multiple departments such as hospitals, police stations, and fire departments.

In traditional systems, the emergency center manually sends notifications to each department separately. This creates several issues:

* High coupling between components
* Difficult maintenance
* Delayed notifications
* Poor scalability when adding new departments
* Repetitive code

The system needs a flexible mechanism where all related departments automatically receive updates whenever an emergency alert is triggered.

---

# Main Design Challenges

## 1. Loose Coupling

The emergency center should not depend directly on every department class.

## 2. Scalability

The system should allow adding new departments without modifying existing code.

## 3. Automatic Notification

All departments must receive updates immediately when an alert occurs.

## 4. Maintainability

The design should be easy to maintain and extend.

---

# Possible Design Patterns

## Option 1: Observer Pattern

### Description

The Observer pattern creates a one-to-many relationship between objects. When the subject changes its state, all observers are notified automatically.

### Application in the System

* EmergencyAlertSystem = Subject
* PoliceDepartment, HospitalDepartment, FireDepartment = Observers

When an emergency alert is triggered, all departments automatically receive the notification.

### Advantages

* Loose coupling
* Easy to add new observers
* Automatic event notification
* High flexibility
* Follows Open/Closed Principle

### Disadvantages

* Can become difficult to debug in very large systems
* Many observers may affect performance

---

## Option 2: Chain of Responsibility Pattern

### Description

The request passes through a chain of handlers until one handler processes it.

### Application in the System

The alert could move from Police → Hospital → Fire Department until one department handles it.

### Advantages

* Flexible request handling
* Reduces direct sender-receiver dependency

### Disadvantages

* Only one handler usually processes the request
* Not suitable when all departments must receive the same alert
* More complex for this scenario

---

# Trade-Off Analysis

| Criteria                   | Observer Pattern | Chain of Responsibility |
| -------------------------- | ---------------- | ----------------------- |
| Multiple receivers         | Excellent        | Weak                    |
| Automatic updates          | Excellent        | Limited                 |
| Scalability                | High             | Medium                  |
| Complexity                 | Simple           | Moderate                |
| Suitable for notifications | Excellent        | Poor                    |
| Loose coupling             | Strong           | Moderate                |

---

# Selected Pattern Justification

The Observer pattern was selected because the emergency alert system requires multiple departments to receive the same notification simultaneously.

Unlike Chain of Responsibility, where the request moves between handlers, the Observer pattern broadcasts updates to all subscribed departments instantly.

This design improves:

* Flexibility
* Scalability
* Maintainability
* Reusability

It also follows important object-oriented design principles such as:

* Open/Closed Principle
* Dependency Inversion Principle
* Separation of Concerns

Therefore, Observer Pattern is the most suitable solution for the problem.

---

# 2. Design Pattern Justification Document

# Selected Design Pattern

## Observer Pattern

---

# Why Observer Pattern Fits the Problem

The system requires multiple departments to react automatically whenever an emergency alert occurs.

The Observer pattern perfectly supports this behavior because:

* One subject can notify many observers
* Observers can subscribe or unsubscribe dynamically
* New departments can be added without changing the core system
* The subject does not need detailed knowledge about observers

This reduces coupling between system components.

---

# Design Principles Applied

## 1. Open/Closed Principle

The system is open for extension because new departments can be added without modifying existing code.

## 2. Dependency Inversion Principle

The subject depends on abstract observer interfaces instead of concrete classes.

## 3. Separation of Concerns

Each department handles its own response independently.

---

# Example Scenario

When the user presses the “Send Emergency Alert” button:

1. The EmergencyAlertSystem triggers an alert.
2. All registered observers are notified.
3. PoliceDepartment receives the alert.
4. HospitalDepartment receives the alert.
5. FireDepartment receives the alert.

This demonstrates automatic event distribution using Observer Pattern.


# Pattern Application Explanation

## Subject

The EmergencyAlertSystem acts as the main subject.

Responsibilities:

* Store observers
* Register departments
* Notify observers when alerts occur

---

## Observer Interface

Defines the update() method used by all departments.

---

## Concrete Observers

Each department implements the Observer interface.

Examples:

* PoliceDepartment
* HospitalDepartment
* FireDepartment

Each observer responds differently to emergency alerts.

---

## Main Buttons

* Send Alert
* Cancel Alert
* Add Emergency
* Update Status

---

# Expected System Output

When the Send Alert button is clicked:

```text
Emergency Alert Triggered!
Police Department received the alert.
Hospital Department received the alert.
Fire Department received the alert.
```

---

# Conclusion

The Observer Pattern provides a clean and scalable solution for emergency notification systems.

It allows multiple departments to receive real-time updates automatically while keeping the system flexible and maintainable.

The design minimizes coupling and follows modern software engineering principles, making it highly suitable for real-world event-driven systems.
