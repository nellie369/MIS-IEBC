# MIS-IEBC
Muthangari International School Voting Management System is a web-based platform designed to facilitate secure, transparent, and efficient voting processes within the school. This system allows students and staff to participate in elections digitally, streamlining vote casting, counting, and result display
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MUTHANGARI INTERNATIONAL SCHOOL VOTING SYSTEM</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            background-color: #81c784; /* Green background */
            padding: 20px;
        }

        .container {
            background-color: white;
            border-radius: 8px;
            padding: 20px;
            max-width: 600px;
            margin: 0 auto;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
        }

        h1 {
            text-align: center;
            margin-bottom: 20px;
            color: #2c6e49; /* Dark green color for the title */
        }

        h2 {
            color: #333;
            margin-bottom: 10px;
        }

        h3 {
            color: #555;
        }

        label {
            display: block;
            margin-bottom: 10px;
            font-weight: bold;
        }

        input[type="text"], input[type="number"], select, button {
            width: 100%;
            padding: 8px;
            margin-bottom: 20px;
            border-radius: 5px;
            border: 1px solid #ccc;
        }

        .candidate, .classRep {
            background-color: #f9f9f9;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
        }

        ul {
            list-style-type: none;
        }

        li {
            padding: 5px 0;
        }

        .admin {
            margin-top: 40px;
        }

        .admin-table {
            width: 100%;
            margin-top: 20px;
            border-collapse: collapse;
        }

        .admin-table, .admin-table th, .admin-table td {
            border: 1px solid #ccc;
        }

        .admin-table th, .admin-table td {
            padding: 10px;
            text-align: center;
        }

        .admin-table th {
            background-color: #f0f0f0;
        }

    </style>
</head>
<body>
    <div class="container">
        <h1>MUTHANGARI INTERNATIONAL SCHOOL VOTING SYSTEM</h1>

        <!-- Voter Details Form -->
        <div id="voterDetails">
            <h2>Enter Voter's Details</h2>
            <label for="firstName">First Name:</label>
            <input type="text" id="firstName" placeholder="Enter First Name" required>

            <label for="lastName">Surname:</label>
            <input type="text" id="lastName" placeholder="Enter Surname" required>

            <label for="admissionNumber">Admission Number:</label>
            <input type="number" id="admissionNumber" placeholder="Enter Admission Number" required>

            <button id="startVoting">Start Voting</button>
        </div>

        <!-- Class selection dropdown -->
        <div id="votingPage" style="display: none;">
            <label for="classSelect">Select your class:</label>
            <select id="classSelect">
                <option value="">Choose Class</option>
                <option value="class1">Year 1</option>
                <option value="class2">Year 2</option>
                <option value="class3">Year 3</option>
                <option value="class4">Year 4</option>
                <option value="class5">Year 5</option>
                <option value="class6">Year 6</option>
                <option value="class7">Year 7</option>
                <option value="class8">Year 8</option>
                <option value="class9">Year 9</option>
                <option value="class10">Year 10</option>
                <option value="class11">Year 11</option>
            </select>

            <div id="schoolCandidates">
                <h2>School-Wide Candidates</h2>
                <div class="candidate">
                    <h3>School President</h3>
                    <ul>
                        <li>
                            <input type="radio" name="president" value="John Doe"> John Doe
                        </li>
                        <li>
                            <input type="radio" name="president" value="Jane Smith"> Jane Smith
                        </li>
                    </ul>
                </div>
                <div class="candidate">
                    <h3>Deputy President</h3>
                    <ul>
                        <li>
                            <input type="radio" name="deputyPresident" value="Sarah Brown"> Sarah Brown
                        </li>
                        <li>
                            <input type="radio" name="deputyPresident" value="Michael Green"> Michael Green
                        </li>
                    </ul>
                </div>
                <div class="candidate">
                    <h3>Games Captain</h3>
                    <ul>
                        <li>
                            <input type="radio" name="gamesCaptain" value="Mark Lee"> Mark Lee
                        </li>
                        <li>
                            <input type="radio" name="gamesCaptain" value="Lisa White"> Lisa White
                        </li>
                    </ul>
                </div>
                <div class="candidate">
                    <h3>Deputy Games Captain</h3>
                    <ul>
                        <li>
                            <input type="radio" name="deputyGamesCaptain" value="Tony Harris"> Tony Harris
                        </li>
                        <li>
                            <input type="radio" name="deputyGamesCaptain" value="Emma Clark"> Emma Clark
                        </li>
                    </ul>
                </div>
            </div>

            <!-- Class-specific candidates -->
            <div id="classCandidates" style="display: none;">
                <h2>Class Representatives</h2>
                <div id="classRep" class="classRep">
                    <!-- Class representatives will be added dynamically based on the selected class -->
                </div>
            </div>

            <!-- Vote Button -->
            <button id="voteBtn">Submit Vote</button>
        </div>
    </div>

    <!-- Admin Page -->
    <div class="admin" id="adminPage" style="display: none;">
        <h2>Admin - Voting Results</h2>

        <!-- School-wide vote results -->
        <div>
            <h3>School-wide Votes</h3>
            <h4>School President</h4>
            <table class="admin-table">
                <thead>
                    <tr>
                        <th>Candidate</th>
                        <th>Votes</th>
                        <th>Percentage</th>
                    </tr>
                </thead>
                <tbody id="presidentResults">
                    <!-- Results will be inserted here -->
                </tbody>
            </table>

            <h4>Deputy President</h4>
            <table class="admin-table">
                <thead>
                    <tr>
                        <th>Candidate</th>
                        <th>Votes</th>
                        <th>Percentage</th>
                    </tr>
                </thead>
                <tbody id="deputyPresidentResults">
                    <!-- Results will be inserted here -->
                </tbody>
            </table>

            <h4>Games Captain</h4>
            <table class="admin-table">
                <thead>
                    <tr>
                        <th>Candidate</th>
                        <th>Votes</th>
                        <th>Percentage</th>
                    </tr>
                </thead>
                <tbody id="gamesCaptainResults">
                    <!-- Results will be inserted here -->
                </tbody>
            </table>

            <h4>Deputy Games Captain</h4>
            <table class="admin-table">
                <thead>
                    <tr>
                        <th>Candidate</th>
                        <th>Votes</th>
                        <th>Percentage</th>
                    </tr>
                </thead>
                <tbody id="deputyGamesCaptainResults">
                    <!-- Results will be inserted here -->
                </tbody>
            </table>
        </div>

        <!-- Class Representatives Results -->
        <div>
            <h3>Class Representatives Votes</h3>
            <table class="admin-table">
                <thead>
                    <tr>
                        <th>Class</th>
                        <th>Candidate</th>
                        <th>Votes</th>
                        <th>Percentage</th>
                    </tr>
                </thead>
                <tbody id="classRepResults">
                    <!-- Results will be inserted here -->
                </tbody>
            </table>
        </div>
    </div>

    <script>
        // Initialize vote counts and students per class (simulated)
        const votes = {
            president: { "John Doe": 0, "Jane Smith": 0 },
            deputyPresident: { "Sarah Brown": 0, "Michael Green": 0 },
            gamesCaptain: { "Mark Lee": 0, "Lisa White": 0 },
            deputyGamesCaptain: { "Tony Harris": 0, "Emma Clark": 0 },
            classRep: {
                class1: { "Anna White": 0, "Tom Green": 0 },
                class2: { "Lucy Brown": 0, "Jake Blue": 0 },
                class3: { "Oliver Black": 0, "Ella Green": 0 },
                class4: { "Lily Martin": 0, "Adam Black": 0 },
                class5: { "Sophia Clark": 0, "James Gray": 0 },
                class6: { "Mia Turner": 0, "Ethan Harris": 0 },
                class7: { "Chloe Williams": 0, "Luke White": 0 },
                class8: { "Nina Brown": 0, "Jack Black": 0 },
                class9: { "Olivia Gray": 0, "Leo Martin": 0 },
                class10: { "Amelia Smith": 0, "Liam White": 0 },
                class11: { "Grace Green": 0, "Noah Black": 0 },
            }
        };

        const studentsPerClass = {
            class1: 25, // Year 1
            class2: 26, // Year 2
            class3: 28, // Year 3
            class4: 30, // Year 4
            class5: 32, // Year 5
            class6: 29, // Year 6
            class7: 33, // Year 7
            class8: 35, // Year 8
            class9: 30, // Year 9
            class10: 32, // Year 10
            class11: 28, // Year 11
        };

        const classSelect = document.getElementById('classSelect');
        const voteBtn = document.getElementById('voteBtn');
        const startVotingBtn = document.getElementById('startVoting');
        const votingPage = document.getElementById('votingPage');
        const adminPage = document.getElementById('adminPage');
        const presidentResults = document.getElementById('presidentResults');
        const deputyPresidentResults = document.getElementById('deputyPresidentResults');
        const gamesCaptainResults = document.getElementById('gamesCaptainResults');
        const deputyGamesCaptainResults = document.getElementById('deputyGamesCaptainResults');
        const classRepResults = document.getElementById('classRepResults');
        const classRepDiv = document.getElementById('classRep');

        // Handle voter details
        startVotingBtn.addEventListener('click', function () {
            const firstName = document.getElementById('firstName').value;
            const lastName = document.getElementById('lastName').value;
            const admissionNumber = document.getElementById('admissionNumber').value;

            if (firstName && lastName && admissionNumber) {
                localStorage.setItem('voter', JSON.stringify({ firstName, lastName, admissionNumber }));
                document.getElementById('voterDetails').style.display = 'none';
                votingPage.style.display = 'block';
            } else {
                alert('Please fill in all fields');
            }
        });

        // Handle class selection and display class representatives
        classSelect.addEventListener('change', function () {
            const selectedClass = classSelect.value;
            if (selectedClass) {
                const classReps = votes.classRep[selectedClass];
                let classRepHtml = '<h3>Class Representatives</h3><ul>';
                for (const [name] of Object.entries(classReps)) {
                    classRepHtml += `
                        <li>
                            <input type="radio" name="classRep" value="${name}"> ${name}
                        </li>
                    `;
                }
                classRepHtml += '</ul>';
                classRepDiv.innerHTML = classRepHtml;
                document.getElementById('classCandidates').style.display = 'block';
            } else {
                document.getElementById('classCandidates').style.display = 'none';
            }
        });

        // Handle voting
        voteBtn.addEventListener('click', function () {
            const selectedPresident = document.querySelector('input[name="president"]:checked');
            const selectedDeputyPresident = document.querySelector('input[name="deputyPresident"]:checked');
            const selectedGamesCaptain = document.querySelector('input[name="gamesCaptain"]:checked');
            const selectedDeputyGamesCaptain = document.querySelector('input[name="deputyGamesCaptain"]:checked');
            const selectedClassRep = document.querySelector('input[name="classRep"]:checked');
            
            if (selectedPresident) votes.president[selectedPresident.value]++;
            if (selectedDeputyPresident) votes.deputyPresident[selectedDeputyPresident.value]++;
            if (selectedGamesCaptain) votes.gamesCaptain[selectedGamesCaptain.value]++;
            if (selectedDeputyGamesCaptain) votes.deputyGamesCaptain[selectedDeputyGamesCaptain.value]++;
            if (selectedClassRep) votes.classRep[classSelect.value][selectedClassRep.value]++;
            
            alert('Vote submitted successfully!');
            document.getElementById('votingPage').style.display = 'none';
            adminPage.style.display = 'block';
            displayResults();
        });

        // Display the results
        function displayResults() {
            let presidentHtml = '';
            for (const candidate in votes.president) {
                const voteCount = votes.president[candidate];
                const totalVotes = studentsPerClass['class1']; // Use the first class for total votes
                const percentage = totalVotes ? ((voteCount / totalVotes) * 100).toFixed(2) : 0;
                presidentHtml += `
                    <tr>
                        <td>${candidate}</td>
                        <td>${voteCount}</td>
                        <td>${percentage}%</td>
                    </tr>
                `;
            }

            // Similarly, display other results like deputy president, games captain, etc.
            presidentResults.innerHTML = presidentHtml;
        }
    </script>
</body>
</html>
