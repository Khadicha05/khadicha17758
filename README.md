<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Khadicha's University Page</title>
    <style>
        /* CSS Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }

        header {
            background: linear-gradient(to right, #2c3e50, #3498db);
            color: white;
            text-align: center;
            padding: 2rem 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url("/api/placeholder/1200/300") center/cover;
            opacity: 0.1;
            z-index: 0;
        }

        .header-content {
            position: relative;
            z-index: 1;
        }

        h1 {
            font-size: 2.5rem;
            margin-bottom: 0.5rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .subtitle {
            font-style: italic;
            opacity: 0.9;
            font-size: 1.2rem;
        }

        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 2rem;
        }

        .welcome-message {
            text-align: center;
            margin-bottom: 2rem;
            padding: 1rem;
            background-color: white;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }

        .assignment-buttons {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
            gap: 1rem;
            margin-bottom: 2.5rem;
        }

        .assignment-btn {
            background: linear-gradient(135deg, #3498db, #2980b9);
            color: white;
            border: none;
            padding: 1rem;
            border-radius: 8px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            text-align: center;
            box-shadow: 0 3px 6px rgba(0,0,0,0.1);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100px;
            text-decoration: none;
        }

        .assignment-btn:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .assignment-btn:active {
            transform: translateY(-2px);
        }

        .assignment-btn .number {
            font-size: 1.8rem;
            margin-bottom: 0.3rem;
        }

        .assignment-btn .text {
            font-size: 0.9rem;
            opacity: 0.9;
        }

        .active-assignment-btn {
            background: linear-gradient(135deg, #2ecc71, #27ae60);
            position: relative;
        }

        .active-assignment-btn::after {
            content: '✓';
            position: absolute;
            top: 5px;
            right: 5px;
            background-color: rgba(255, 255, 255, 0.2);
            border-radius: 50%;
            width: 20px;
            height: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.8rem;
        }

        .card {
            background-color: white;
            border-radius: 12px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            margin: 2rem auto;
            max-width: 1200px;
            overflow: hidden;
        }

        .card-header {
            background: linear-gradient(to right, #2c3e50, #3498db);
            color: white;
            padding: 1rem 2rem;
            font-size: 1.5rem;
            font-weight: bold;
        }

        .card-body {
            padding: 2rem;
        }

        .assignment-list {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
            margin-top: 1.5rem;
        }

        .assignment-item {
            border-left: 4px solid #ecf0f1;
            transition: all 0.3s ease;
        }

        .assignment-item.active {
            border-left: 4px solid #3498db;
        }

        .assignment-link {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1rem;
            background-color: #f8f9fa;
            color: #2c3e50;
            text-decoration: none;
            font-weight: bold;
            transition: all 0.2s ease;
        }

        .assignment-link:hover {
            background-color: #e8f4fc;
            transform: translateX(5px);
        }

        .assignment-link.uploaded {
            color: #27ae60;
        }

        .assignment-link.uploaded::after {
            content: '✓';
            background-color: rgba(46, 204, 113, 0.2);
            border-radius: 50%;
            width: 24px;
            height: 24px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-left: 1rem;
        }

        .assignment-date {
            color: #7f8c8d;
            font-size: 0.9rem;
            font-weight: normal;
        }

        footer {
            text-align: center;
            margin-top: 3rem;
            padding: 1.5rem;
            background-color: #2c3e50;
            color: white;
            border-top: 5px solid #3498db;
        }

        @media (max-width: 768px) {
            .assignment-buttons {
                grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
            }
            
            .assignment-btn {
                height: 80px;
            }
            
            .assignment-btn .number {
                font-size: 1.5rem;
            }
        }
    </style>
</head>
<body>
    <header>
        <div class="header-content">
            <h1>Khadicha</h1>
            <p class="subtitle">University Assignments Portal</p>
        </div>
    </header>

    <div class="container">
        <div class="welcome-message">
            <p>Welcome to my university assignments page. Click on an assignment button to view the corresponding assignment page.</p>
        </div>
        
        <div class="assignment-buttons" id="assignment-buttons">
            <!-- Assignment buttons will be generated here -->
        </div>
    </div>
 
    <!-- Assignment Collection Section -->
    <div class="card">
        <div class="card-header">Assignment Collection</div>
        <div class="card-body">
            <p>Track your assignment progress throughout the semester</p>
            
            <div class="assignment-list" id="assignment-list">
                <!-- Assignment list items will be generated here -->
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2025 Khadicha - University Assignments Portal</p>
    </footer>

    <script>
        // JavaScript Functionality
        const TOTAL_ASSIGNMENTS = 10;
        
        // Assignment URLs - add your specific URLs here
        const assignmentUrls = {
            1: "#", // Replace with your Assignment 1 URL when available
            2: "#", // Replace with your Assignment 2 URL when available
            3: "#", // Replace with your Assignment 3 URL when available
            4: "#", // Replace with your Assignment 4 URL when available
            5: "#", // Replace with your Assignment 5 URL when available
            6: "#", // Replace with your Assignment 6 URL when available
            7: "#", // Replace with your Assignment 7 URL when available
            8: "#", // Replace with your Assignment 8 URL when available
            9: "#", // Replace with your Assignment 9 URL when available
            10: "https://khadicha05.github.io/assignment9/",
        };
        
        // Assignment due dates
        const assignmentDueDates = {
            1: "Feb 15, 2025",
            2: "Mar 1, 2025",
            3: "Mar 15, 2025",
            4: "Apr 1, 2025",
            5: "Apr 15, 2025",
            6: "May 1, 2025",
            7: "May 15, 2025",
            8: "Jun 1, 2025",
            9: "Jun 15, 2025",
            10: "Jul 1, 2025"
        };
        
        // Completed assignments (assignments with valid URLs)
        const completedAssignments = [10,];
        
        // Initialize assignments
        function initializeAssignments() {
            const buttonsContainer = document.getElementById('assignment-buttons');
            const assignmentListContainer = document.getElementById('assignment-list');
            
            buttonsContainer.innerHTML = '';
            assignmentListContainer.innerHTML = '';
            
            for (let i = 1; i <= TOTAL_ASSIGNMENTS; i++) {
                // Create assignment button
                const button = document.createElement('a');
                button.className = 'assignment-btn';
                button.id = `assignment-btn-${i}`;
                button.href = assignmentUrls[i];
                
                // If URL is a placeholder, prevent default navigation
                if (assignmentUrls[i] === "#") {
                    button.onclick = function(e) {
                        e.preventDefault();
                        alert(`Assignment ${i} is not available yet.`);
                    };
                } else {
                    button.target = "_blank"; // Open in new tab
                }
                
                // Add "active" class for completed assignments
                if (completedAssignments.includes(i)) {
                    button.classList.add('active-assignment-btn');
                }
                
                const numberSpan = document.createElement('span');
                numberSpan.className = 'number';
                numberSpan.textContent = i;
                
                const textSpan = document.createElement('span');
                textSpan.className = 'text';
                textSpan.textContent = `Assignment ${i}`;
                
                button.appendChild(numberSpan);
                button.appendChild(textSpan);
                buttonsContainer.appendChild(button);
                
                // Create assignment list item
                const listItem = document.createElement('div');
                listItem.className = 'assignment-item';
                if (completedAssignments.includes(i)) {
                    listItem.classList.add('active');
                }
                
                const link = document.createElement('a');
                link.className = 'assignment-link';
                link.href = assignmentUrls[i];
                
                if (assignmentUrls[i] !== "#") {
                    link.classList.add('uploaded');
                    link.target = "_blank"; // Open in new tab
                } else {
                    link.onclick = function(e) {
                        e.preventDefault();
                        alert(`Assignment ${i} is not available yet.`);
                    };
                }
                
                link.textContent = `Assignment ${i}`;
                
                const dateSpan = document.createElement('span');
                dateSpan.className = 'assignment-date';
                dateSpan.textContent = `Due: ${assignmentDueDates[i]}`;
                
                link.appendChild(dateSpan);
                listItem.appendChild(link);
                assignmentListContainer.appendChild(listItem);
            }
        }
        
        // Initialize on page load
        window.onload = function() {
            initializeAssignments();
        };
    </script>
</body>
</html>
