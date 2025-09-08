<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Patient Registration</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap');
        body {
            font-family: 'Inter', sans-serif;
        }
        .message-box {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 1rem;
            border-radius: 0.5rem;
            color: white;
            z-index: 100;
            display: none;
            opacity: 0;
            transition: opacity 0.5s ease-in-out;
        }
        .message-box.show {
            display: block;
            opacity: 1;
        }
        .message-success {
            background-color: #22c55e; /* green-500 */
        }
        .message-error {
            background-color: #ef4444; /* red-500 */
        }
        input[type="radio"] {
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            display: inline-block;
            width: 1rem;
            height: 1rem;
            border: 2px solid #6b7280; /* gray-500 */
            border-radius: 50%;
            margin-right: 0.5rem;
            position: relative;
            cursor: pointer;
        }
        input[type="radio"]:checked {
            border: 5px solid #4f46e5; /* indigo-600 */
        }
        input[type="radio"]:focus {
            outline: none;
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.5);
        }
        input[type="checkbox"] {
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            width: 1rem;
            height: 1rem;
            border: 2px solid #6b7280; /* gray-500 */
            border-radius: 0.25rem;
            position: relative;
            cursor: pointer;
        }
        input[type="checkbox"]:checked {
            background-color: #4f46e5; /* indigo-600 */
            border-color: #4f46e5;
        }
        input[type="checkbox"]:checked::after {
            content: '✔';
            color: white;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 0.75rem;
        }
        .required::after {
            content: ' *';
            color: red;
        }
    </style>
</head>
<body class="bg-gray-100 flex items-center justify-center min-h-screen p-4">
    <div class="bg-white p-8 rounded-xl shadow-lg w-full max-w-2xl">
        <h1 class="text-3xl font-bold text-center mb-6 text-gray-800">Patient Registration</h1>

        <div id="registration-section-1">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label class="block text-gray-700 text-sm font-semibold mb-2">Registration Date</label>
                    <input type="text" id="registration-date" class="w-full px-4 py-2 border border-gray-300 rounded-lg bg-gray-200" disabled>
                </div>
                <div>
                    <label class="block text-gray-700 text-sm font-semibold mb-2">Time</label>
                    <input type="text" id="registration-time" class="w-full px-4 py-2 border border-gray-300 rounded-lg bg-gray-200" disabled>
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="aadhar-number" class="block text-gray-700 text-sm font-semibold mb-2">Aadhaar Number</label>
                    <input type="text" id="aadhar-number" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Aadhaar Number" maxlength="12">
                </div>
                <div>
                    <label class="block text-gray-700 text-sm font-semibold mb-2">DOB</label>
                    <div class="grid grid-cols-3 gap-2">
                        <input type="text" id="dob-dd" placeholder="DD" class="px-4 py-2 border border-gray-300 rounded-lg" maxlength="2">
                        <input type="text" id="dob-mm" placeholder="MM" class="px-4 py-2 border border-gray-300 rounded-lg" maxlength="2">
                        <input type="text" id="dob-yy" placeholder="YY" class="px-4 py-2 border border-gray-300 rounded-lg" maxlength="4">
                    </div>
                </div>
            </div>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-semibold mb-2">Gender</label>
                <div class="flex items-center gap-4">
                    <label class="inline-flex items-center">
                        <input type="radio" name="gender" value="Male" class="form-radio">
                        <span class="ml-2 text-gray-700">Male</span>
                    </label>
                    <label class="inline-flex items-center">
                        <input type="radio" name="gender" value="Female" class="form-radio">
                        <span class="ml-2 text-gray-700">Female</span>
                    </label>
                    <label class="inline-flex items-center">
                        <input type="checkbox" name="gender-transgender" value="Transgender" class="form-checkbox">
                        <span class="ml-2 text-gray-700">Transgender</span>
                    </label>
                </div>
            </div>
            <div class="mb-4">
                <label for="title" class="block text-gray-700 text-sm font-semibold mb-2">Title</label>
                <select id="title" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                    <option value="">-- Select Title --</option>
                    <option value="Mr.">Mr.</option>
                    <option value="Mrs.">Mrs.</option>
                    <option value="Ms.">Ms.</option>
                </select>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="first-name" class="block text-gray-700 text-sm font-semibold mb-2">First Name</label>
                    <input type="text" id="first-name" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="First Name">
                </div>
                <div>
                    <label for="last-name" class="block text-gray-700 text-sm font-semibold mb-2">Last Name</label>
                    <input type="text" id="last-name" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Last Name">
                </div>
            </div>
            <div class="mb-4">
                <label class="block text-gray-700 text-sm font-semibold mb-2">Father/Spouse Name</label>
                <div class="flex items-center gap-4">
                    <label class="inline-flex items-center">
                        <input type="radio" name="relative" value="Father" class="form-radio">
                        <span class="ml-2 text-gray-700">Father</span>
                    </label>
                    <label class="inline-flex items-center">
                        <input type="radio" name="relative" value="Spouse" class="form-radio">
                        <span class="ml-2 text-gray-700">Spouse</span>
                    </label>
                    <label class="inline-flex items-center">
                        <input type="radio" name="relative" value="Other" class="form-radio">
                        <span class="ml-2 text-gray-700">Other</span>
                    </label>
                </div>
            </div>
            <div class="flex flex-col gap-4">
                <button id="next-btn-1" class="w-full bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out">
                    Next
                </button>
                <button id="exit-btn-1" class="w-full bg-red-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500 transition duration-300 ease-in-out">
                    Exit
                </button>
            </div>
        </div>

        <div id="registration-section-2" class="hidden">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="nationality" class="block text-gray-700 text-sm font-semibold mb-2">Nationality</label>
                    <select id="nationality" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        <option value="Indian">Indian</option>
                        <option value="Other">Other</option>
                    </select>
                </div>
                <div>
                    <label for="religion" class="block text-gray-700 text-sm font-semibold mb-2">Religion</label>
                    <select id="religion" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        <option value="">Select</option>
                        <option value="Hindu">Hindu</option>
                        <option value="Muslim">Muslim</option>
                        <option value="Christian">Christian</option>
                        <option value="Other">Other</option>
                    </select>
                </div>
            </div>
            <div class="mb-4">
                <label for="abha-number" class="block text-gray-700 text-sm font-semibold mb-2">ABHA Number</label>
                <input type="text" id="abha-number" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="ABHA Number">
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="department" class="block text-gray-700 text-sm font-semibold mb-2">Department / Doctor I wish to consult</label>
                    <input type="text" id="department" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Department / Doctor I wish to consult">
                </div>
                <div>
                    <label for="referral-doctor" class="block text-gray-700 text-sm font-semibold mb-2">Referral Doctor Name</label>
                    <input type="text" id="referral-doctor" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Referral Doctor Name">
                </div>
            </div>
            <div class="flex flex-col md:flex-row gap-4">
                <button id="previous-btn-2" class="w-full bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out">
                    Previous
                </button>
                <button id="next-btn-2" class="w-full bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out">
                    Next
                </button>
            </div>
        </div>

        <div id="registration-section-3" class="hidden">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="door-street" class="block text-gray-700 text-sm font-semibold mb-2 required">Door No / Street Name</label>
                    <input type="text" id="door-street" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
                <div>
                    <label for="locality" class="block text-gray-700 text-sm font-semibold mb-2">Locality</label>
                    <input type="text" id="locality" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="country" class="block text-gray-700 text-sm font-semibold mb-2 required">Country</label>
                    <select id="country" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                        <option value="India">India</option>
                    </select>
                </div>
                <div>
                    <label for="state" class="block text-gray-700 text-sm font-semibold mb-2">State</label>
                    <input type="text" id="state" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Karnataka">
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="district" class="block text-gray-700 text-sm font-semibold mb-2 required">District</label>
                    <input type="text" id="district" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500" placeholder="Bengaluru">
                </div>
                <div>
                    <label for="town-city" class="block text-gray-700 text-sm font-semibold mb-2">Town/City</label>
                    <input type="text" id="town-city" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
                <div>
                    <label for="pincode" class="block text-gray-700 text-sm font-semibold mb-2 required">Pincode</label>
                    <input type="text" id="pincode" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
                <div>
                    <label for="landline-mobile" class="block text-gray-700 text-sm font-semibold mb-2 required">Landline / Mobile</label>
                    <input type="text" id="landline-mobile" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
            </div>
            <div class="mb-6">
                <label for="email" class="block text-gray-700 text-sm font-semibold mb-2">Email</label>
                <input type="email" id="email" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-indigo-500">
            </div>
            <div class="mb-6">
                <label class="inline-flex items-start">
                    <input type="checkbox" id="declaration" class="mt-1 form-checkbox">
                    <span class="ml-2 text-gray-700 text-sm">This above information provided is true and correct to the best of my knowledge. I also understand that what I have disclosed to the healthcare team is deemed as an authorization for the management of my health. I agree to abide by rules and regulations of the hospital and country related to my medical treatment</span>
                </label>
            </div>
            <div class="flex flex-col md:flex-row gap-4">
                <button id="previous-btn-3" class="w-full bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out">
                    Previous
                </button>
                <button id="finish-btn" class="w-full bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out">
                    Finish
                </button>
            </div>
        </div>
        
        <div id="success-section" class="hidden text-center">
            <h2 class="text-2xl font-bold text-green-600 mb-4">Registration Successful!</h2>
            <p class="text-gray-700 mb-2">Please show the following temporary ID at the reception counter:</p>
            <p class="text-4xl font-extrabold text-indigo-700 my-4">Temporary ID: <span id="temporary-id"></span></p>
            <div class="flex flex-col md:flex-row gap-4 mt-6">
                <button id="add-new-patient-btn" class="w-full bg-blue-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-500 transition duration-300 ease-in-out">
                    ADD NEW PATIENT
                </button>
                <button id="exit-btn-final" class="w-full bg-red-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-red-500 transition duration-300 ease-in-out">
                    Exit
                </button>
            </div>
        </div>

    </div>

    <div id="message-box" class="message-box"></div>

    <script>
        const nextBtn1 = document.getElementById('next-btn-1');
        const exitBtn1 = document.getElementById('exit-btn-1');
        const previousBtn2 = document.getElementById('previous-btn-2');
        const nextBtn2 = document.getElementById('next-btn-2');
        const previousBtn3 = document.getElementById('previous-btn-3');
        const finishBtn = document.getElementById('finish-btn');
        const addNewPatientBtn = document.getElementById('add-new-patient-btn');
        const exitBtnFinal = document.getElementById('exit-btn-final');
        
        const registrationSection1 = document.getElementById('registration-section-1');
        const registrationSection2 = document.getElementById('registration-section-2');
        const registrationSection3 = document.getElementById('registration-section-3');
        const successSection = document.getElementById('success-section');
        const messageBox = document.getElementById('message-box');
        const registrationDateInput = document.getElementById('registration-date');
        const registrationTimeInput = document.getElementById('registration-time');
        const temporaryIdSpan = document.getElementById('temporary-id');
        const aadharNumberInput = document.getElementById('aadhar-number');
        const dobDdInput = document.getElementById('dob-dd');
        const dobMmInput = document.getElementById('dob-mm');
        const dobYyInput = document.getElementById('dob-yy');
        const firstNameInput = document.getElementById('first-name');
        const lastNameInput = document.getElementById('last-name');
        const emailInput = document.getElementById('email');

        const showMessage = (message, type) => {
            messageBox.textContent = message;
            messageBox.className = `message-box show message-${type}`;
            setTimeout(() => {
                messageBox.classList.remove('show');
            }, 3000);
        };

        const setDateTime = () => {
            const now = new Date();
            const date = now.toLocaleDateString('en-GB', { day: '2-digit', month: '2-digit', year: 'numeric' }).replace(/\//g, '/');
            const time = now.toLocaleTimeString('en-US', { hour: '2-digit', minute: '2-digit', hour12: false });
            if (registrationDateInput) registrationDateInput.value = date;
            if (registrationTimeInput) registrationTimeInput.value = time;
        };
        
        const isValidDate = (day, month, year) => {
            const d = parseInt(day, 10);
            const m = parseInt(month, 10);
            const y = parseInt(year, 10);
            if (isNaN(d) || isNaN(m) || isNaN(y)) {
                return false;
            }
            const date = new Date(y, m - 1, d);
            return date.getFullYear() === y && date.getMonth() === m - 1 && date.getDate() === d;
        };

        dobDdInput.addEventListener('input', (event) => {
            if (event.target.value.length === event.target.maxLength) {
                dobMmInput.focus();
            }
        });

        dobMmInput.addEventListener('input', (event) => {
            if (event.target.value.length === event.target.maxLength) {
                dobYyInput.focus();
            }
        });

        document.addEventListener('DOMContentLoaded', () => {
            setDateTime();
            registrationSection1.classList.remove('hidden');
        });

        const patientData = {};

        nextBtn1.addEventListener('click', () => {
            const aadharNumber = aadharNumberInput.value.trim();
            const day = dobDdInput.value.trim();
            const month = dobMmInput.value.trim();
            const year = dobYyInput.value.trim();
            const firstName = firstNameInput.value.trim();
            const lastName = lastNameInput.value.trim();
            const gender = document.querySelector('input[name="gender"]:checked');
            const transgender = document.querySelector('input[name="gender-transgender"]:checked');
            const title = document.getElementById('title').value;

            if (!firstName || !lastName) {
                showMessage("First Name and Last Name are required.", "error");
                return;
            }
            if (!gender && !transgender) {
                showMessage("Please select a gender.", "error");
                return;
            }
            if (!title) {
                showMessage("Please select a title.", "error");
                return;
            }

            if (aadharNumber && (aadharNumber.length !== 12 || isNaN(aadharNumber))) {
                showMessage("Please enter a valid 12-digit Aadhaar number.", "error");
                return;
            }

            if ((day || month || year) && !isValidDate(day, month, year)) {
                showMessage("Enter a correct date. Format: DD (2 digits), MM (2 digits), YYYY (4 digits).", "error");
                return;
            }
            
            patientData.firstName = firstName;
            patientData.lastName = lastName;
            patientData.aadharNumber = aadharNumber;
            patientData.dob = `${day}/${month}/${year}`;
            patientData.gender = gender?.value || transgender?.value;
            patientData.title = title;
            patientData.relative = document.querySelector('input[name="relative"]:checked')?.value;

            registrationSection1.classList.add('hidden');
            registrationSection2.classList.remove('hidden');
        });

        exitBtn1.addEventListener('click', () => {
            showMessage("Application closed.", "success");
        });
        
        previousBtn2.addEventListener('click', () => {
            registrationSection2.classList.add('hidden');
            registrationSection1.classList.remove('hidden');
        });
        
        nextBtn2.addEventListener('click', () => {
            patientData.nationality = document.getElementById('nationality').value;
            patientData.religion = document.getElementById('religion').value;
            patientData.abhaNumber = document.getElementById('abha-number').value;
            patientData.department = document.getElementById('department').value;
            patientData.referralDoctor = document.getElementById('referral-doctor').value;

            registrationSection2.classList.add('hidden');
            registrationSection3.classList.remove('hidden');
        });

        previousBtn3.addEventListener('click', () => {
            registrationSection3.classList.add('hidden');
            registrationSection2.classList.remove('hidden');
        });
        
        finishBtn.addEventListener('click', () => {
            const declarationCheckbox = document.getElementById('declaration');
            const requiredFields = ['door-street', 'country', 'district', 'pincode', 'landline-mobile'];
            
            for (const fieldId of requiredFields) {
                if (!document.getElementById(fieldId).value.trim()) {
                    showMessage("Please fill in all required fields.", "error");
                    return;
                }
            }

            if (!declarationCheckbox.checked) {
                showMessage("Please agree to the declaration before finishing.", "error");
                return;
            }

            patientData.doorStreet = document.getElementById('door-street').value;
            patientData.locality = document.getElementById('locality').value;
            patientData.country = document.getElementById('country').value;
            patientData.state = document.getElementById('state').value;
            patientData.district = document.getElementById('district').value;
            patientData.townCity = document.getElementById('town-city').value;
            patientData.pincode = document.getElementById('pincode').value;
            patientData.landlineMobile = document.getElementById('landline-mobile').value;
            patientData.email = emailInput.value;
            patientData.registrationDate = registrationDateInput.value;
            patientData.registrationTime = registrationTimeInput.value;

            const tempId = Math.floor(10000000 + Math.random() * 90000000);
            patientData.tempId = tempId;

            localStorage.setItem(tempId, JSON.stringify(patientData));
            
            temporaryIdSpan.textContent = tempId;
            registrationSection3.classList.add('hidden');
            successSection.classList.remove('hidden');
            showMessage("Registration form data submitted successfully.", "success");
        });

        addNewPatientBtn.addEventListener('click', () => {
            successSection.classList.add('hidden');
            registrationSection1.classList.remove('hidden');
            document.getElementById('aadhar-number').value = '';
            document.getElementById('dob-dd').value = '';
            document.getElementById('dob-mm').value = '';
            document.getElementById('dob-yy').value = '';
            document.getElementById('first-name').value = '';
            document.getElementById('last-name').value = '';
            document.getElementById('abha-number').value = '';
            document.getElementById('department').value = '';
            document.getElementById('referral-doctor').value = '';
            document.getElementById('door-street').value = '';
            document.getElementById('locality').value = '';
            document.getElementById('state').value = '';
            document.getElementById('district').value = '';
            document.getElementById('town-city').value = '';
            document.getElementById('pincode').value = '';
            document.getElementById('landline-mobile').value = '';
            document.getElementById('email').value = '';
            
            const radioButtons = document.querySelectorAll('input[name="gender"], input[name="relative"]');
            radioButtons.forEach(radio => radio.checked = false);
            
            const checkboxes = document.querySelectorAll('input[type="checkbox"]');
            checkboxes.forEach(checkbox => checkbox.checked = false);
            
            document.getElementById('title').value = ''; // Reset the title dropdown
            
            setDateTime();
        });

        exitBtnFinal.addEventListener('click', () => {
            showMessage("Application closed.", "success");
        });

    </script>
</body>
</html>
