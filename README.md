
<!DOCTYPE html>
<html lang="ka">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>სტუდენტების შერჩევა</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background: linear-gradient(45deg, rgba(255, 0, 79, 0.6), rgba(255, 115, 0, 0.6), rgba(255, 235, 0, 0.6), rgba(63, 255, 108, 0.6), rgba(0, 168, 255, 0.6));
            background-size: 600% 600%;
            animation: gradient 15s ease infinite;
            #groupSizeOptions button.not-recommended {
    background-color: #ff5722; /* სტაფილოსფერი */
    color: white;
}

        }
        .container {
            display: flex;
            flex-direction: column;
            align-items: center;
            width: 80%;
            max-width: 600px;
        }
        .input-container {
            position: fixed;
            top: 20px;
            right: 20px;
            text-align: center;
        }
        #nameInput {
            padding: 10px;
            width: 250px;
            margin-bottom: 10px;
        }
        button {
            padding: 10px 20px;
            margin: 5px;
            border: none;
            background-color: #007bff;
            color: white;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #0056b3;
        }
        .name-list {
            margin-top: 20px;
            width: 100%;
            max-height: 300px;
            overflow-y: auto;
            #groupSizeOptions button.not-recommended {
    background-color: #ffa500; /* სტაფილოსფერი */
    color: #fff;
}

        }
        .name {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 5px;
            border: 1px solid #ccc;
            margin: 5px 0;
            background-color: #fff;
            border-radius: 5px;
        }
        .delete-button {
            cursor: pointer;
            color: red;
            font-weight: bold;
        }
        .winner {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 4em;
            text-align: center;
            z-index: 1000;
            display: none;
            color: white;
            background-color: rgba(0, 0, 0, 0.5);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.5);
            text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
        }
        .pairing-button {
            position: fixed;
            top: 20px;
            left: 20px;
        }
        .groups-list {
            margin-top: 20px;
            text-align: center;
        }
        .group {
            margin: 5px;
            font-size: 18px;
        }
        #groupSizeOptions {
            display: flex;
            justify-content: center;
            margin-top: 10px;
        }
        #nameCounter {
            margin-top: 10px;
            font-size: 18px;
            color: white;
        }
        @keyframes gradient {
            0% { background-position: 0% 0%; }
            50% { background-position: 100% 100%; }
            100% { background-position: 0% 0%; }
        }
        #groupSizeOptions button.recommended {
            background-color: #28a745; /* გამწვანებული ფერი რეკომენდირებული ზომისთვის */
        }
        /* Keep the background white initially */
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: white;
}

/* Countdown timer in the bottom-right corner */
#timer {
  position: fixed;
  bottom: 10px;
  right: 10px;
  font-size: 24px;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  padding: 10px;
  border-radius: 5px;
  z-index: 10;
}
.enlarge-button {
    background-color: #4CAF50;
    color: white;
    border: none;
    padding: 10px 20px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
    margin: 4px 2px;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .enlarge-button:hover {
    background-color: #45a049;
  }

  /* Styles for the enlarged view */
  .enlarged {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(255, 255, 255, 0.8);
    backdrop-filter: blur(5px);
    z-index: 1000;
    display: flex;
    justify-content: center;
    align-items: center;
    opacity: 0;
    transition: opacity 0.3s ease-in-out;
  }

  .enlarged.show {
    opacity: 1;
  }

  .enlarged-content {
    background-color: white;
    padding: 40px;
    border-radius: 10px;
    box-shadow: 0 0 20px rgba(0,0,0,0.2);
    max-width: 80%;
    max-height: 80%;
    overflow-y: auto;
    text-align: center;
  }

  /* Close button for the enlarged view */
  .close-button {
    position: absolute;
    top: 20px;
    right: 20px;
    font-size: 30px;
    cursor: pointer;
    background-color: #f44336;
    color: white;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    transition: background-color 0.3s;
  }

  .close-button:hover {
    background-color: #d32f2f;
  }

  /* Style for enlarged groups */
  .enlarged .group {
    font-size: 53px;
    margin-bottom: 30px;
    text-transform: uppercase;
  }
/* Hide the message and RGB background initially */
#message {
  display: none;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 48px;
  font-weight: bold;
  color: white;
  z-index: 20;
  opacity: 0;
  animation: fadeIn 2s forwards;
}

@keyframes fadeIn {
  to { opacity: 1; }
}

/* RGB background animation */
@keyframes rgbBackground {
  0% { background-color: red; }
  33% { background-color: green; }
  66% { background-color: blue; }
  100% { background-color: red; }
}

/* Animate background after countdown finishes */
#rgbBackground {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  animation: rgbBackground 5s infinite;
  display: none; /* Hidden until the countdown finishes */
}

/* Password input form */
#passwordForm {
  display: none;
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: white;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.5);
  z-index: 30;
}

#passwordForm input {
  margin-bottom: 10px;
  padding: 10px;
  font-size: 16px;
}

    </style>
</head>
<body><div id="product-content">
    <!-- პროდუქტის კონტენტი -->
    
  </div>

  <div id="timer"></div>
  <div id="rgbBackground"></div>
  <div id="message">საიტი გათიშულია</div>

  <!-- პაროლის ფორმა -->
  <div id="passwordForm">
    <h2>გთხოვთ შეიყვანოთ პაროლი</h2>
    <input type="password" id="passwordInput" placeholder="პაროლი">
    <button onclick="checkPassword()">შეამოწმე</button>
    <button onclick="closePasswordForm()">გაუქმე</button>
  </div>

    <div class="container">
        <div class="input-container">
            <input type="text" id="nameInput" placeholder="შეიყვანეთ მოსწავლის სახელი">
            <button id="addNameButton">დამატება</button>
        </div>
        <button id="selectStudentButton">მოსწავლის არჩევა</button>
        <button id="pairStudentsButton" class="pairing-button">ჯგუფების დაწყვილება</button>
        <div id="nameCounter">სულ სტუდენტები: 0</div>
        <div id="nameList" class="name-list"></div>
        <div id="winnerDisplay" class="winner"></div>
        <div id="groupsList" class="groups-list"></div>
        <div id="groupSizeOptions">
            <button id="enlargeButton" class="enlarge-button">გადიდება</button>
            <button onclick="distributeGroups(2)">2</button>
            <button onclick="distributeGroups(3)">3</button>
            <button onclick="distributeGroups(4)">4</button>
            <button onclick="distributeGroups(5)">5</button>
            <button onclick="distributeGroups(6)">6</button>
            <button onclick="distributeGroups(7)">7</button>
        </div>
    </div>
<script>
    let students = [];
    let availableStudents = [];
    let templates = JSON.parse(localStorage.getItem('templates')) || {};

    const nameInput = document.getElementById('nameInput');
    const addNameButton = document.getElementById('addNameButton');
    const selectStudentButton = document.getElementById('selectStudentButton');
    const pairStudentsButton = document.getElementById('pairStudentsButton');
    const groupSizeOptions = document.getElementById('groupSizeOptions');
    const nameList = document.getElementById('nameList');
    const winnerDisplay = document.getElementById('winnerDisplay');
    const groupsList = document.getElementById('groupsList');
    const nameCounter = document.getElementById('nameCounter');

    addNameButton.addEventListener('click', addStudent);
    selectStudentButton.addEventListener('click', selectRandomStudent);

    function addStudent() {
        const name = nameInput.value.trim();

        if (name.includes("=")) {
            const [templateName, templateContent] = name.split("=").map(item => item.trim());
            if (templateContent.startsWith('"') && templateContent.endsWith('"')) {
                const individualNames = templateContent.slice(1, -1).split(/\s+/);
                templates[templateName] = individualNames;
                localStorage.setItem('templates', JSON.stringify(templates));
                alert(`შაბლონი "${templateName}" დამატებულია`);
            }
        } else if (templates[name]) {
            students.push(...templates[name]);
            availableStudents.push(...templates[name]);
        } else if (name) {
            students.push(name);
            availableStudents.push(name);
        }
        
        nameInput.value = '';
        updateNameList();
        updatePairButtonState();
        updateButtonHighlighting();
    }

    function updateNameList() {
        nameList.innerHTML = '';
        students.forEach((student, index) => {
            const nameElement = document.createElement('div');
            nameElement.className = 'name';
            nameElement.innerHTML = `
                ${student}
                <span class="delete-button" onclick="deleteStudent(${index})">X</span>
            `;
            nameList.appendChild(nameElement);
        });
        nameCounter.textContent = `სულ სტუდენტები: ${students.length}`;
    }

    function deleteStudent(index) {
        students.splice(index, 1);
        availableStudents = [...students];
        updateNameList();
        updatePairButtonState();
        updateButtonHighlighting();
    }

    function updatePairButtonState() {
        if (students.length < 4) {
            pairStudentsButton.disabled = true;
        } else {
            pairStudentsButton.disabled = false;
        }
    }

    function selectRandomStudent() {
        if (availableStudents.length === 0) {
            availableStudents = [...students];
        }

        const randomIndex = Math.floor(Math.random() * availableStudents.length);
        const selectedStudent = availableStudents.splice(randomIndex, 1)[0];

        winnerDisplay.textContent = `შერჩეული მოსწავლე: ${selectedStudent}`;
        winnerDisplay.style.display = 'block';

        setTimeout(() => {
            winnerDisplay.style.display = 'none';
        }, 3000);
    }

    function distributeGroups(groupSize) {
        if (groupSize >= students.length) {
            alert(`ჯგუფი ვერ შეიქმნება ${groupSize}-იანი, სტუდენტების რაოდენობა ძალიან ცოტაა.`);
            return;
        }

        const shuffled = [...students].sort(() => 0.5 - Math.random());
        const groups = [];
        
        let remainingStudents = students.length;
        let index = 0;

        while (remainingStudents > 0) {
            const currentGroupSize = Math.min(groupSize, remainingStudents);

            if (remainingStudents === groupSize + 1 && groupSize > 2) {
                // Adjust to prevent creating a group with only 1 member
                currentGroupSize--;
            }

            groups.push(shuffled.slice(index, index + currentGroupSize));
            index += currentGroupSize;
            remainingStudents -= currentGroupSize;
        }

        displayGroups(groups);
    }

    function displayGroups(groups) {
        groupsList.innerHTML = '';
        groups.forEach((group, index) => {
            const groupElement = document.createElement('div');
            groupElement.className = 'group';
            groupElement.textContent = `ჯგუფი ${index + 1}: ${group.join(', ')}`;
            groupsList.appendChild(groupElement);
        });
    }

    function updateButtonHighlighting() {
        document.querySelectorAll('#groupSizeOptions button').forEach(button => {
            const size = parseInt(button.textContent);
            button.classList.remove('recommended');

            if (students.length % size === 0 && students.length >= size) {
                button.classList.add('recommended');
            }
        });
    }
    function distributeGroups(groupSize) {
    // Prevent group creation if group size equals or is greater than the number of students
    if (groupSize >= students.length) {
        alert(`ჯგუფი ვერ შეიქმნება ${groupSize}-იანი, სტუდენტების რაოდენობა ძალიან ცოტაა.`);
        return;
    }

    // Calculate the remainder when dividing the number of students by the group size
    const remainder = students.length % groupSize;

    // If there's a remainder of 1, create groups and add the extra student to one group
    if (remainder === 1) {
        const adjustedGroupSize = groupSize;
        const groups = [];
        const shuffled = [...students].sort(() => 0.5 - Math.random());

        let remainingStudents = students.length;
        let index = 0;

        while (remainingStudents > 0) {
            const currentGroupSize = Math.min(adjustedGroupSize, remainingStudents);

            // Create groups with adjusted size to accommodate the remainder
            if (remainingStudents === adjustedGroupSize + 1) {
                // Adjust the last group size
                groups.push(shuffled.slice(index, index + adjustedGroupSize - 1));
                index += adjustedGroupSize - 1;
                remainingStudents -= adjustedGroupSize - 1;
            } else {
                groups.push(shuffled.slice(index, index + currentGroupSize));
                index += currentGroupSize;
                remainingStudents -= currentGroupSize;
            }
        }

        // Add the extra student to the first group (or any group as per your preference)
        if (groups.length > 0) {
            groups[0].push(shuffled[index]);
        }

        displayGroups(groups);
        return;
    }

    // Normal distribution without remainder of 1
    if (students.length % groupSize === 0) {
        const shuffled = [...students].sort(() => 0.5 - Math.random());
        const groups = [];
        
        let remainingStudents = students.length;
        let index = 0;

        while (remainingStudents > 0) {
            const currentGroupSize = Math.min(groupSize, remainingStudents);

            groups.push(shuffled.slice(index, index + currentGroupSize));
            index += currentGroupSize;
            remainingStudents -= currentGroupSize;
        }

        displayGroups(groups);
    }
}

function updateButtonHighlighting() {
    document.querySelectorAll('#groupSizeOptions button').forEach(button => {
        const size = parseInt(button.textContent);
        button.classList.remove('recommended', 'not-recommended');

        if (students.length % size === 0 && students.length >= size) {
            button.classList.add('recommended');
        } else if (students.length % size === 1 && students.length >= size) {
            button.classList.add('not-recommended');
        }
    });
}

function distributeGroups(groupSize) {
    // Prevent group creation if conditions are not met
    if (groupSize < 2 || groupSize > 7 || students.length < 5 || students.length > 30) {
        alert(`ჯგუფების შექმნა შესაძლებელია 5-დან 30-მდე სტუდენტისთვის და 2-დან 7-მდე ჯგუფის ზომისთვის.`);
        return;
    }

    const totalStudents = students.length;
    const numberOfGroups = Math.ceil(totalStudents / groupSize);
    const minGroupSize = Math.floor(totalStudents / numberOfGroups);
    const remainder = totalStudents % numberOfGroups;

    // Create an array to hold our groups
    const groups = [];

    // Shuffle the students array
    const shuffledStudents = [...students].sort(() => 0.5 - Math.random());

    let currentIndex = 0;

    // Distribute students into groups
    for (let i = 0; i < numberOfGroups; i++) {
        const currentGroupSize = minGroupSize + (i < remainder ? 1 : 0);
        groups.push(shuffledStudents.slice(currentIndex, currentIndex + currentGroupSize));
        currentIndex += currentGroupSize;
    }

    displayGroups(groups);
}
function distributeGroups(groupSize) {
    // Prevent group creation if conditions are not met
    if (groupSize < 2 || groupSize > 7 || students.length < 5 || students.length > 30) {
        alert(`ჯგუფების შექმნა შესაძლებელია 5-დან 30-მდე სტუდენტისთვის და 2-დან 7-მდე ჯგუფის ზომისთვის.`);
        return;
    }

    const totalStudents = students.length;
    const baseGroupCount = Math.floor(totalStudents / groupSize);
    const remainder = totalStudents % groupSize;

    // Create an array to hold our groups
    const groups = [];

    // Shuffle the students array
    const shuffledStudents = [...students].sort(() => 0.5 - Math.random());

    let currentIndex = 0;

    // Distribute students into groups
    for (let i = 0; i < baseGroupCount; i++) {
        const currentGroupSize = groupSize + (i < remainder ? 1 : 0);
        groups.push(shuffledStudents.slice(currentIndex, currentIndex + currentGroupSize));
        currentIndex += currentGroupSize;
    }

    // If there are any remaining students, add them to the last group
    if (currentIndex < totalStudents) {
        groups[groups.length - 1].push(...shuffledStudents.slice(currentIndex));
    }

    displayGroups(groups);
}
function updateButtonHighlighting() {
    document.querySelectorAll('#groupSizeOptions button').forEach(button => {
        const size = parseInt(button.textContent);
        button.classList.remove('recommended', 'not-recommended');

        if (students.length >= 5 && size >= 2 && size <= 7) {
            if (students.length % size === 0) {
                button.classList.add('recommended');
                button.title = 'ჯგუფები ზუსტად გადანაწილდებიან';
            } else {
                button.classList.add('not-recommended');
                button.title = 'ჯგუფის წევრები ზუსტად ვერ გადანაწილდებიან, მაგრამ სხვაობა მცირე იქნება';
            }
        } else {
            button.classList.remove('recommended', 'not-recommended');
            button.title = '';
        }
    });
}
// გლობალური ცვლადები
let countdownTime;
let timerInterval;
let rightClickStartTime;
let isRightClickHeld = false;

// ელემენტების მოძიება
const timerElement = document.getElementById('timer');
const messageElement = document.getElementById('message');
const rgbBackground = document.getElementById('rgbBackground');
const productContent = document.getElementById('product-content');
const passwordForm = document.getElementById('passwordForm');

// შევამოწმოთ საიტის მდგომარეობა
function checkSiteStatus() {
  const siteStatus = localStorage.getItem('siteStatus');
  const remainingTime = localStorage.getItem('remainingTime');
  const lastUpdateTime = localStorage.getItem('lastUpdateTime');

  if (siteStatus === 'shutdown') {
    showShutdownState();
  } else if (siteStatus === 'counting' && remainingTime && lastUpdateTime) {
    const elapsedTime = Math.floor((Date.now() - parseInt(lastUpdateTime)) / 1000);
    countdownTime = Math.max(0, parseInt(remainingTime) - elapsedTime);

    if (countdownTime > 0) {
      startCountdown();
    } else {
      showShutdownState();
    }
  } else {
    startCountdown();
  }
}

function startCountdown() {
  // გავასუფთაოთ წინა ინტერვალი, თუ არსებობს
  if (timerInterval) {
    clearInterval(timerInterval);
  }

  if (countdownTime === undefined) {
    countdownTime = 36720000// დროის ათვლის საწყისი მნიშვნელობა
  }

  localStorage.setItem('siteStatus', 'counting');

  // აჩვენე პროდუქტის კონტენტი და დამალე შატდაუნის ელემენტები
  document.body.style.backgroundColor = 'white';
  rgbBackground.style.display = 'none';
  messageElement.style.display = 'none';
  productContent.style.display = 'block';

  function updateTimer() {
    if (countdownTime > 0) {
      timerElement.textContent = `დარჩენილი დრო: ${countdownTime} წამი`;
      timerElement.style.display = 'block';
      localStorage.setItem('remainingTime', countdownTime);
      localStorage.setItem('lastUpdateTime', Date.now());
      countdownTime--;
    } else {
      clearInterval(timerInterval);
      localStorage.setItem('siteStatus', 'shutdown');
      showShutdownState();
    }
  }

  updateTimer(); // გამოიძახე ერთხელ დაუყოვნებლივ
  timerInterval = setInterval(updateTimer, 1000);
}

function showShutdownState() {
  timerElement.style.display = 'none';
  document.body.style.backgroundColor = 'black';
  rgbBackground.style.display = 'block';
  messageElement.style.display = 'block';
  productContent.style.display = 'none';
  passwordForm.style.display = 'block'; // გამოჩნდეს პაროლის ფორმა
  localStorage.setItem('siteStatus', 'shutdown');
}

function checkPassword() {
  const passwordInput = document.getElementById('passwordInput').value;
  if (passwordInput === 'osqelaparoli@13') {
    passwordForm.style.display = 'none';
    startCountdown();
  } else {
    alert('არასწორი პაროლი. სცადეთ ხელახლა.');
  }
}

function closePasswordForm() {
  passwordForm.style.display = 'none';
}

// მარჯვენა ღილაკის დაჭერის დამუშავება
document.addEventListener('mousedown', function(event) {
    if (event.button === 2) { // 2 არის მარჯვენა ღილაკის კოდი
        event.preventDefault(); // სტანდარტული კონტექსტური მენიუს გამოჩენის პრევენცია
        rightClickStartTime = Date.now();
        isRightClickHeld = true;
  }
});

document.addEventListener('mouseup', function(event) {
  if (event.button === 2) {
    isRightClickHeld = false;
  }
});

// კონტექსტური მენიუს გამოჩენის პრევენცია
document.addEventListener('contextmenu', function(event) {
  event.preventDefault();
});

// ყოველ 100 მილიწამში ვამოწმებთ, ხომ არ გავიდა 10 წამი მარჯვენა ღილაკის დაჭერიდან
setInterval(function() {
  if (isRightClickHeld && Date.now() - rightClickStartTime >= 10000) {
    isRightClickHeld = false;
    // არ დაიწყოს დროის ათვლა ხელახლა, თუ პაროლი არ არის შეყვანილი
  }
}, 100);

// გვერდის ჩატვირთვისას შევამოწმოთ საიტის მდგომარეობა
document.addEventListener('DOMContentLoaded', checkSiteStatus);

// CSS სტილები (დაამატეთ თქვენს არსებულ CSS-ს)
/*
#groupSizeOptions button.recommended {
    background-color: #28a745; // მწვანე
}

#groupSizeOptions button.not-recommended {
    background-color: #dc3545; // წითელი
    color: white;
}
*/function distributeGroups(groupSize) {
    // შევამოწმოთ, რომ სტუდენტების რაოდენობა 5-დან 35-მდეა
    if (students.length < 5 || students.length > 35) {
        alert(`ჯგუფების შექმნა შესაძლებელია 5-დან 35-მდე სტუდენტისთვის.`);
        return;
    }

    // შევამოწმოთ, რომ ჯგუფის ზომა 2-დან 7-მდეა
    if (groupSize < 2 || groupSize > 7) {
        alert(`ჯგუფის ზომა უნდა იყოს 2-დან 7-მდე.`);
        return;
    }

    const totalStudents = students.length;
    
    // გამოვთვალოთ ჯგუფების რაოდენობა, მინიმუმ 2
    let numberOfGroups = Math.max(2, Math.min(Math.floor(totalStudents / groupSize), Math.floor(totalStudents / 2)));
    
    // გამოვთვალოთ მინიმალური და მაქსიმალური ჯგუფის ზომები
    const minGroupSize = Math.floor(totalStudents / numberOfGroups);
    const maxGroupSize = Math.ceil(totalStudents / numberOfGroups);
    const numberOfLargerGroups = totalStudents % numberOfGroups;

    // შევქმნათ მასივი ჯგუფების ზომებით
    const groupSizes = Array(numberOfGroups).fill(minGroupSize);
    for (let i = 0; i < numberOfLargerGroups; i++) {
        groupSizes[i] = maxGroupSize;
    }

    // შევქმნათ მასივი ჯგუფებისთვის
    const groups = [];

    // არეულად დავალაგოთ სტუდენტები
    const shuffledStudents = [...students].sort(() => 0.5 - Math.random());

    let currentIndex = 0;
    for (const size of groupSizes) {
        groups.push(shuffledStudents.slice(currentIndex, currentIndex + size));
        currentIndex += size;
    }

    displayGroups(groups);
}function updateButtonHighlighting() {
    document.querySelectorAll('#groupSizeOptions button').forEach(button => {
        const size = parseInt(button.textContent);
        button.classList.remove('recommended', 'not-recommended');

        if (students.length >= 5 && students.length <= 35 && size >= 2 && size <= 7) {
            const totalStudents = students.length;
            
            // შევამოწმოთ, შესაძლებელია თუ არა მოთხოვნილი ზომის ჯგუფების შექმნა
            if (totalStudents % size > 0 && totalStudents % size < size - 1) {
                button.classList.add('not-recommended');
                button.title = `${size} კაციანი ჯგუფები ვერ გაკეთდება ${totalStudents} სტუდენტისთვის`;
            } else {
                const numberOfGroups = Math.max(2, Math.min(Math.floor(totalStudents / size), Math.floor(totalStudents / 2)));
                const minGroupSize = Math.floor(totalStudents / numberOfGroups);
                const maxGroupSize = Math.ceil(totalStudents / numberOfGroups);
                
                if (maxGroupSize - minGroupSize <= 1) {
                    button.classList.add('recommended');
                    button.title = `${numberOfGroups} ჯგუფი, ${minGroupSize}-${maxGroupSize} სტუდენტით`;
                } else {
                    button.classList.add('not-recommended');
                    button.title = 'არათანაბარი განაწილება';
                }
            }
        } else {
            button.classList.remove('recommended', 'not-recommended');
            button.title = '';
        }
    });
}
 document.addEventListener('DOMContentLoaded', function() {
    const enlargeButton = document.getElementById('enlargeButton');
    const groupsList = document.getElementById('groupsList');
    const container = document.querySelector('.container');

    enlargeButton.addEventListener('click', function() {
      // Create a new div for the enlarged view
      const enlargedView = document.createElement('div');
      enlargedView.className = 'enlarged';

      const enlargedContent = document.createElement('div');
      enlargedContent.className = 'enlarged-content';
      enlargedContent.innerHTML = groupsList.innerHTML;

      enlargedView.appendChild(enlargedContent);

      // Add a close button
      const closeButton = document.createElement('span');
      closeButton.innerHTML = '&times;';
      closeButton.className = 'close-button';
      enlargedView.appendChild(closeButton);

      // Add the enlarged view to the body
      document.body.appendChild(enlargedView);

      // Animate the enlargement
      setTimeout(() => {
        enlargedView.classList.add('show');
      }, 50);

      // Close button functionality
      closeButton.addEventListener('click', function() {
        enlargedView.classList.remove('show');
        setTimeout(() => {
          document.body.removeChild(enlargedView);
        }, 300);
      });
    });
  });

  // Modify the existing displayGroups function to update both the original and enlarged view if it exists
  function displayGroups(groups) {
    const groupsHTML = groups.map((group, index) => 
      `<div class="group">ჯგუფი ${index + 1}: ${group.join(', ')}</div>`
    ).join('');

    groupsList.innerHTML = groupsHTML;

    // Update the enlarged view if it exists
    const enlargedContent = document.querySelector('.enlarged-content');
    if (enlargedContent) {
      enlargedContent.innerHTML = groupsHTML;
    }
  }
  function updateButtonHighlighting() {
    document.querySelectorAll('#groupSizeOptions button').forEach(button => {
        const size = parseInt(button.textContent);
        button.classList.remove('recommended', 'not-recommended', 'pulse');

        if (students.length >= 5 && students.length <= 35 && size >= 2 && size <= 7) {
            if (students.length % size === 0) {
                button.classList.add('recommended', 'pulse');
                button.title = `${students.length / size} ჯგუფი, თითოეულში ${size} სტუდენტით`;
            } else {
                button.classList.add('not-recommended');
                button.title = 'არათანაბარი განაწილება';
            }
        } else {
            button.title = '';
        }
    });
}
// შევამოწმოთ საიტის მდგომარეობა
function checkSiteStatus() {
  const siteStatus = localStorage.getItem('siteStatus');
  const remainingTime = localStorage.getItem('remainingTime');
  const lastUpdateTime = localStorage.getItem('lastUpdateTime');
  const isFirstVisit = localStorage.getItem('isFirstVisit') !== 'false';

  if (isFirstVisit) {
    localStorage.setItem('isFirstVisit', 'false');
    showShutdownState();
    return;
  }

  if (siteStatus === 'shutdown') {
    showShutdownState();
  } else if (siteStatus === 'counting' && remainingTime && lastUpdateTime) {
    const elapsedTime = Math.floor((Date.now() - parseInt(lastUpdateTime)) / 1000);
    countdownTime = Math.max(0, parseInt(remainingTime) - elapsedTime);

    if (countdownTime > 0) {
      startCountdown();
    } else {
      showShutdownState();
    }
  } else {
    startCountdown();
  }
}

// გვერდის ჩატვირთვისას შევამოწმოთ საიტის მდგომარეობა
document.addEventListener('DOMContentLoaded', checkSiteStatus);
if (!localStorage.getItem('isFirstVisit')) {
  localStorage.setItem('isFirstVisit', 'true');
}
// ფუნქცია შაბლონების ექსპორტისთვის
function exportTemplates() {
    const templates = JSON.parse(localStorage.getItem('templates')) || {};
    const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(templates));
    const downloadAnchorNode = document.createElement('a');
    downloadAnchorNode.setAttribute("href", dataStr);
    downloadAnchorNode.setAttribute("download", "templates.json");
    document.body.appendChild(downloadAnchorNode);
    downloadAnchorNode.click();
    downloadAnchorNode.remove();
}

// ფუნქცია შაბლონების იმპორტისთვის
function importTemplates(event) {
    const file = event.target.files[0];
    const reader = new FileReader();
    reader.onload = function(e) {
        try {
            const templates = JSON.parse(e.target.result);
            localStorage.setItem('templates', JSON.stringify(templates));
            alert('შაბლონები წარმატებით დაიმპორტდა!');
            // განაახლეთ ინტერფეისი საჭიროების შემთხვევაში
        } catch (error) {
            alert('შეცდომა შაბლონების იმპორტისას. გთხოვთ, შეამოწმეთ ფაილი.');
        }
    };
    reader.readAsText(file);
}
function addStudent() {
    const name = nameInput.value.trim();

    if (name === 'iii123') {
        exportTemplates();
        nameInput.value = '';
        return;
    }

    if (name === 'iii1234') {
        importTemplates();
        nameInput.value = '';
        return;
    }

    if (name.includes("=")) {
        const [templateName, templateContent] = name.split("=").map(item => item.trim());
        if (templateContent.startsWith('"') && templateContent.endsWith('"')) {
            const individualNames = templateContent.slice(1, -1).split(/\s+/);
            templates[templateName] = individualNames;
            localStorage.setItem('templates', JSON.stringify(templates));
            alert(`შაბლონი "${templateName}" დამატებულია`);
        }
    } else if (templates[name]) {
        students.push(...templates[name]);
        availableStudents.push(...templates[name]);
    } else if (name) {
        students.push(name);
        availableStudents.push(name);
    }
    
    nameInput.value = '';
    updateNameList();
    updatePairButtonState();
    updateButtonHighlighting();
}

// განვაახლოთ exportTemplates ფუნქცია
function exportTemplates() {
    const templates = JSON.parse(localStorage.getItem('templates')) || {};
    const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(templates));
    const downloadAnchorNode = document.createElement('a');
    downloadAnchorNode.setAttribute("href", dataStr);
    downloadAnchorNode.setAttribute("download", "templates.json");
    document.body.appendChild(downloadAnchorNode);
    downloadAnchorNode.click();
    downloadAnchorNode.remove();
    alert('შაბლონები წარმატებით დაექსპორტდა!');
}

// განვაახლოთ importTemplates ფუნქცია
function importTemplates() {
    const input = document.createElement('input');
    input.type = 'file';
    input.accept = '.json';
    input.onchange = function(event) {
        const file = event.target.files[0];
        const reader = new FileReader();
        reader.onload = function(e) {
            try {
                const templates = JSON.parse(e.target.result);
                localStorage.setItem('templates', JSON.stringify(templates));
                alert('შაბლონები წარმატებით დაიმპორტდა!');
            } catch (error) {
                alert('შეცდომა შაბლონების იმპორტისას. გთხოვთ, შეამოწმეთ ფაილი.');
            }
        };
        reader.readAsText(file);
    };
    input.click();
}

// დავამატოთ ეს ფუნქცია, რომ ავტომატურად დავტვირთოთ შაბლონები
function loadTemplates() {
    templates = JSON.parse(localStorage.getItem('templates')) || {};
}

// გამოვიძახოთ ეს ფუნქცია გვერდის ჩატვირთვისას
document.addEventListener('DOMContentLoaded', function() {
    loadTemplates();
    checkSiteStatus();
});

// მოდიფიცირებული updateButtonHighlighting ფუნქცია
function updateButtonHighlighting() {
    document.querySelectorAll('#groupSizeOptions button').forEach(button => {
        const size = parseInt(button.textContent);
        button.classList.remove('recommended', 'not-recommended', 'pulse');

        if (students.length >= 5 && students.length <= 35 && size >= 2 && size <= 7) {
            if (students.length % size === 0 && students.length !== size) {
                button.classList.add('recommended', 'pulse');
                button.title = `${students.length / size} ჯგუფი, თითოეულში ${size} სტუდენტით`;
            } else {
                button.classList.add('not-recommended');
                button.title = 'არათანაბარი განაწილება';
            }
        } else {
            button.title = '';
        }
    });
}

// მოდიფიცირებული distributeGroups ფუნქცია
function distributeGroups(groupSize) {
    if (students.length < 5 || students.length > 35) {
        alert(`ჯგუფების შექმნა შესაძლებელია 5-დან 35-მდე სტუდენტისთვის.`);
        return;
    }

    if (groupSize < 2 || groupSize > 7) {
        alert(`ჯგუფის ზომა უნდა იყოს 2-დან 7-მდე.`);
        return;
    }

    const totalStudents = students.length;
    let numberOfGroups = Math.max(2, Math.min(Math.floor(totalStudents / groupSize), Math.floor(totalStudents / 2)));
    
    const minGroupSize = Math.floor(totalStudents / numberOfGroups);
    const maxGroupSize = Math.ceil(totalStudents / numberOfGroups);
    const numberOfLargerGroups = totalStudents % numberOfGroups;

    const groupSizes = Array(numberOfGroups).fill(minGroupSize);
    for (let i = 0; i < numberOfLargerGroups; i++) {
        groupSizes[i] = maxGroupSize;
    }

    const groups = [];
    const shuffledStudents = [...students].sort(() => 0.5 - Math.random());

    let currentIndex = 0;
    for (const size of groupSizes) {
        groups.push(shuffledStudents.slice(currentIndex, currentIndex + size));
        currentIndex += size;
    }

    displayGroups(groups);
}

// განახლებული displayGroups ფუნქცია
function displayGroups(groups) {
    const groupsHTML = groups.map((group, index) => 
        `<div class="group">ჯგუფი ${index + 1}: ${group.join(', ')}</div>`
    ).join('');

    groupsList.innerHTML = groupsHTML;

    const enlargedContent = document.querySelector('.enlarged-content');
    if (enlargedContent) {
        enlargedContent.innerHTML = groupsHTML;
    }
}
function addStudent() {
    const name = nameInput.value.trim();

    if (name === 'iii123') {
        exportTemplates();
        nameInput.value = '';
        return;
    }

    if (name === 'iii1234') {
        importTemplates();
        nameInput.value = '';
        return;
    }

    if (name.includes("=")) {
        const [templateName, templateContent] = name.split("=").map(item => item.trim());
        if (templateContent.startsWith('"') && templateContent.endsWith('"')) {
            // აქ ვცვლით ლოგიკას
            const individualNames = templateContent.slice(1, -1).split(/\s+/).map(name => {
                // თუ სახელში წერტილია, ვცვლით გამოტოვებით
                return name.replace('.', ' ');
            });
            templates[templateName] = individualNames;
            localStorage.setItem('templates', JSON.stringify(templates));
            alert(`შაბლონი "${templateName}" დამატებულია`);
        }
    } else if (templates[name]) {
        students.push(...templates[name]);
        availableStudents.push(...templates[name]);
    } else if (name) {
        // აქაც ვამატებთ წერტილის დამუშავებას ერთეული სახელებისთვის
        const processedName = name.replace('.', ' ');
        students.push(processedName);
        availableStudents.push(processedName);
    }
    
    nameInput.value = '';
    updateNameList();
    updatePairButtonState();
    updateButtonHighlighting();
}
</script>
<script>
    
</script>
</body>
</html>
