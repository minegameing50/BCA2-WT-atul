# Day 39 — Advanced Form Validation with JavaScript

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 7 — Web Forms & Database
🧪 **Lab Experiment:** 22 (Part 2), 24

---

## Learning Objectives

By the end of this session, students will be able to:
- Implement client-side form validation using JavaScript
- Use regular expressions for pattern matching
- Validate forms in real-time (on input/blur)
- Display custom error messages dynamically

---

## 1. Validation Strategy

> **Analogy:** Client-side validation is like a **security guard at the gate** — catches obvious problems before they reach the manager (server). But the manager (server) still checks again because the guard can be bypassed.

### Validation Layers

| Layer | Technology | Purpose |
|-------|-----------|---------|
| HTML5 | `required`, `pattern`, `min/max` | Basic browser validation |
| JavaScript | Custom logic, regex | Enhanced client-side |
| Server | PHP, Node.js, etc. | Final authority (never trust client) |

---

## 2. Common Regex Patterns

```javascript
// Email: basic pattern
const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;

// Phone: 10 digits (Indian)
const phoneRegex = /^[6-9]\d{9}$/;

// Password: min 8 chars, 1 uppercase, 1 lowercase, 1 digit
const pwdRegex = /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$/;

// PIN Code (Indian)
const pinRegex = /^\d{6}$/;

// Name: only letters and spaces
const nameRegex = /^[a-zA-Z\s]{2,50}$/;

// Roll Number: e.g., 25BCA060
const rollRegex = /^\d{2}BCA\d{3}$/i;
```

---

## 3. Real-Time Validation

```javascript
function showError(input, message) {
    const feedback = input.nextElementSibling;
    input.classList.add('is-invalid');
    input.classList.remove('is-valid');
    if (feedback) feedback.textContent = message;
}

function showSuccess(input) {
    input.classList.add('is-valid');
    input.classList.remove('is-invalid');
}

// Validate on blur (when user leaves field)
document.getElementById('email').addEventListener('blur', function() {
    const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
    if (!emailRegex.test(this.value)) {
        showError(this, 'Please enter a valid email');
    } else {
        showSuccess(this);
    }
});

// Validate on input (real-time as user types)
document.getElementById('phone').addEventListener('input', function() {
    const phoneRegex = /^[6-9]\d{9}$/;
    if (this.value.length === 10 && phoneRegex.test(this.value)) {
        showSuccess(this);
    } else if (this.value.length >= 10) {
        showError(this, 'Enter valid 10-digit number starting with 6-9');
    }
});
```

---

## 4. Password Strength Meter

```javascript
function checkPasswordStrength(password) {
    let strength = 0;
    if (password.length >= 8) strength++;
    if (/[A-Z]/.test(password)) strength++;
    if (/[a-z]/.test(password)) strength++;
    if (/\d/.test(password)) strength++;
    if (/[!@#$%^&*(),.?":{}|<>]/.test(password)) strength++;
    return strength; // 0-5
}

document.getElementById('password').addEventListener('input', function() {
    const strength = checkPasswordStrength(this.value);
    const bar = document.getElementById('strengthBar');
    const labels = ['', 'Very Weak', 'Weak', 'Fair', 'Strong', 'Very Strong'];
    const colors = ['', 'bg-danger', 'bg-warning', 'bg-info', 'bg-primary', 'bg-success'];
    bar.style.width = (strength * 20) + '%';
    bar.className = 'progress-bar ' + colors[strength];
    bar.textContent = labels[strength];
});
```

---

## 5. Confirm Password Match

```javascript
document.getElementById('confirmPwd').addEventListener('input', function() {
    const pwd = document.getElementById('password').value;
    if (this.value !== pwd) {
        showError(this, 'Passwords do not match');
    } else if (this.value.length > 0) {
        showSuccess(this);
    }
});
```

---

## Practical Session

### 🧪 Lab Experiments 22 (Part 2) & 24: Advanced Validated Registration Form

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Form Validation</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body class="bg-light">

    <div class="container my-5">
        <div class="row justify-content-center">
            <div class="col-lg-7">
                <div class="card shadow">
                    <div class="card-header bg-primary text-white text-center">
                        <h3 class="mb-0">Student Registration</h3>
                        <small>With Real-Time JavaScript Validation</small>
                    </div>
                    <div class="card-body p-4">
                        <form id="regForm" novalidate>

                            <!-- Name -->
                            <div class="mb-3">
                                <label for="name" class="form-label">Full Name</label>
                                <input type="text" class="form-control" id="name" placeholder="Enter full name">
                                <div class="invalid-feedback">Name must be 2-50 letters only</div>
                                <div class="valid-feedback">Looks good!</div>
                            </div>

                            <!-- Roll Number -->
                            <div class="mb-3">
                                <label for="roll" class="form-label">Roll Number</label>
                                <input type="text" class="form-control" id="roll" placeholder="e.g., 25BCA060">
                                <div class="invalid-feedback">Format: 25BCA060</div>
                                <div class="valid-feedback">Valid roll number</div>
                            </div>

                            <!-- Email -->
                            <div class="mb-3">
                                <label for="email" class="form-label">Email</label>
                                <input type="email" class="form-control" id="email" placeholder="name@example.com">
                                <div class="invalid-feedback">Enter a valid email address</div>
                                <div class="valid-feedback">Valid email</div>
                            </div>

                            <!-- Phone -->
                            <div class="mb-3">
                                <label for="phone" class="form-label">Phone Number</label>
                                <input type="tel" class="form-control" id="phone" placeholder="10-digit number">
                                <div class="invalid-feedback">Enter valid 10-digit number (starts with 6-9)</div>
                                <div class="valid-feedback">Valid phone number</div>
                            </div>

                            <!-- Password -->
                            <div class="mb-3">
                                <label for="password" class="form-label">Password</label>
                                <input type="password" class="form-control" id="password" placeholder="Min 8 characters">
                                <div class="progress mt-2" style="height: 6px;">
                                    <div class="progress-bar" id="strengthBar" role="progressbar" style="width: 0%"></div>
                                </div>
                                <small id="pwdHint" class="text-muted">Use uppercase, lowercase, numbers & symbols</small>
                                <div class="invalid-feedback">Min 8 chars, 1 uppercase, 1 lowercase, 1 digit</div>
                            </div>

                            <!-- Confirm Password -->
                            <div class="mb-3">
                                <label for="confirmPwd" class="form-label">Confirm Password</label>
                                <input type="password" class="form-control" id="confirmPwd" placeholder="Re-enter password">
                                <div class="invalid-feedback">Passwords do not match</div>
                                <div class="valid-feedback">Passwords match</div>
                            </div>

                            <!-- DOB -->
                            <div class="mb-3">
                                <label for="dob" class="form-label">Date of Birth</label>
                                <input type="date" class="form-control" id="dob">
                                <div class="invalid-feedback">Must be 16-30 years old</div>
                                <div class="valid-feedback">Valid age</div>
                            </div>

                            <!-- Course -->
                            <div class="mb-3">
                                <label for="course" class="form-label">Course</label>
                                <select class="form-select" id="course">
                                    <option value="">Select course...</option>
                                    <option>BCA</option>
                                    <option>BBA</option>
                                    <option>B.Tech CSE</option>
                                </select>
                                <div class="invalid-feedback">Please select a course</div>
                            </div>

                            <!-- Terms -->
                            <div class="form-check mb-3">
                                <input class="form-check-input" type="checkbox" id="terms">
                                <label class="form-check-label" for="terms">
                                    I agree to the terms and conditions
                                </label>
                                <div class="invalid-feedback">You must agree</div>
                            </div>

                            <!-- Error Summary -->
                            <div class="alert alert-danger d-none" id="errorSummary">
                                <strong>Please fix the following errors:</strong>
                                <ul id="errorList" class="mb-0"></ul>
                            </div>

                            <!-- Success -->
                            <div class="alert alert-success d-none" id="successMsg">
                                ✅ Registration successful!
                            </div>

                            <button type="submit" class="btn btn-primary w-100 btn-lg">Register</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <script>
    (function() {
        'use strict';

        // Regex patterns
        const patterns = {
            name:  /^[a-zA-Z\s]{2,50}$/,
            roll:  /^\d{2}BCA\d{3}$/i,
            email: /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/,
            phone: /^[6-9]\d{9}$/,
            pwd:   /^(?=.*[a-z])(?=.*[A-Z])(?=.*\d).{8,}$/
        };

        // Helper functions
        function showError(el, msg) {
            el.classList.add('is-invalid');
            el.classList.remove('is-valid');
            const fb = el.parentElement.querySelector('.invalid-feedback');
            if (fb && msg) fb.textContent = msg;
        }

        function showValid(el) {
            el.classList.add('is-valid');
            el.classList.remove('is-invalid');
        }

        function validate(el, regex) {
            if (regex.test(el.value.trim())) {
                showValid(el);
                return true;
            } else {
                showError(el);
                return false;
            }
        }

        // Real-time validation on blur
        const fields = [
            { id: 'name',  regex: patterns.name },
            { id: 'roll',  regex: patterns.roll },
            { id: 'email', regex: patterns.email },
            { id: 'phone', regex: patterns.phone },
            { id: 'password', regex: patterns.pwd }
        ];

        fields.forEach(function(f) {
            document.getElementById(f.id).addEventListener('blur', function() {
                if (this.value.trim() !== '') validate(this, f.regex);
            });
        });

        // Password strength meter
        document.getElementById('password').addEventListener('input', function() {
            let strength = 0;
            const val = this.value;
            if (val.length >= 8) strength++;
            if (/[A-Z]/.test(val)) strength++;
            if (/[a-z]/.test(val)) strength++;
            if (/\d/.test(val)) strength++;
            if (/[^a-zA-Z0-9]/.test(val)) strength++;

            const bar = document.getElementById('strengthBar');
            const labels = ['', 'Very Weak', 'Weak', 'Fair', 'Strong', 'Very Strong'];
            const colors = ['', 'bg-danger', 'bg-warning', 'bg-info', 'bg-primary', 'bg-success'];
            bar.style.width = (strength * 20) + '%';
            bar.className = 'progress-bar ' + colors[strength];
            bar.textContent = labels[strength];
        });

        // Confirm password match
        document.getElementById('confirmPwd').addEventListener('input', function() {
            const pwd = document.getElementById('password').value;
            if (this.value === pwd && this.value.length > 0) {
                showValid(this);
            } else {
                showError(this, 'Passwords do not match');
            }
        });

        // DOB validation: 16-30 years old
        document.getElementById('dob').addEventListener('change', function() {
            const dob = new Date(this.value);
            const today = new Date();
            let age = today.getFullYear() - dob.getFullYear();
            const monthDiff = today.getMonth() - dob.getMonth();
            if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < dob.getDate())) {
                age--;
            }
            if (age >= 16 && age <= 30) {
                showValid(this);
            } else {
                showError(this, 'Must be 16-30 years old');
            }
        });

        // Course selection
        document.getElementById('course').addEventListener('change', function() {
            if (this.value !== '') {
                showValid(this);
            } else {
                showError(this, 'Please select a course');
            }
        });

        // Form submit
        document.getElementById('regForm').addEventListener('submit', function(e) {
            e.preventDefault();
            const errors = [];

            // Validate all fields
            if (!validate(document.getElementById('name'), patterns.name)) 
                errors.push('Name must be 2-50 letters');
            if (!validate(document.getElementById('roll'), patterns.roll)) 
                errors.push('Roll number format: 25BCA060');
            if (!validate(document.getElementById('email'), patterns.email)) 
                errors.push('Enter a valid email');
            if (!validate(document.getElementById('phone'), patterns.phone)) 
                errors.push('Enter valid 10-digit phone');
            if (!validate(document.getElementById('password'), patterns.pwd)) 
                errors.push('Password needs 8+ chars, uppercase, lowercase, digit');

            const pwd = document.getElementById('password').value;
            const confirmPwd = document.getElementById('confirmPwd');
            if (confirmPwd.value !== pwd || confirmPwd.value === '') {
                showError(confirmPwd, 'Passwords do not match');
                errors.push('Passwords must match');
            }

            const dob = document.getElementById('dob');
            if (!dob.value) {
                showError(dob, 'Date of birth is required');
                errors.push('Date of birth is required');
            }

            const course = document.getElementById('course');
            if (course.value === '') {
                showError(course, 'Please select a course');
                errors.push('Select a course');
            }

            const terms = document.getElementById('terms');
            if (!terms.checked) {
                showError(terms, 'You must agree');
                errors.push('Accept terms and conditions');
            } else {
                showValid(terms);
            }

            // Show results
            const errorSummary = document.getElementById('errorSummary');
            const errorList = document.getElementById('errorList');
            const successMsg = document.getElementById('successMsg');

            if (errors.length > 0) {
                errorList.innerHTML = errors.map(function(e) { return '<li>' + e + '</li>'; }).join('');
                errorSummary.classList.remove('d-none');
                successMsg.classList.add('d-none');
            } else {
                errorSummary.classList.add('d-none');
                successMsg.classList.remove('d-none');
                this.reset();
                // Clear validation classes
                this.querySelectorAll('.is-valid, .is-invalid').forEach(function(el) {
                    el.classList.remove('is-valid', 'is-invalid');
                });
                document.getElementById('strengthBar').style.width = '0%';
            }
        });
    })();
    </script>

</body>
</html>
```

---

## Summary

| Concept | Technique |
|---------|-----------|
| Regex validation | `regex.test(value)` |
| Real-time | `blur` and `input` events |
| Password strength | Count criteria met (0-5) |
| Error display | `classList.add('is-invalid')` |
| Success display | `classList.add('is-valid')` |
| Error summary | Collect all errors, display in list |

---

*Day 39 of 55 | Unit 7 — Web Forms & Database | Web Technology (25BCA060)*
