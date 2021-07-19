# Lesson X: Biometric Authentication in iOS with Swift

### Lesson Duration: 2 hours 40 minutes

> Purpose: The purpose of this lesson is to introduce Biometric Authentication concepts, requirements and final implementation in an iOS App.

---

### Setup

- Xcode, simulator or device with biometric input (Touch ID or Face ID)

### Learning Objectives

After this lesson, students will be able to:

- Correctly introduce biometric authentication in key places inside the app
- Know the difference between passcode verification and biometric authentication
- Authenticate the user's identity with biometric data

---

### Lesson 1 key concepts

> :clock10: 30 min

- Introduce the importance of user authentication
- UX concepts for biometric authentication
- Explain the device's requirements
- Show the different cases in which the authentication succeeds and fails


---

:coffee: **BREAK**

---

#### :pencil2: Check for Understanding - Class activity

> :clock10: 10 min (+ 10 min Review)

<details>
  <summary> Click for Instructions: Activity 1 </summary>

- List four cases in which an app would ask for biometric authentication.

</details>

<details>
  <summary> Click for Solution: Activity 1 solutions </summary>

- Online purchases
- Update credit card information
- Login attempts
- Change passwords

</details>

---

:coffee: **BREAK**

---

### Lesson 2 Check availability - Key concepts

> :clock10: 30 min

- Local Authentication framework
- Local Authentication Context
- NSError
- Policy evaluation

<details>
  <summary> Click for Code Sample </summary>

```swift
func isBiometricActive() -> Bool {
    let localAuthenticationContext = LAContext()
    var authorizationError: NSError?
    if localAuthenticationContext.canEvaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, error: &authorizationError) {
        return true
    } else {
        return false
    } 
}
```

</details>

---

#### :pencil2: Check for Understanding - Class activity/quick quiz

> :clock10: 30 min (+ 10 min Review)

<details>
  <summary> Click for Instructions: Activity 2 </summary>

- Link to [activity 2](). Insert BioAuth inside a pre-made login app

</details>

<details>
  <summary> Click for Solution: Activity 2 solutions </summary>

- Link to [activity 2 solutions]().

</details>

---

:coffee: **BREAK**

---

### Lesson 3 Prompt the user - key concepts

> :clock10: 30 min

- Local Authentication Biometry Type
- Revisit Policy Evaluation
- Clousures
- Async instructions

<details>
  <summary> Click for Code Sample</summary>

```swift
func authUser() {
     if isBiometricActive() {
           let localAuthenticationContext = LAContext()
           let reason = localAuthenticationContext.biometryType == LABiometryType.touchId ? “Place your fingerprint” : “Scan your face”
           localAuthenticationContext.evaluatePolicy(.deviceOwnerAuthenticationWithBiometrics, localizedReason: reason) { success, evaluateError in
                if success {
                    // do something asynchronously
                } else {
                    // do something with evaluateError
                } 
            }
    } else {
        // handle non biometric authentication
    } 
}
```

</details>

---

### :pencil2: Check for Understanding - Class activity

> :clock10: 30 min

<details>
  <summary> Click for Instructions: Activity 3 </summary>

- Insert sample code in previous activity.

</details>

<details>
  <summary>Click for Solution: Activity 3 solutions</summary>

- Link to [activity 3 solution]().

</details>

---