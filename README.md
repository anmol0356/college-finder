<made by anmol singh>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kanpur College Finder - Find Your Perfect College</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
        }

        .watermark {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.95);
            padding: 12px 20px;
            border-radius: 25px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
            cursor: pointer;
            transition: all 0.3s ease;
            z-index: 1000;
            font-weight: 600;
            color: #667eea;
            font-size: 0.9em;
        }

        .watermark:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.3);
            background: #667eea;
            color: white;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px;
            text-align: center;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .form-section {
            padding: 40px;
        }

        .form-group {
            margin-bottom: 25px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #333;
            font-size: 1.1em;
        }

        .form-group input,
        .form-group select,
        .form-group textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 1em;
            transition: all 0.3s ease;
            resize: vertical;
        }

        .form-group input:focus,
        .form-group select:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .submit-btn {
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1.2em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 20px;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
        }

        .compare-btn {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, #28a745 0%, #20c997 100%);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1em;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            margin-bottom: 20px;
        }

        .compare-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(40, 167, 69, 0.3);
        }

        .results {
            padding: 40px;
            display: none;
        }

        .best-selects {
            background: linear-gradient(135deg, #4caf50 0%, #81c784 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin-bottom: 30px;
            text-align: center;
        }

        .best-selects h3 {
            font-size: 1.8em;
            margin-bottom: 15px;
        }

        .best-selects ul {
            list-style: none;
            display: flex;
            justify-content: space-around;
            flex-wrap: wrap;
        }

        .best-selects li {
            background: rgba(255,255,255,0.2);
            padding: 10px 20px;
            border-radius: 10px;
            margin: 5px;
        }

        .college-card {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 30px;
            margin-bottom: 25px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            position: relative;
        }

        .college-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.15);
        }

        .college-checkbox {
            position: absolute;
            top: 15px;
            right: 15px;
        }

        .college-name {
            font-size: 1.8em;
            color: #667eea;
            margin-bottom: 15px;
            font-weight: 700;
            cursor: pointer;
            text-decoration: underline;
        }

        .college-name:hover {
            color: #764ba2;
        }

        .recommended-badge {
            display: inline-block;
            background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-size: 0.9em;
            margin-bottom: 15px;
            font-weight: 600;
        }

        .college-info {
            margin: 20px 0;
        }

        .info-item {
            margin-bottom: 12px;
            line-height: 1.6;
        }

        .info-label {
            font-weight: 600;
            color: #333;
        }

        .yearly-programs-section {
            background: #e3f2fd;
            padding: 20px;
            border-radius: 10px;
            margin: 15px 0;
        }

        .courses-section {
            background: white;
            padding: 20px;
            border-radius: 10px;
            margin: 15px 0;
        }

        .course-tag {
            display: inline-block;
            background: #667eea;
            color: white;
            padding: 6px 12px;
            border-radius: 15px;
            margin: 5px;
            font-size: 0.9em;
        }

        .reviews-section {
            background: #fff3cd;
            padding: 20px;
            border-radius: 10px;
            margin: 15px 0;
        }

        .review {
            margin-bottom: 15px;
            padding: 15px;
            background: white;
            border-radius: 8px;
            border-left: 4px solid #667eea;
        }

        .review-author {
            font-weight: 600;
            color: #667eea;
            margin-bottom: 5px;
        }

        .star-rating {
            color: #ffc107;
            margin-bottom: 8px;
        }

        .highlights {
            background: #e8f5e9;
            padding: 20px;
            border-radius: 10px;
            margin: 15px 0;
        }

        .highlight-item {
            padding: 8px 0;
            display: flex;
            align-items: center;
        }

        .highlight-item:before {
            content: "✓";
            color: #4caf50;
            font-weight: bold;
            margin-right: 10px;
            font-size: 1.2em;
        }

        .admission-section {
            background: #f9f9f9;
            padding: 20px;
            border-radius: 10px;
            margin: 15px 0;
        }

        .admission-section h3 {
            color: #333;
            margin-bottom: 15px;
        }

        .admission-section ul {
            list-style-type: decimal;
            padding-left: 20px;
        }

        .admission-section li {
            margin-bottom: 8px;
            line-height: 1.5;
        }

        .scholarships-section {
            background: linear-gradient(135deg, #ff9800 0%, #ff5722 100%);
            color: white;
            padding: 30px;
            border-radius: 15px;
            margin: 30px 0;
        }

        .scholarships-section h3 {
            font-size: 1.8em;
            margin-bottom: 15px;
        }

        .scholarship-card {
            background: rgba(255,255,255,0.2);
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
        }

        .scholarship-name {
            font-size: 1.2em;
            font-weight: 600;
            margin-bottom: 5px;
        }

        .scholarship-details {
            font-size: 0.9em;
            opacity: 0.9;
        }

        .modal {
            display: none;
            position: fixed;
            z-index: 2000;
            left: 0;
            top: 0;
            width: 100%;
            height: 100%;
            overflow: auto;
            background-color: rgba(0,0,0,0.4);
        }

        .modal-content {
            background-color: #fefefe;
            margin: 5% auto;
            padding: 20px;
            border: none;
            border-radius: 10px;
            width: 90%;
            max-width: 1200px;
            max-height: 80vh;
            overflow-y: auto;
        }

        .close {
            color: #aaa;
            float: right;
            font-size: 28px;
            font-weight: bold;
            cursor: pointer;
        }

        .close:hover {
            color: black;
        }

        .comparison-wrapper {
            overflow-x: auto;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            min-width: 600px;
        }

        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
            white-space: nowrap;
        }

        th {
            background-color: #667eea;
            color: white;
        }

        #feesChart {
            max-width: 400px;
            margin: 20px auto;
        }

        @media (max-width: 768px) {
            body {
                padding: 10px;
            }

            .watermark {
                bottom: 10px;
                right: 10px;
                padding: 8px 15px;
                font-size: 0.8em;
            }

            .header {
                padding: 30px 20px;
            }

            .header h1 {
                font-size: 1.8em;
            }

            .header p {
                font-size: 1em;
            }
            
            .form-section {
                padding: 20px;
            }

            .form-group input,
            .form-group select,
            .form-group textarea {
                padding: 12px;
                font-size: 16px; /* Touch-friendly */
            }

            .submit-btn,
            .compare-btn {
                padding: 15px;
                font-size: 1.1em;
            }

            .results {
                padding: 20px;
            }

            .best-selects {
                padding: 20px;
            }

            .best-selects h3 {
                font-size: 1.4em;
            }

            .best-selects ul {
                flex-direction: column;
                align-items: center;
            }

            .best-selects li {
                width: 100%;
                text-align: center;
                margin: 5px 0;
            }

            .college-card {
                padding: 20px;
                margin-bottom: 20px;
            }

            .college-name {
                font-size: 1.4em;
            }

            .college-checkbox {
                top: 10px;
                right: 10px;
                width: 20px;
                height: 20px;
            }

            .course-tag,
            .scholarship-card {
                font-size: 0.8em;
                padding: 4px 8px;
                margin: 2px;
            }

            .admission-section {
                padding: 15px;
            }

            .admission-section ul {
                padding-left: 15px;
            }

            .scholarships-section {
                padding: 20px;
            }

            .scholarships-section h3 {
                font-size: 1.4em;
            }

            .modal-content {
                width: 95%;
                margin: 10% auto;
                padding: 15px;
            }

            .close {
                font-size: 24px;
            }

            .comparison-wrapper {
                font-size: 0.9em;
            }

            th, td {
                padding: 6px 4px;
            }

            #feesChart {
                max-width: 300px;
            }
        }

        @media (max-width: 480px) {
            .header h1 {
                font-size: 1.5em;
            }

            .college-card {
                padding: 15px;
            }

            .college-name {
                font-size: 1.2em;
            }

            .info-item {
                font-size: 0.9em;
            }

            .reviews-section,
            .highlights,
            .courses-section,
            .yearly-programs-section,
            .admission-section {
                padding: 15px;
            }

            table {
                min-width: 500px;
            }
        }
    </style>
</head>
<body>
    <div class="watermark" onclick="window.open('https://www.instagram.com/rajput_anmolsingh3', '_blank')">
        ANMOL SINGH / IG: rajput_anmolsingh3
    </div>

    <div class="container">
        <div class="header">
            <h1>🎓 Kanpur College Finder</h1>
            <p>Find Your Perfect College & Course Match</p>
        </div>

        <div class="form-section">
            <form id="collegeForm">
                <div class="form-group">
                    <label for="studentName">Your Name</label>
                    <input type="text" id="studentName" required placeholder="Enter your full name">
                </div>

                <div class="form-group">
                    <label for="percentage">Class 12th Percentage</label>
                    <input type="number" id="percentage" min="0" max="100" step="0.01" required placeholder="Enter your percentage (e.g., 85.5)">
                </div>

                <div class="form-group">
                    <label for="interest">Field of Interest</label>
                    <select id="interest" required>
                        <option value="">Select your interest</option>
                        <option value="Engineering">Engineering</option>
                        <option value="Medical">Medical</option>
                        <option value="Management">Management (MBA/BBA)</option>
                        <option value="Commerce">Commerce (B.Com/CA)</option>
                        <option value="Arts">Arts & Humanities</option>
                        <option value="Science">Pure Science</option>
                        <option value="Computer">Computer Applications (BCA/MCA)</option>
                        <option value="Law">Law</option>
                        <option value="Pharmacy">Pharmacy</option>
                        <option value="Architecture">Architecture</option>
                    </select>
                </div>

                <div class="form-group">
                    <label for="specificInterest">Specific Interests (e.g., experiments, college programs, sports, research)</label>
                    <textarea id="specificInterest" rows="3" placeholder="Describe what you're interested in, like lab experiments, annual fests, internships, etc."></textarea>
                </div>

                <button type="submit" class="submit-btn">Find My Perfect College 🚀</button>
            </form>
        </div>

        <div class="results" id="results"></div>
    </div>

    <!-- Comparison Modal -->
    <div id="compareModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <h2>College Comparison</h2>
            <div class="comparison-wrapper">
                <div id="comparisonTable"></div>
            </div>
        </div>
    </div>

    <!-- Fees Chart Modal -->
    <div id="feesModal" class="modal">
        <div class="modal-content">
            <span class="close">&times;</span>
            <h2 id="feesTitle">College Fees Breakdown</h2>
            <canvas id="feesChart"></canvas>
            <p style="text-align: center; margin-top: 10px; font-size: 0.9em; color: #666;">Note: Fees are approximate and may vary. Check official website for latest details.</p>
        </div>
    </div>

    <script>
        const colleges = [
            {
                name: "Flora Institute of Technology",
                minPercentage: 51,
                interests: ["Engineering"],
                specificKeywords: ["experiments", "labs", "workshops"],
                courses: ["B.Tech", "Diploma in Engineering"],
                yearlyPrograms: ["Freshers Party", "Tech Fest", "Annual Sports Day"],
                admissionProcess: [
                    "1. Fill online application form on college website",
                    "2. Submit Class 10th and 12th marksheets",
                    "3. Appear for college entrance test (if required)",
                    "4. Attend counseling session",
                    "5. Pay admission fees to confirm seat"
                ],
                highlights: [
                    "Budget-friendly engineering education",
                    "Basic facilities available",
                    "Focus on core subjects",
                    "Supportive management",
                    "Regular parent-teacher meetings"
                ],
                reviews: [
                    { author: "Suresh Kumar", rating: 2, text: "Average college for engineering. Affordable option." },
                    { author: "Manju Devi", rating: 2, text: "Basic infrastructure. Need better facilities." }
                ]
            },
            {
                name: "Global Institute of Technology & Management",
                minPercentage: 55,
                interests: ["Engineering", "Management"],
                specificKeywords: ["industry interactions", "student clubs", "sports"],
                courses: ["B.Tech", "MBA", "BBA", "M.Tech"],
                yearlyPrograms: ["Management Conclave", "Engineering Expo", "Cultural Night"],
                admissionProcess: [
                    "1. Register on AKTU counseling portal",
                    "2. Upload documents and pay counseling fee",
                    "3. Participate in online counseling rounds",
                    "4. Select preferred branch and college",
                    "5. Report to college for document verification and fee payment"
                ],
                highlights: [
                    "Growing institution",
                    "Modern classrooms",
                    "Industry interaction programs",
                    "Active student clubs",
                    "Sports facilities"
                ],
                reviews: [
                    { author: "Ashish Verma", rating: 3, text: "Decent college with improving infrastructure." },
                    { author: "Priyanka Singh", rating: 3, text: "Good campus environment. Faculty is cooperative." }
                ]
            },
            {
                name: "BBD University Kanpur Campus",
                minPercentage: 56,
                interests: ["Engineering", "Management", "Pharmacy"],
                specificKeywords: ["cultural events", "placement assistance", "labs"],
                courses: ["B.Tech", "MBA", "B.Pharma", "BBA"],
                yearlyPrograms: ["University Fest", "Pharma Symposium", "Placement Drive"],
                admissionProcess: [
                    "1. Apply through university online portal",
                    "2. Submit entrance exam scores (JEE/UPSEE or university test)",
                    "3. Attend group discussion and personal interview (for MBA)",
                    "4. Merit list publication",
                    "5. Fee deposit and admission confirmation"
                ],
                highlights: [
                    "University campus in Kanpur",
                    "Multiple program options",
                    "Good infrastructure",
                    "Regular cultural events",
                    "Placement assistance"
                ],
                reviews: [
                    { author: "Mohit Agarwal", rating: 3, text: "Good university campus. Variety of courses available." },
                    { author: "Seema Mishra", rating: 3, text: "Decent education quality. Campus life is good." }
                ]
            },
            {
                name: "MVN University Kanpur Center",
                minPercentage: 57,
                interests: ["Engineering", "Management"],
                specificKeywords: ["workshops", "industry partnerships", "placements"],
                courses: ["B.Tech", "MBA", "BCA", "MCA"],
                yearlyPrograms: ["Innovation Week", "Leadership Summit", "Tech Hackathon"],
                admissionProcess: [
                    "1. Online application submission",
                    "2. Entrance exam (MVN Entrance Test or equivalent)",
                    "3. Document verification",
                    "4. Seat allotment based on merit",
                    "5. Registration and orientation"
                ],
                highlights: [
                    "Part of MVN education group",
                    "Modern infrastructure",
                    "Industry partnerships",
                    "Regular workshops",
                    "Good placement support"
                ],
                reviews: [
                    { author: "Anuj Sharma", rating: 3, text: "Good college with brand value. Faculty is experienced." },
                    { author: "Ruchi Gupta", rating: 3, text: "Decent college. Placements are satisfactory." }
                ]
            },
            {
                name: "Subharti University Kanpur Extension",
                minPercentage: 58,
                interests: ["Medical", "Engineering", "Pharmacy"],
                specificKeywords: ["clinical exposure", "research", "hospital facilities"],
                courses: ["MBBS", "B.Tech", "B.Pharma", "BDS"],
                yearlyPrograms: ["Medical Conference", "Engineering Seminar", "Health Camp"],
                admissionProcess: [
                    "1. Apply via university website or NEET counseling",
                    "2. Submit NEET scorecard (for medical/pharmacy)",
                    "3. Counseling and seat allocation",
                    "4. Medical fitness certificate submission",
                    "5. Final admission with fee payment"
                ],
                highlights: [
                    "Medical and technical education",
                    "Well-equipped labs",
                    "Experienced faculty",
                    "Hospital facilities",
                    "Research opportunities"
                ],
                reviews: [
                    { author: "Dr. Amit Singh", rating: 4, text: "Good for medical students. Clinical exposure is excellent." },
                    { author: "Shruti Pandey", rating: 3, text: "Decent college with multiple course options." }
                ]
            },
            {
                name: "Noida International University Kanpur Campus",
                minPercentage: 56,
                interests: ["Engineering", "Management", "Law"],
                specificKeywords: ["guest lectures", "international collaborations", "placements"],
                courses: ["B.Tech", "MBA", "LL.B", "BBA"],
                yearlyPrograms: ["Law Moot Court", "Business Fair", "Global Forum"],
                admissionProcess: [
                    "1. Fill application form online",
                    "2. Submit academic transcripts",
                    "3. Entrance test or direct admission based on merit",
                    "4. Interview for management quota",
                    "5. Admission letter and fee submission"
                ],
                highlights: [
                    "Multi-disciplinary university campus",
                    "Modern facilities",
                    "International collaborations",
                    "Regular guest lectures",
                    "Active placement cell"
                ],
                reviews: [
                    { author: "Sanjay Mishra", rating: 3, text: "Good university campus. Variety of courses." },
                    { author: "Neetu Verma", rating: 3, text: "Decent infrastructure. Faculty is supportive." }
                ]
            },
            {
                name: "Amity University Kanpur Campus",
                minPercentage: 65,
                interests: ["Engineering", "Management", "Law", "Arts"],
                specificKeywords: ["international exposure", "industry connections", "placements"],
                courses: ["B.Tech", "MBA", "LL.B", "BA LLB", "BBA", "B.Com"],
                yearlyPrograms: ["Amity Youth Fest", "Career Fair", "Art Exhibition"],
                admissionProcess: [
                    "1. Online application through Amity portal",
                    "2. Selection based on Amity JEE or Class 12 marks",
                    "3. Video response or interview",
                    "4. Merit list and conditional offer",
                    "5. Fee payment and enrollment"
                ],
                highlights: [
                    "Renowned Amity brand",
                    "World-class infrastructure",
                    "International exposure programs",
                    "Strong industry connections",
                    "Excellent placement record"
                ],
                reviews: [
                    { author: "Raghav Khanna", rating: 4, text: "Excellent college with great brand value. Expensive but worth it." },
                    { author: "Aisha Khan", rating: 4, text: "Best infrastructure and faculty. Great campus life." }
                ]
            },
            {
                name: "Bennett University Kanpur Extension",
                minPercentage: 70,
                interests: ["Engineering", "Management", "Computer"],
                specificKeywords: ["media focus", "tech collaborations", "placements"],
                courses: ["B.Tech", "MBA", "BBA", "B.Sc (Hons)"],
                yearlyPrograms: ["Media Conclave", "Tech Summit", "Innovation Challenge"],
                admissionProcess: [
                    "1. Apply online on Bennett website",
                    "2. Submit SAT/JEE scores or Class 12 marks",
                    "3. Online assessment test",
                    "4. Personal interview",
                    "5. Offer letter and deposit"
                ],
                highlights: [
                    "Part of Times of India group",
                    "World-class facilities",
                    "Media and tech focus",
                    "Strong placement support",
                    "International collaborations"
                ],
                reviews: [
                    { author: "Aryan Gupta", rating: 4, text: "Premium college with excellent facilities. Good for tech and media." },
                    { author: "Ishita Sharma", rating: 4, text: "Expensive but provides great exposure and opportunities." }
                ]
            },
            {
                name: "Lovely Professional University Study Center Kanpur",
                minPercentage: 55,
                interests: ["Engineering", "Management", "Commerce", "Arts"],
                specificKeywords: ["flexible learning", "recognized degrees", "support"],
                courses: ["B.Tech", "MBA", "BBA", "B.Com", "BA"],
                yearlyPrograms: ["LPU Fest", "Commerce Meet", "Arts Festival"],
                admissionProcess: [
                    "1. Online registration on LPU portal",
                    "2. LPUNEST entrance exam",
                    "3. Merit-based selection",
                    "4. Document submission",
                    "5. Fee payment and joining"
                ],
                highlights: [
                    "Distance and regular programs",
                    "Affordable education",
                    "Recognized degrees",
                    "Flexible learning options",
                    "Support center facilities"
                ],
                reviews: [
                    { author: "Vishal Tiwari", rating: 3, text: "Good for distance education. LPU brand helps in placements." },
                    { author: "Mamta Agarwal", rating: 3, text: "Affordable option with recognized degrees." }
                ]
            },
            {
                name: "Mangalayatan University Kanpur Campus",
                minPercentage: 54,
                interests: ["Engineering", "Management", "Commerce"],
                specificKeywords: ["skill development", "workshops", "placements"],
                courses: ["B.Tech", "MBA", "BBA", "B.Com"],
                yearlyPrograms: ["Skill Fest", "Business Workshop", "Commerce Day"],
                admissionProcess: [
                    "1. Application form submission",
                    "2. Entrance test (MUEE)",
                    "3. Counseling session",
                    "4. Seat confirmation",
                    "5. Academic documents verification"
                ],
                highlights: [
                    "Growing university campus",
                    "Modern infrastructure",
                    "Focus on skill development",
                    "Regular workshops",
                    "Placement assistance"
                ],
                reviews: [
                    { author: "Karan Verma", rating: 3, text: "Developing university. Infrastructure is improving." },
                    { author: "Nikita Singh", rating: 3, text: "Decent college with potential for growth." }
                ]
            },
            {
                name: "Invertis University Kanpur Extension",
                minPercentage: 56,
                interests: ["Engineering", "Management", "Pharmacy"],
                specificKeywords: ["fests", "student communities", "partnerships"],
                courses: ["B.Tech", "MBA", "B.Pharma", "BCA"],
                yearlyPrograms: ["Cultural Fest", "Pharma Expo", "Management Meet"],
                admissionProcess: [
                    "1. Online or offline application",
                    "2. Submit JEE/UPSEE scores",
                    "3. Merit list preparation",
                    "4. Admission counseling",
                    "5. Fee remittance"
                ],
                highlights: [
                    "Multi-disciplinary university",
                    "Good infrastructure",
                    "Industry partnerships",
                    "Regular fests and events",
                    "Active student communities"
                ],
                reviews: [
                    { author: "Aditya Pandey", rating: 3, text: "Good university with variety of courses. Campus is nice." },
                    { author: "Tanvi Mishra", rating: 3, text: "Decent education quality. Faculty is experienced." }
                ]
            },
            {
                name: "Sharda University Kanpur Campus",
                minPercentage: 62,
                interests: ["Engineering", "Management", "Medical"],
                specificKeywords: ["international exposure", "research", "placements"],
                courses: ["B.Tech", "MBA", "MBBS", "BDS", "B.Pharma"],
                yearlyPrograms: ["Global Summit", "Medical Conference", "Tech Fest"],
                admissionProcess: [
                    "1. Apply through SUAT entrance exam",
                    "2. Or direct admission with Class 12 marks",
                    "3. Group discussion and interview",
                    "4. Allotment letter",
                    "5. Registration process"
                ],
                highlights: [
                    "Renowned university brand",
                    "International exposure",
                    "Modern facilities",
                    "Strong placement record",
                    "Research opportunities"
                ],
                reviews: [
                    { author: "Shubham Agarwal", rating: 4, text: "Premium university with excellent facilities. Good for medical and engineering." },
                    { author: "Aditi Sharma", rating: 4, text: "Expensive but provides world-class education and exposure." }
                ]
            },
            {
                name: "GLA University Kanpur Study Center",
                minPercentage: 60,
                interests: ["Engineering", "Management"],
                specificKeywords: ["workshops", "connections", "placements"],
                courses: ["B.Tech", "MBA", "BCA", "MCA"],
                yearlyPrograms: ["Academic Workshop", "Industry Day", "Placement Week"],
                admissionProcess: [
                    "1. Online application",
                    "2. GLAET entrance test",
                    "3. Merit-based selection",
                    "4. Counseling and seat booking",
                    "5. Document verification"
                ],
                highlights: [
                    "Established university brand",
                    "Good academic reputation",
                    "Industry connections",
                    "Regular workshops",
                    "Placement support"
                ],
                reviews: [
                    { author: "Aman Singh", rating: 3, text: "Good university with strong academics. Faculty is experienced." },
                    { author: "Parul Gupta", rating: 3, text: "Decent college with good placement support." }
                ]
            },
            {
                name: "Teerthanker Mahaveer University Kanpur Campus",
                minPercentage: 58,
                interests: ["Engineering", "Medical", "Management"],
                specificKeywords: ["research facilities", "placements", "labs"],
                courses: ["B.Tech", "MBBS", "MBA", "B.Pharma"],
                yearlyPrograms: ["Research Day", "Medical Fest", "Business Seminar"],
                admissionProcess: [
                    "1. Application via TMU portal",
                    "2. TMU entrance exam or NEET",
                    "3. Merit list",
                    "4. Physical counseling",
                    "5. Admission formalities"
                ],
                highlights: [
                    "Multi-disciplinary university",
                    "Medical and engineering programs",
                    "Good infrastructure",
                    "Research facilities",
                    "Active placement cell"
                ],
                reviews: [
                    { author: "Varun Mishra", rating: 3, text: "Good university with multiple options. Infrastructure is developing." },
                    { author: "Swati Verma", rating: 3, text: "Decent education quality across programs." }
                ]
            },
            {
                name: "IIMT University Kanpur Extension",
                minPercentage: 55,
                interests: ["Engineering", "Management", "Pharmacy"],
                specificKeywords: ["skill programs", "partnerships", "placements"],
                courses: ["B.Tech", "MBA", "B.Pharma", "BCA"],
                yearlyPrograms: ["Skill Development Camp", "Pharma Week", "Tech Meet"],
                admissionProcess: [
                    "1. Fill IIMT application form",
                    "2. Entrance test (IIMT-JEE)",
                    "3. Document submission",
                    "4. Seat allocation",
                    "5. Fee payment"
                ],
                highlights: [
                    "Growing university presence",
                    "Modern labs and facilities",
                    "Industry partnerships",
                    "Regular skill development programs",
                    "Placement assistance"
                ],
                reviews: [
                    { author: "Nikhil Jain", rating: 3, text: "Developing university. Good for engineering students." },
                    { author: "Anjali Mishra", rating: 3, text: "Decent facilities. Faculty is supportive." }
                ]
            },
            {
                name: "Shri Venkateshwara University Kanpur Center",
                minPercentage: 56,
                interests: ["Engineering", "Management", "Commerce"],
                specificKeywords: ["guidance sessions", "flexible options", "support"],
                courses: ["B.Tech", "MBA", "BBA", "B.Com"],
                yearlyPrograms: ["Guidance Seminar", "Commerce Fest", "Engineering Day"],
                admissionProcess: [
                    "1. Online registration",
                    "2. Merit-based on Class 12 marks",
                    "3. Direct admission for eligible candidates",
                    "4. Provisional admission letter",
                    "5. Final verification"
                ],
                highlights: [
                    "University study center",
                    "Flexible learning options",
                    "Recognized degrees",
                    "Support facilities",
                    "Regular guidance sessions"
                ],
                reviews: [
                    { author: "Rohit Pandey", rating: 3, text: "Good for working professionals. Flexible schedules." },
                    { author: "Meena Agarwal", rating: 3, text: "Decent option for distance education with support." }
                ]
            },
            {
                name: "Integral University Kanpur Campus",
                minPercentage: 60,
                interests: ["Engineering", "Management", "Pharmacy"],
                specificKeywords: ["research focus", "infrastructure", "placements"],
                courses: ["B.Tech", "MBA", "B.Pharma", "M.Tech"],
                yearlyPrograms: ["Research Symposium", "Pharma Conference", "Tech Fest"],
                admissionProcess: [
                    "1. Apply online",
                    "2. IUET entrance exam",
                    "3. Result declaration",
                    "4. Counseling",
                    "5. Admission completion"
                ],
                highlights: [
                    "Established university campus",
                    "Good academic reputation",
                    "Modern infrastructure",
                    "Research focus",
                    "Decent placement record"
                ],
                reviews: [
                    { author: "Faisal Khan", rating: 3, text: "Good university with quality education. Faculty is knowledgeable." },
                    { author: "Zara Ahmed", rating: 3, text: "Decent college with focus on academics." }
                ]
            },
            {
                name: "Era University Kanpur Extension",
                minPercentage: 62,
                interests: ["Medical", "Engineering", "Management"],
                specificKeywords: ["clinical exposure", "labs", "faculty"],
                courses: ["MBBS", "BDS", "B.Tech", "MBA", "B.Pharma"],
                yearlyPrograms: ["Clinical Workshop", "Engineering Expo", "Management Summit"],
                admissionProcess: [
                    "1. NEET-based application for medical",
                    "2. Counseling through MCC",
                    "3. Seat allotment",
                    "4. Reporting to college",
                    "5. Document and fee submission"
                ],
                highlights: [
                    "Medical university with tech programs",
                    "Hospital facilities",
                    "Modern labs",
                    "Experienced medical faculty",
                    "Clinical exposure"
                ],
                reviews: [
                    { author: "Dr. Priya Singh", rating: 4, text: "Good for medical students. Clinical training is thorough." },
                    { author: "Akash Verma", rating: 3, text: "Decent university with multiple program options." }
                ]
            },
            {
                name: "Monad University Kanpur Study Center",
                minPercentage: 54,
                interests: ["Engineering", "Management", "Arts"],
                specificKeywords: ["flexible learning", "affordable", "support"],
                courses: ["B.Tech", "MBA", "BBA", "BA", "B.Com"],
                yearlyPrograms: ["Arts Festival", "Management Day", "Engineering Meet"],
                admissionProcess: [
                    "1. Online form filling",
                    "2. Merit list based on qualifying exam",
                    "3. Provisional admission",
                    "4. Original documents check",
                    "5. Fee deposit"
                ],
                highlights: [
                    "University study center",
                    "Multiple program options",
                    "Flexible learning",
                    "Support facilities",
                    "Affordable fees"
                ],
                reviews: [
                    { author: "Sachin Gupta", rating: 3, text: "Good for distance learning. Support center is helpful." },
                    { author: "Kritika Sharma", rating: 3, text: "Decent option for working students." }
                ]
            },
            {
                name: "Wisdom School of Management",
                minPercentage: 58,
                interests: ["Management"],
                specificKeywords: ["corporate visits", "case studies", "development"],
                courses: ["BBA", "MBA", "PGDM"],
                yearlyPrograms: ["Corporate Conclave", "Case Study Competition", "Leadership Camp"],
                admissionProcess: [
                    "1. CAT/MAT score submission",
                    "2. Group discussion",
                    "3. Personal interview",
                    "4. Final selection",
                    "5. Admission confirmation"
                ],
                highlights: [
                    "Management focused institution",
                    "Industry-oriented curriculum",
                    "Regular corporate visits",
                    "Case study methodology",
                    "Personality development focus"
                ],
                reviews: [
                    { author: "Kunal Jain", rating: 3, text: "Good for management students. Faculty has corporate experience." },
                    { author: "Simran Kapoor", rating: 3, text: "Decent management college with practical approach." }
                ]
            },
            {
                name: "Excel Engineering College",
                minPercentage: 52,
                interests: ["Engineering"],
                specificKeywords: ["lab sessions", "workshops", "faculty support"],
                courses: ["B.Tech", "Diploma in Engineering"],
                yearlyPrograms: ["Lab Expo", "Engineering Workshop", "Freshers Meet"],
                admissionProcess: [
                    "1. Direct admission based on Class 12 marks",
                    "2. Management quota application",
                    "3. Document submission",
                    "4. Fee payment",
                    "5. Orientation"
                ],
                highlights: [
                    "Focus on engineering education",
                    "Regular lab sessions",
                    "Workshop facilities",
                    "Affordable fees",
                    "Supportive faculty"
                ],
                reviews: [
                    { author: "Pawan Kumar", rating: 3, text: "Budget engineering college. Good for average students." },
                    { author: "Sunita Mishra", rating: 2, text: "Average infrastructure. Need better facilities." }
                ]
            },
            {
                name: "Kanpur College of Pharmacy",
                minPercentage: 56,
                interests: ["Pharmacy"],
                specificKeywords: ["pharma labs", "industry training", "research"],
                courses: ["B.Pharma", "M.Pharma", "D.Pharma"],
                yearlyPrograms: ["Pharma Fest", "Industry Visit Day", "Research Seminar"],
                admissionProcess: [
                    "1. UPSEE counseling for B.Pharma",
                    "2. Merit list",
                    "3. Seat allocation",
                    "4. Reporting with documents",
                    "5. Admission fee"
                ],
                highlights: [
                    "Specialized pharmacy college",
                    "Well-equipped pharmaceutical labs",
                    "Industry training programs",
                    "Research opportunities",
                    "Placement in pharma companies"
                ],
                reviews: [
                    { author: "Naveen Pandey", rating: 3, text: "Good for pharmacy students. Practical training is emphasized." },
                    { author: "Roshni Verma", rating: 3, text: "Decent pharmacy college with good lab facilities." }
                ]
            },
            {
                name: "Lakshmi Narain College of Technology & Science",
                minPercentage: 54,
                interests: ["Engineering", "Science"],
                specificKeywords: ["science events", "research", "labs"],
                courses: ["B.Tech", "B.Sc", "M.Tech", "M.Sc"],
                yearlyPrograms: ["Science Fair", "Tech Symposium", "Research Day"],
                admissionProcess: [
                    "1. Online application",
                    "2. Entrance exam (LNCTET)",
                    "3. Result and merit list",
                    "4. Counseling",
                    "5. Final admission"
                ],
                highlights: [
                    "Technical and science education",
                    "Good lab facilities",
                    "Research opportunities",
                    "Experienced faculty",
                    "Regular science events"
                ],
                reviews: [
                    { author: "Ashok Yadav", rating: 3, text: "Good for science and engineering. Faculty is supportive." },
                    { author: "Rachna Singh", rating: 3, text: "Decent college with focus on research." }
                ]
            },
            {
                name: "Northern India Engineering College",
                minPercentage: 53,
                interests: ["Engineering"],
                specificKeywords: ["industrial visits", "workshops", "placements"],
                courses: ["B.Tech in CSE", "B.Tech in ME", "B.Tech in Civil", "B.Tech in EE"],
                yearlyPrograms: ["Industrial Tour", "Engineering Fest", "Placement Week"],
                admissionProcess: [
                    "1. AKTU counseling registration",
                    "2. Choice filling",
                    "3. Seat allotment",
                    "4. Upgradation rounds",
                    "5. College reporting"
                ],
                highlights: [
                    "Established engineering college",
                    "Focus on practical knowledge",
                    "Regular industrial visits",
                    "Workshop facilities",
                    "Placement assistance"
                ],
                reviews: [
                    { author: "Sanjiv Kumar", rating: 3, text: "Average engineering college. Faculty tries to help students." },
                    { author: "Pooja Agarwal", rating: 3, text: "Decent option for engineering at affordable cost." }
                ]
            },
            {
                name: "Modern Institute of Technology & Research Centre",
                minPercentage: 55,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["coding workshops", "tech community", "mentorship"],
                courses: ["B.Tech", "M.Tech", "BCA", "MCA"],
                yearlyPrograms: ["Coding Hackathon", "Tech Fest", "Mentor Meet"],
                admissionProcess: [
                    "1. Application form",
                    "2. Direct merit admission",
                    "3. Entrance test for competitive seats",
                    "4. Document verification",
                    "5. Fee submission"
                ],
                highlights: [
                    "Modern infrastructure",
                    "IT focused programs",
                    "Regular coding workshops",
                    "Industry mentorship",
                    "Active tech community"
                ],
                reviews: [
                    { author: "Tarun Gupta", rating: 3, text: "Good for IT students. Labs are well-equipped." },
                    { author: "Neha Rastogi", rating: 3, text: "Decent college with focus on technology." }
                ]
            },
            {
                name: "Maharana Pratap Engineering College",
                minPercentage: 52,
                interests: ["Engineering"],
                specificKeywords: ["practicals", "management support", "core subjects"],
                courses: ["B.Tech", "Diploma in Engineering"],
                yearlyPrograms: ["Practical Lab Day", "Core Subject Seminar", "Annual Meet"],
                admissionProcess: [
                    "1. Online application",
                    "2. Class 12 merit",
                    "3. Management counseling",
                    "4. Seat confirmation",
                    "5. Joining formalities"
                ],
                highlights: [
                    "Budget-friendly engineering education",
                    "Basic facilities",
                    "Focus on core subjects",
                    "Regular practicals",
                    "Supportive management"
                ],
                reviews: [
                    { author: "Dinesh Yadav", rating: 2, text: "Average college for engineering. Affordable option." },
                    { author: "Kamla Devi", rating: 2, text: "Basic infrastructure. Need improvement in facilities." }
                ]
            },
            {
                name: "Institute of Technology & Science (ITS) Kanpur",
                minPercentage: 57,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["tech events", "partnerships", "placements"],
                courses: ["B.Tech", "M.Tech", "BCA", "MCA"],
                yearlyPrograms: ["Tech Event", "Innovation Fair", "Placement Drive"],
                admissionProcess: [
                    "1. UPSEE counseling",
                    "2. Online registration",
                    "3. Choice locking",
                    "4. Allotment and reporting",
                    "5. Fee payment"
                ],
                highlights: [
                    "Technology focused institution",
                    "Modern computer labs",
                    "Regular tech events",
                    "Industry partnerships",
                    "Active placement cell"
                ],
                reviews: [
                    { author: "Anshul Sharma", rating: 3, text: "Good college for CSE and IT. Faculty encourages innovation." },
                    { author: "Isha Mishra", rating: 3, text: "Decent infrastructure. Placements are satisfactory." }
                ]
            },
            {
                name: "Alpine Institute of Technology",
                minPercentage: 53,
                interests: ["Engineering"],
                specificKeywords: ["practical training", "industrial exposure", "affordable"],
                courses: ["B.Tech", "Diploma in Engineering"],
                yearlyPrograms: ["Training Workshop", "Industry Day", "Sports Meet"],
                admissionProcess: [
                    "1. Apply online or offline",
                    "2. Merit list from Class 12",
                    "3. Spot counseling",
                    "4. Admission letter",
                    "5. Documents and fees"
                ],
                highlights: [
                    "Growing engineering institute",
                    "Focus on practical training",
                    "Workshop facilities",
                    "Industrial exposure",
                    "Affordable fees"
                ],
                reviews: [
                    { author: "Vivek Singh", rating: 3, text: "Developing college. Faculty is cooperative." },
                    { author: "Sapna Gupta", rating: 3, text: "Average college with basic facilities." }
                ]
            },
            {
                name: "Future Institute of Engineering & Technology",
                minPercentage: 54,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["tech workshops", "expert sessions", "training"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in ECE", "M.Tech"],
                yearlyPrograms: ["Future Tech Workshop", "Expert Talk", "Placement Training"],
                admissionProcess: [
                    "1. FIET entrance test",
                    "2. Online application",
                    "3. Merit selection",
                    "4. Counseling",
                    "5. Confirmation"
                ],
                highlights: [
                    "Future-ready curriculum",
                    "Modern labs",
                    "Regular tech workshops",
                    "Industry expert sessions",
                    "Placement training"
                ],
                reviews: [
                    { author: "Arun Pandey", rating: 3, text: "Good college with focus on new technologies. Faculty is updated." },
                    { author: "Divya Verma", rating: 3, text: "Decent engineering college. Infrastructure is improving." }
                ]
            },
            {
                name: "Progressive Education Society's College of Engineering",
                minPercentage: 56,
                interests: ["Engineering"],
                specificKeywords: ["industrial training", "quality education", "labs"],
                courses: ["B.Tech", "M.Tech"],
                yearlyPrograms: ["Industrial Training Camp", "Quality Seminar", "Lab Day"],
                admissionProcess: [
                    "1. Application through PEC portal",
                    "2. Entrance exam",
                    "3. Merit list",
                    "4. Seat allotment",
                    "5. Reporting"
                ],
                highlights: [
                    "Established educational society",
                    "Focus on quality education",
                    "Experienced faculty",
                    "Good lab facilities",
                    "Regular industrial training"
                ],
                reviews: [
                    { author: "Ramesh Tiwari", rating: 3, text: "Good engineering college with experienced teachers." },
                    { author: "Usha Singh", rating: 3, text: "Decent college. Management is supportive." }
                ]
            },
            {
                name: "Indian Institute of Technology (IIT) Kanpur",
                minPercentage: 90,
                interests: ["Engineering", "Science", "Computer"],
                specificKeywords: ["research", "experiments", "internships", "global programs"],
                courses: ["B.Tech in CSE", "B.Tech in Mechanical", "B.Tech in Electrical", "B.Tech in Civil", "M.Tech", "PhD Programs"],
                yearlyPrograms: ["Techkriti", "Rendezvous", "Research Symposium"],
                admissionProcess: [
                    "1. Qualify JEE Advanced",
                    "2. Online JoSAA counseling",
                    "3. Choice filling for IIT Kanpur",
                    "4. Seat allotment",
                    "5. Document verification and fee payment"
                ],
                highlights: [
                    "Premier institute with global recognition",
                    "World-class research facilities",
                    "Excellent placement record with top tech companies",
                    "Beautiful 1000+ acre campus",
                    "Strong alumni network including industry leaders"
                ],
                reviews: [
                    { author: "Rahul Sharma", rating: 5, text: "Best engineering college in India. The faculty and research opportunities are unmatched." },
                    { author: "Priya Singh", rating: 5, text: "Life-changing experience. The campus culture and academic rigor prepare you for anything." }
                ]
            },
            {
                name: "Harcourt Butler Technical University (HBTU)",
                minPercentage: 75,
                interests: ["Engineering", "Computer", "Architecture"],
                specificKeywords: ["coding clubs", "tech societies", "placements"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in Mechanical", "B.Arch", "M.Tech", "MBA"],
                yearlyPrograms: ["Coding Fest", "Architecture Expo", "Cultural Fest"],
                admissionProcess: [
                    "1. JEE Main qualification",
                    "2. UPSEE counseling",
                    "3. Choice of HBTU",
                    "4. Seat allocation",
                    "5. Reporting and admission"
                ],
                highlights: [
                    "One of the oldest technical institutions in UP",
                    "Strong industry connections",
                    "Affordable quality education",
                    "Active coding clubs and tech societies",
                    "Good placement opportunities"
                ],
                reviews: [
                    { author: "Amit Kumar", rating: 4, text: "Great college with decent placements. The peer group is very competitive and motivating." },
                    { author: "Neha Gupta", rating: 4, text: "Good infrastructure and experienced faculty. Cultural fests are amazing!" }
                ]
            },
            {
                name: "PSIT (Pranveer Singh Institute of Technology)",
                minPercentage: 60,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["guest lectures", "placement cell", "sports"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in ECE", "B.Tech in Mechanical", "MBA", "MCA"],
                yearlyPrograms: ["Guest Lecture Series", "Sports Day", "Tech Fest"],
                admissionProcess: [
                    "1. UPSEE or direct admission",
                    "2. Online registration",
                    "3. Merit list",
                    "4. Counseling at PSIT",
                    "5. Fee deposit"
                ],
                highlights: [
                    "Modern infrastructure with AC labs",
                    "Industry-oriented curriculum",
                    "Regular guest lectures by industry experts",
                    "Active placement cell",
                    "Sports and cultural facilities"
                ],
                reviews: [
                    { author: "Vikram Yadav", rating: 4, text: "Good college for CSE. Placements are decent with companies like TCS, Wipro visiting regularly." },
                    { author: "Anjali Verma", rating: 3, text: "Infrastructure is good but need more industry exposure programs." }
                ]
            },
            {
                name: "Axis Colleges",
                minPercentage: 55,
                interests: ["Engineering", "Computer", "Management"],
                specificKeywords: ["practical learning", "entrepreneurship", "visits"],
                courses: ["B.Tech in CSE", "B.Tech in ME", "BBA", "MBA", "B.Pharma"],
                yearlyPrograms: ["Entrepreneur Meet", "Practical Lab Day", "Industrial Visit"],
                admissionProcess: [
                    "1. Apply through Axis portal",
                    "2. Entrance test or merit",
                    "3. Personal interview",
                    "4. Offer acceptance",
                    "5. Enrollment"
                ],
                highlights: [
                    "Multi-disciplinary institution",
                    "Focus on practical learning",
                    "Entrepreneurship development programs",
                    "Modern computer labs",
                    "Regular industrial visits"
                ],
                reviews: [
                    { author: "Rohit Malhotra", rating: 3, text: "Decent college for engineering. Faculty is supportive and helpful." },
                    { author: "Shreya Agarwal", rating: 4, text: "Good environment for overall development. Extracurricular activities are encouraged." }
                ]
            },
            {
                name: "AKG Engineering College",
                minPercentage: 58,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["coding culture", "hackathons", "placements"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in ECE", "B.Tech in Civil", "MBA"],
                yearlyPrograms: ["Hackathon", "Coding Competition", "Placement Fair"],
                admissionProcess: [
                    "1. UPSEE registration",
                    "2. Counseling process",
                    "3. Seat selection",
                    "4. Verification",
                    "5. Admission"
                ],
                highlights: [
                    "Well-equipped laboratories",
                    "Experienced faculty from IITs and NITs",
                    "Active coding culture",
                    "Regular hackathons and tech events",
                    "Growing placement record"
                ],
                reviews: [
                    { author: "Manish Tiwari", rating: 4, text: "Great for CSE students. Lots of coding competitions and workshops." },
                    { author: "Pooja Mishra", rating: 3, text: "Good college with improving placements year by year." }
                ]
            },
            {
                name: "Ganesh Shankar Vidyarthi Memorial Medical College (GSVM)",
                minPercentage: 88,
                interests: ["Medical"],
                specificKeywords: ["clinical exposure", "hospital", "PG success"],
                courses: ["MBBS", "MD", "MS", "Diploma Courses"],
                yearlyPrograms: ["Medical Conference", "Clinical Workshop", "Alumni Meet"],
                admissionProcess: [
                    "1. NEET UG qualification",
                    "2. UP NEET counseling",
                    "3. Choice filling for GSVM",
                    "4. Seat allotment",
                    "5. Joining and document check"
                ],
                highlights: [
                    "Government medical college with low fees",
                    "Attached to major teaching hospital",
                    "Excellent clinical exposure",
                    "Experienced medical faculty",
                    "Good PG entrance success rate"
                ],
                reviews: [
                    { author: "Dr. Ankit Pandey", rating: 5, text: "Best medical college in Kanpur. Great patient exposure and learning opportunities." },
                    { author: "Dr. Divya Saxena", rating: 4, text: "Challenging environment that makes you a confident doctor. Hostel life is memorable." }
                ]
            },
            {
                name: "Rama Medical College",
                minPercentage: 75,
                interests: ["Medical"],
                specificKeywords: ["research", "CME programs", "faculty ratio"],
                courses: ["MBBS", "BDS", "B.Sc Nursing", "Paramedical Courses"],
                yearlyPrograms: ["Research Day", "CME Seminar", "Nursing Fest"],
                admissionProcess: [
                    "1. NEET score submission",
                    "2. Direct counseling at Rama",
                    "3. Merit-based selection",
                    "4. Medical exam",
                    "5. Admission"
                ],
                highlights: [
                    "Private medical college with modern facilities",
                    "Well-equipped hospital with 1000+ beds",
                    "Research opportunities available",
                    "Regular CME programs",
                    "Good faculty-student ratio"
                ],
                reviews: [
                    { author: "Kritika Sharma", rating: 4, text: "Good infrastructure and patient variety. Faculty is supportive." },
                    { author: "Varun Gupta", rating: 4, text: "Expensive but worth it for quality medical education." }
                ]
            },
            {
                name: "Institute of Management Studies (IMS) Kanpur",
                minPercentage: 70,
                interests: ["Management"],
                specificKeywords: ["corporate interactions", "case studies", "clubs"],
                courses: ["MBA", "PGDM", "BBA", "Executive MBA"],
                yearlyPrograms: ["Corporate Meet", "Case Study Fest", "Management Club Event"],
                admissionProcess: [
                    "1. CAT/CMAT score",
                    "2. Application form",
                    "3. GD/PI",
                    "4. Final merit list",
                    "5. Fee payment"
                ],
                highlights: [
                    "Strong industry interface",
                    "Regular corporate interactions",
                    "Case study based learning",
                    "Good placement in marketing and finance",
                    "Active management clubs"
                ],
                reviews: [
                    { author: "Saurabh Jain", rating: 4, text: "Great for MBA. Good mix of academics and practical exposure." },
                    { author: "Megha Kapoor", rating: 4, text: "Faculty has industry experience. Placements are satisfactory." }
                ]
            },
            {
                name: "Lloyd Business School",
                minPercentage: 65,
                interests: ["Management"],
                specificKeywords: ["industrial training", "entrepreneurship", "collaborations"],
                courses: ["BBA", "MBA", "PGDM", "B.Com Hons"],
                yearlyPrograms: ["Training Camp", "Entrepreneur Fair", "International Day"],
                admissionProcess: [
                    "1. Online application",
                    "2. Entrance test (LBSAT)",
                    "3. Interview",
                    "4. Selection",
                    "5. Enrollment"
                ],
                highlights: [
                    "Modern campus with AC classrooms",
                    "Focus on personality development",
                    "Regular industrial training",
                    "International collaborations",
                    "Active entrepreneurship cell"
                ],
                reviews: [
                    { author: "Arjun Khanna", rating: 3, text: "Good for BBA. Lots of events and competitions throughout the year." },
                    { author: "Simran Chopra", rating: 4, text: "Faculty is experienced. Practical approach to management education." }
                ]
            },
            {
                name: "Chandra Shekhar Azad University of Agriculture & Technology (CSAUAT)",
                minPercentage: 60,
                interests: ["Commerce", "Management", "Science"],
                specificKeywords: ["agricultural research", "peaceful campus", "placements"],
                courses: ["B.Com", "M.Com", "MBA", "B.Sc Agriculture", "M.Sc"],
                yearlyPrograms: ["Agriculture Fair", "Commerce Seminar", "Science Day"],
                admissionProcess: [
                    "1. ICAR AIEEA or university test",
                    "2. Counseling",
                    "3. Merit list",
                    "4. Seat booking",
                    "5. Joining"
                ],
                highlights: [
                    "Government university with low fees",
                    "Good for commerce students",
                    "Agricultural research opportunities",
                    "Peaceful campus environment",
                    "Decent placement assistance"
                ],
                reviews: [
                    { author: "Naman Agarwal", rating: 3, text: "Good government college for B.Com. Affordable and decent education." },
                    { author: "Ritu Singh", rating: 3, text: "Campus is nice but placements could be better." }
                ]
            },
            {
                name: "DAV College Kanpur",
                minPercentage: 55,
                interests: ["Commerce", "Arts", "Science"],
                specificKeywords: ["NCC", "NSS", "cultural programs"],
                courses: ["B.Com", "B.A.", "B.Sc", "M.Com", "M.A."],
                yearlyPrograms: ["Cultural Program", "NCC Camp", "NSS Drive"],
                admissionProcess: [
                    "1. Online application via CSJM portal",
                    "2. Merit list based on Class 12",
                    "3. Counseling at college",
                    "4. Document verification",
                    "5. Fee payment"
                ],
                highlights: [
                    "Established institution with good reputation",
                    "Affordable fees structure",
                    "Good faculty for commerce",
                    "Active NCC and NSS units",
                    "Regular cultural programs"
                ],
                reviews: [
                    { author: "Gaurav Mishra", rating: 4, text: "One of the best colleges for B.Com in Kanpur. Faculty is very knowledgeable." },
                    { author: "Sakshi Gupta", rating: 4, text: "Great college life. Teachers are supportive and encouraging." }
                ]
            },
            {
                name: "Christ Church College",
                minPercentage: 50,
                interests: ["Commerce", "Arts"],
                specificKeywords: ["debate societies", "literary", "holistic development"],
                courses: ["B.Com", "B.A.", "M.Com", "M.A. in English"],
                yearlyPrograms: ["Debate Competition", "Literary Fest", "Arts Day"],
                admissionProcess: [
                    "1. Application form",
                    "2. Merit admission",
                    "3. Interview for arts",
                    "4. Provisional list",
                    "5. Final admission"
                ],
                highlights: [
                    "Historic institution with legacy",
                    "Focus on holistic development",
                    "Good for arts and commerce",
                    "Active debate and literary societies",
                    "Centrally located campus"
                ],
                reviews: [
                    { author: "Ayush Verma", rating: 3, text: "Good college for arts students. Faculty is experienced." },
                    { author: "Isha Sharma", rating: 3, text: "Nice environment for studies. Need better infrastructure." }
                ]
            },
            {
                name: "Institute of Engineering & Technology (IET) Kanpur",
                minPercentage: 68,
                interests: ["Computer", "Engineering"],
                specificKeywords: ["coding community", "technical training", "placements"],
                courses: ["BCA", "MCA", "B.Tech", "M.Tech"],
                yearlyPrograms: ["Coding Fest", "Tech Training", "Placement Week"],
                admissionProcess: [
                    "1. UPSEE for B.Tech/MCA",
                    "2. Counseling",
                    "3. Seat allotment",
                    "4. Reporting",
                    "5. Verification"
                ],
                highlights: [
                    "Government institute under AKTU",
                    "Low fees with quality education",
                    "Strong technical training",
                    "Active coding community",
                    "Good placement record"
                ],
                reviews: [
                    { author: "Shubham Rai", rating: 4, text: "Best government college for MCA. Great faculty and infrastructure." },
                    { author: "Pallavi Joshi", rating: 4, text: "Excellent for computer science students. Peer learning is great." }
                ]
            },
            {
                name: "Babu Banarasi Das University (BBDU)",
                minPercentage: 55,
                interests: ["Computer", "Engineering", "Management"],
                specificKeywords: ["skill workshops", "alumni network", "IT infrastructure"],
                courses: ["BCA", "MCA", "B.Tech", "MBA", "B.Pharma"],
                yearlyPrograms: ["Skill Workshop", "Alumni Meet", "IT Day"],
                admissionProcess: [
                    "1. Online application",
                    "2. BBDU entrance test",
                    "3. Merit list",
                    "4. Counseling",
                    "5. Admission"
                ],
                highlights: [
                    "Private university with multiple programs",
                    "Modern IT infrastructure",
                    "Industry partnerships",
                    "Regular skill development workshops",
                    "Growing alumni network"
                ],
                reviews: [
                    { author: "Karan Singh", rating: 3, text: "Good for BCA. Faculty is supportive. Need better placements." },
                    { author: "Prachi Agarwal", rating: 3, text: "Decent college with good facilities. Improving every year." }
                ]
            },
            {
                name: "Kanpur University (CSJM University)",
                minPercentage: 50,
                interests: ["Arts", "Commerce", "Science"],
                specificKeywords: ["research opportunities", "wide courses", "affordable"],
                courses: ["B.A.", "M.A.", "B.Com", "M.Com", "B.Sc", "M.Sc", "PhD"],
                yearlyPrograms: ["Arts Seminar", "Commerce Conference", "Science Fest"],
                admissionProcess: [
                    "1. Online registration",
                    "2. Merit-based on Class 12",
                    "3. Departmental counseling",
                    "4. Seat allocation",
                    "5. Fee and documents"
                ],
                highlights: [
                    "Main university of Kanpur",
                    "Wide range of courses",
                    "Affordable government institution",
                    "Strong arts and humanities department",
                    "Research opportunities available"
                ],
                reviews: [
                    { author: "Deepak Kumar", rating: 3, text: "Good for arts students. Many affiliated colleges offer variety." },
                    { author: "Sneha Mishra", rating: 3, text: "Decent university for postgraduate studies in arts." }
                ]
            },
            {
                name: "National Law University (NLU) Kanpur",
                minPercentage: 85,
                interests: ["Law"],
                specificKeywords: ["moot courts", "legal research", "placements"],
                courses: ["B.A. LL.B", "LL.M", "PhD in Law"],
                yearlyPrograms: ["Moot Court Competition", "Legal Research Day", "Law Fest"],
                admissionProcess: [
                    "1. CLAT qualification",
                    "2. AILET counseling",
                    "3. Preference for NLU Kanpur",
                    "4. Seat confirmation",
                    "5. Joining"
                ],
                highlights: [
                    "Premier law institution",
                    "Excellent faculty with judicial experience",
                    "Regular moot court competitions",
                    "Strong legal research culture",
                    "Good placement in law firms and corporates"
                ],
                reviews: [
                    { author: "Aditya Mishra", rating: 5, text: "Best law college in the region. Rigorous training prepares you for legal profession." },
                    { author: "Nikita Singh", rating: 4, text: "Challenging but rewarding. Great exposure to legal field." }
                ]
            },
            {
                name: "IFTM University Kanpur Campus",
                minPercentage: 58,
                interests: ["Pharmacy", "Medical"],
                specificKeywords: ["pharma labs", "industrial training", "research"],
                courses: ["B.Pharma", "M.Pharma", "D.Pharma", "Pharm.D"],
                yearlyPrograms: ["Pharma Research Day", "Medical Training", "Lab Workshop"],
                admissionProcess: [
                    "1. Application form",
                    "2. UPSEE for pharmacy",
                    "3. Counseling",
                    "4. Seat allotment",
                    "5. Admission"
                ],
                highlights: [
                    "Well-equipped pharmaceutical labs",
                    "Industrial training programs",
                    "Research in pharmaceutical sciences",
                    "Good placement in pharma companies",
                    "Modern infrastructure"
                ],
                reviews: [
                    { author: "Vishal Gupta", rating: 4, text: "Great for pharmacy students. Good practical exposure." },
                    { author: "Anjana Sharma", rating: 3, text: "Decent college with improving placements in pharma sector." }
                ]
            },
            {
                name: "JSS Academy of Technical Education",
                minPercentage: 62,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["technical workshops", "student clubs", "connections"],
                courses: ["B.Tech in CSE", "B.Tech in ME", "B.Tech in ECE", "MBA"],
                yearlyPrograms: ["Technical Workshop", "Club Fest", "Industry Connect"],
                admissionProcess: [
                    "1. UPSEE counseling",
                    "2. Registration",
                    "3. Choice filling",
                    "4. Allotment",
                    "5. Reporting"
                ],
                highlights: [
                    "Focus on technical skills",
                    "Modern lab facilities",
                    "Regular technical workshops",
                    "Active student clubs",
                    "Growing industry connections"
                ],
                reviews: [
                    { author: "Rajat Verma", rating: 3, text: "Good college for engineering. Faculty is cooperative." },
                    { author: "Kavya Rastogi", rating: 3, text: "Decent infrastructure. Need more placement drives." }
                ]
            },
            {
                name: "Naraina College of Engineering & Technology",
                minPercentage: 55,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["project exhibitions", "sports", "faculty support"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in Civil", "B.Tech in Mechanical"],
                yearlyPrograms: ["Project Expo", "Sports Day", "Tech Meet"],
                admissionProcess: [
                    "1. Online application",
                    "2. Merit or entrance",
                    "3. Counseling",
                    "4. Seat confirmation",
                    "5. Fee"
                ],
                highlights: [
                    "Affordable engineering education",
                    "Practical approach to learning",
                    "Regular project exhibitions",
                    "Sports facilities available",
                    "Supportive faculty"
                ],
                reviews: [
                    { author: "Mohit Sharma", rating: 3, text: "Good for students with average percentage. Teachers help a lot." },
                    { author: "Riya Gupta", rating: 3, text: "Budget-friendly option with decent education quality." }
                ]
            },
            {
                name: "Sri Ram Swaroop Memorial College",
                minPercentage: 52,
                interests: ["Commerce", "Management"],
                specificKeywords: ["CA coaching", "guest lectures", "academic"],
                courses: ["B.Com", "BBA", "M.Com", "MBA"],
                yearlyPrograms: ["CA Prep Session", "Guest Lecture Series", "Commerce Fest"],
                admissionProcess: [
                    "1. CSJM University portal",
                    "2. Merit list",
                    "3. Counseling",
                    "4. Admission",
                    "5. Registration"
                ],
                highlights: [
                    "Established commerce college",
                    "Focus on accounting and finance",
                    "CA coaching assistance",
                    "Regular guest lectures",
                    "Good academic environment"
                ],
                reviews: [
                    { author: "Aman Saxena", rating: 4, text: "Best for commerce students preparing for CA. Faculty guides well." },
                    { author: "Priyanka Dwivedi", rating: 3, text: "Good college for B.Com. Helps in competitive exam preparation." }
                ]
            },
            {
                name: "Vidya College of Education",
                minPercentage: 50,
                interests: ["Arts", "Commerce"],
                specificKeywords: ["teaching experience", "pedagogy workshops", "affordable"],
                courses: ["B.Ed", "M.Ed", "D.El.Ed"],
                yearlyPrograms: ["Teaching Practice", "Pedagogy Workshop", "Education Day"],
                admissionProcess: [
                    "1. UP B.Ed JEE",
                    "2. Counseling",
                    "3. Seat allotment",
                    "4. Reporting",
                    "5. Documents"
                ],
                highlights: [
                    "Focus on teacher training",
                    "Practical teaching experience",
                    "Good for those wanting teaching career",
                    "Regular workshops on pedagogy",
                    "Affordable fees"
                ],
                reviews: [
                    { author: "Sunita Verma", rating: 4, text: "Excellent for B.Ed students. Teaching practice is well-organized." },
                    { author: "Ramesh Gupta", rating: 4, text: "Great faculty who are experienced teachers themselves." }
                ]
            },
            {
                name: "Government Science College",
                minPercentage: 60,
                interests: ["Science"],
                specificKeywords: ["competitive exams", "science labs", "faculty"],
                courses: ["B.Sc in Physics", "B.Sc in Chemistry", "B.Sc in Maths", "M.Sc"],
                yearlyPrograms: ["Science Competition", "Lab Day", "Exam Prep Camp"],
                admissionProcess: [
                    "1. CSJM merit list",
                    "2. Online application",
                    "3. Counseling",
                    "4. Selection",
                    "5. Admission"
                ],
                highlights: [
                    "Government college with nominal fees",
                    "Good for pure science students",
                    "Well-equipped science labs",
                    "Prepares well for competitive exams",
                    "Experienced science faculty"
                ],
                reviews: [
                    { author: "Abhishek Mishra", rating: 4, text: "Best government college for B.Sc. Great for students preparing for IIT-JAM." },
                    { author: "Swati Singh", rating: 4, text: "Excellent science faculty. Good environment for research-minded students." }
                ]
            },
            {
                name: "Accurate Institute of Management and Technology",
                minPercentage: 58,
                interests: ["Management", "Computer"],
                specificKeywords: ["corporate visits", "personality development", "placements"],
                courses: ["BBA", "BCA", "MBA", "MCA"],
                yearlyPrograms: ["Corporate Visit", "PD Session", "Placement Drive"],
                admissionProcess: [
                    "1. Application",
                    "2. AIMT entrance",
                    "3. GD/PI",
                    "4. Merit",
                    "5. Join"
                ],
                highlights: [
                    "Focus on industry-ready skills",
                    "Regular corporate visits",
                    "Personality development programs",
                    "Modern campus facilities",
                    "Active placement cell"
                ],
                reviews: [
                    { author: "Siddharth Jain", rating: 3, text: "Good for management studies. Events and competitions are regular." },
                    { author: "Tanya Agarwal", rating: 3, text: "Decent college with focus on overall development." }
                ]
            },
            {
                name: "Kamla Nehru Institute of Technology (KNIT)",
                minPercentage: 72,
                interests: ["Engineering", "Architecture"],
                specificKeywords: ["design studios", "workshops", "placements"],
                courses: ["B.Tech", "B.Arch", "M.Tech"],
                yearlyPrograms: ["Design Workshop", "Architecture Fest", "Tech Day"],
                admissionProcess: [
                    "1. UPSEE counseling",
                    "2. JEE Main score",
                    "3. Seat allotment",
                    "4. Reporting",
                    "5. Admission"
                ],
                highlights: [
                    "Government engineering college",
                    "Good for architecture students",
                    "Design studios and workshops",
                    "Experienced architecture faculty",
                    "Decent placement record"
                ],
                reviews: [
                    { author: "Nishant Malhotra", rating: 4, text: "Great for architecture. Good balance of theory and practical work." },
                    { author: "Avni Sharma", rating: 4, text: "Faculty is supportive. Studio culture is very collaborative." }
                ]
            },
            {
                name: "R.V. Northland Institute",
                minPercentage: 55,
                interests: ["Pharmacy", "Engineering", "Management"],
                specificKeywords: ["industrial tie-ups", "guest lectures", "infrastructure"],
                courses: ["B.Pharma", "B.Tech", "MBA", "D.Pharma"],
                yearlyPrograms: ["Tie-up Seminar", "Guest Lecture", "Pharma Day"],
                admissionProcess: [
                    "1. Direct or UPSEE",
                    "2. Application",
                    "3. Merit",
                    "4. Counseling",
                    "5. Fee"
                ],
                highlights: [
                    "Multi-disciplinary institution",
                    "Modern pharmacy labs",
                    "Industrial tie-ups",
                    "Regular guest lectures",
                    "Good infrastructure"
                ],
                reviews: [
                    { author: "Piyush Gupta", rating: 3, text: "Good for pharmacy students. Faculty has industry experience." },
                    { author: "Nidhi Verma", rating: 3, text: "Decent college with focus on practical pharmaceutical training." }
                ]
            },
            {
                name: "Shri Ramswaroop Memorial Group of Colleges",
                minPercentage: 60,
                interests: ["Engineering", "Management", "Pharmacy"],
                specificKeywords: ["cultural fests", "training cell", "sports"],
                courses: ["B.Tech", "MBA", "B.Pharma", "MCA"],
                yearlyPrograms: ["Cultural Fest", "Training Session", "Sports Complex Event"],
                admissionProcess: [
                    "1. SRMC portal application",
                    "2. Entrance test",
                    "3. Merit list",
                    "4. Counseling",
                    "5. Admission"
                ],
                highlights: [
                    "Large campus with multiple departments",
                    "Good infrastructure",
                    "Regular cultural and technical fests",
                    "Active training and placement cell",
                    "Sports complex available"
                ],
                reviews: [
                    { author: "Harsh Pandey", rating: 3, text: "Big college with many facilities. Good campus life." },
                    { author: "Richa Agarwal", rating: 3, text: "Decent college for engineering. Placements are improving." }
                ]
            },
            {
                name: "Sanskriti University",
                minPercentage: 52,
                interests: ["Engineering", "Management", "Arts", "Commerce"],
                specificKeywords: ["skill development", "partnerships", "seminars"],
                courses: ["B.Tech", "BBA", "B.Com", "B.A.", "MBA", "M.Tech"],
                yearlyPrograms: ["Skill Seminar", "Partnership Meet", "Arts Day"],
                admissionProcess: [
                    "1. Online form",
                    "2. Sanskriti University test",
                    "3. Selection",
                    "4. Offer",
                    "5. Join"
                ],
                highlights: [
                    "Private university with multiple programs",
                    "Modern facilities",
                    "Focus on skill development",
                    "Industry partnerships",
                    "Regular workshops and seminars"
                ],
                reviews: [
                    { author: "Akash Tiwari", rating: 3, text: "Good university with variety of courses. Faculty is supportive." },
                    { author: "Pooja Saxena", rating: 3, text: "Developing university with potential. Infrastructure is good." }
                ]
            },
            {
                name: "Radha Govind Engineering College",
                minPercentage: 56,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["coding competitions", "expert sessions", "clubs"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in ECE", "B.Tech in ME"],
                yearlyPrograms: ["Coding Competition", "Expert Session", "Tech Club Meet"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Counseling",
                    "3. Allotment",
                    "4. Reporting",
                    "5. Fee"
                ],
                highlights: [
                    "Focus on technical education",
                    "Regular coding competitions",
                    "Industry expert sessions",
                    "Well-maintained labs",
                    "Active technical clubs"
                ],
                reviews: [
                    { author: "Vinay Kumar", rating: 3, text: "Good for engineering students. Faculty is experienced." },
                    { author: "Shruti Mishra", rating: 3, text: "Decent college with focus on practical learning." }
                ]
            },
            {
                name: "Bundelkhand Institute of Engineering & Technology",
                minPercentage: 54,
                interests: ["Engineering"],
                specificKeywords: ["industrial training", "core branches", "faculty"],
                courses: ["B.Tech in Civil", "B.Tech in Mechanical", "B.Tech in Electrical", "B.Tech in CSE"],
                yearlyPrograms: ["Industrial Training", "Core Branch Seminar", "Engineering Day"],
                admissionProcess: [
                    "1. JEE Main",
                    "2. UPSEE counseling",
                    "3. Choice",
                    "4. Seat",
                    "5. Join"
                ],
                highlights: [
                    "Government aided institution",
                    "Affordable fees structure",
                    "Good for core engineering branches",
                    "Experienced faculty",
                    "Regular industrial training"
                ],
                reviews: [
                    { author: "Rajesh Yadav", rating: 3, text: "Good government college. Strong in mechanical and civil engineering." },
                    { author: "Madhuri Singh", rating: 3, text: "Budget-friendly with decent education quality." }
                ]
            },
            {
                name: "United College of Engineering & Research",
                minPercentage: 53,
                interests: ["Engineering", "Management"],
                specificKeywords: ["personality sessions", "library", "societies"],
                courses: ["B.Tech", "MBA", "Diploma in Engineering"],
                yearlyPrograms: ["PD Session", "Library Week", "Society Event"],
                admissionProcess: [
                    "1. Application",
                    "2. Merit",
                    "3. Counseling",
                    "4. Seat",
                    "5. Admission"
                ],
                highlights: [
                    "Multiple engineering branches",
                    "Focus on employability skills",
                    "Regular personality development sessions",
                    "Good library facilities",
                    "Active student societies"
                ],
                reviews: [
                    { author: "Sunil Gupta", rating: 3, text: "Average college but faculty tries hard to help students." },
                    { author: "Anita Sharma", rating: 3, text: "Decent option for engineering at affordable fees." }
                ]
            },
            {
                name: "Maharishi University of Information Technology",
                minPercentage: 55,
                interests: ["Computer", "Engineering"],
                specificKeywords: ["hackathons", "coding culture", "curriculum"],
                courses: ["B.Tech", "BCA", "MCA", "M.Tech"],
                yearlyPrograms: ["Hackathon", "Coding Camp", "IT Seminar"],
                admissionProcess: [
                    "1. Online",
                    "2. Entrance",
                    "3. Merit",
                    "4. Counseling",
                    "5. Fee"
                ],
                highlights: [
                    "Focus on IT and computer science",
                    "Modern computer labs",
                    "Regular hackathons",
                    "Industry-oriented curriculum",
                    "Coding culture"
                ],
                reviews: [
                    { author: "Deepak Joshi", rating: 3, text: "Good for computer science students. Labs are well-equipped." },
                    { author: "Sapna Verma", rating: 3, text: "Focuses on programming skills. Need better placements." }
                ]
            },
            {
                name: "Galgotias University Kanpur Campus",
                minPercentage: 58,
                interests: ["Engineering", "Management", "Computer"],
                specificKeywords: ["corporate training", "international programs", "connections"],
                courses: ["B.Tech", "BCA", "BBA", "MBA", "M.Tech"],
                yearlyPrograms: ["Corporate Training", "International Day", "Industry Connect"],
                admissionProcess: [
                    "1. GUEE test",
                    "2. Application",
                    "3. Selection",
                    "4. Offer",
                    "5. Enrollment"
                ],
                highlights: [
                    "Part of renowned Galgotias group",
                    "Modern infrastructure",
                    "Good industry connections",
                    "Regular corporate training",
                    "International exposure programs"
                ],
                reviews: [
                    { author: "Vaibhav Singh", rating: 4, text: "Good college with brand value. Placements are satisfactory." },
                    { author: "Neetu Agarwal", rating: 3, text: "Expensive but provides good facilities and exposure." }
                ]
            },
            {
                name: "Shambhunath Institute of Engineering & Technology",
                minPercentage: 52,
                interests: ["Engineering"],
                specificKeywords: ["guest lectures", "workshop facilities", "management"],
                courses: ["B.Tech in CSE", "B.Tech in ME", "B.Tech in Civil", "B.Tech in EE"],
                yearlyPrograms: ["Guest Lecture", "Workshop Day", "Annual Meet"],
                admissionProcess: [
                    "1. Direct admission",
                    "2. Class 12 marks",
                    "3. Application",
                    "4. Verification",
                    "5. Fee"
                ],
                highlights: [
                    "Affordable engineering college",
                    "Focus on fundamental concepts",
                    "Regular guest lectures",
                    "Good workshop facilities",
                    "Supportive management"
                ],
                reviews: [
                    { author: "Praveen Kumar", rating: 3, text: "Budget college with basic facilities. Teachers are helpful." },
                    { author: "Rekha Mishra", rating: 3, text: "Good for students with limited budget. Education quality is decent." }
                ]
            },
            {
                name: "Technocrats Institute of Technology",
                minPercentage: 54,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["technical workshops", "project learning", "robotics"],
                courses: ["B.Tech", "Diploma in Engineering", "M.Tech"],
                yearlyPrograms: ["Technical Workshop", "Project Exhibition", "Robotics Fest"],
                admissionProcess: [
                    "1. TIT entrance",
                    "2. Online",
                    "3. Merit",
                    "4. Counseling",
                    "5. Join"
                ],
                highlights: [
                    "Technical focused institution",
                    "Regular technical workshops",
                    "Project-based learning",
                    "Industry mentorship programs",
                    "Active robotics club"
                ],
                reviews: [
                    { author: "Sanjay Tiwari", rating: 3, text: "Good for technical skills development. Hands-on approach to learning." },
                    { author: "Priyanka Gupta", rating: 3, text: "Decent college with focus on practical knowledge." }
                ]
            },
            {
                name: "Lucknow Christian Degree College (Kanpur Branch)",
                minPercentage: 50,
                interests: ["Arts", "Commerce"],
                specificKeywords: ["cultural activities", "value education", "campus"],
                courses: ["B.A.", "B.Com", "M.A.", "M.Com"],
                yearlyPrograms: ["Cultural Activity", "Value Education Seminar", "Campus Day"],
                admissionProcess: [
                    "1. Merit based",
                    "2. Application",
                    "3. List",
                    "4. Counseling",
                    "5. Admission"
                ],
                highlights: [
                    "Minority institution with inclusive culture",
                    "Focus on value-based education",
                    "Good for arts and commerce",
                    "Regular cultural activities",
                    "Peaceful campus environment"
                ],
                reviews: [
                    { author: "Thomas Jacob", rating: 3, text: "Good college with focus on character building. Faculty is caring." },
                    { author: "Mary Joseph", rating: 3, text: "Nice environment for studies. Teachers are supportive." }
                ]
            },
            {
                name: "Kanpur Institute of Technology & Pharmacy",
                minPercentage: 55,
                interests: ["Pharmacy", "Engineering"],
                specificKeywords: ["industrial visits", "research", "placements"],
                courses: ["B.Pharma", "D.Pharma", "B.Tech", "M.Pharma"],
                yearlyPrograms: ["Industrial Visit", "Research Day", "Pharma Placement"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Counseling",
                    "3. Allotment",
                    "4. Reporting",
                    "5. Fee"
                ],
                highlights: [
                    "Combined tech and pharmacy institute",
                    "Well-equipped pharmaceutical labs",
                    "Regular industrial visits",
                    "Focus on research",
                    "Placement assistance"
                ],
                reviews: [
                    { author: "Rohit Pandey", rating: 3, text: "Good for pharmacy students. Practical training is emphasized." },
                    { author: "Seema Verma", rating: 3, text: "Decent college with good lab facilities." }
                ]
            },
            {
                name: "Vivekananda College of Technology & Management",
                minPercentage: 53,
                interests: ["Engineering", "Management"],
                specificKeywords: ["motivational sessions", "sports", "value programs"],
                courses: ["B.Tech", "BBA", "MBA", "Diploma"],
                yearlyPrograms: ["Motivational Talk", "Sports Event", "Value Program"],
                admissionProcess: [
                    "1. Application",
                    "2. Merit",
                    "3. Interview",
                    "4. Selection",
                    "5. Join"
                ],
                highlights: [
                    "Multi-disciplinary institution",
                    "Focus on holistic development",
                    "Regular motivational sessions",
                    "Sports and cultural activities",
                    "Value education programs"
                ],
                reviews: [
                    { author: "Ankit Dubey", rating: 3, text: "Good college with focus on overall personality. Faculty is supportive." },
                    { author: "Ritu Singh", rating: 3, text: "Decent infrastructure and learning environment." }
                ]
            },
            {
                name: "Buddha Institute of Technology",
                minPercentage: 52,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["lab sessions", "placements", "core subjects"],
                courses: ["B.Tech in CSE", "B.Tech in ECE", "B.Tech in ME", "Diploma"],
                yearlyPrograms: ["Lab Session Day", "Placement Drive", "Core Subject Fest"],
                admissionProcess: [
                    "1. Direct",
                    "2. Class 12",
                    "3. Application",
                    "4. Verification",
                    "5. Fee"
                ],
                highlights: [
                    "Growing engineering institute",
                    "Affordable fee structure",
                    "Focus on core subjects",
                    "Regular lab sessions",
                    "Improving placement record"
                ],
                reviews: [
                    { author: "Manoj Kumar", rating: 3, text: "Budget-friendly engineering college. Education quality is acceptable." },
                    { author: "Sonam Gupta", rating: 2, text: "Average college. Need better infrastructure and placements." }
                ]
            },
            {
                name: "Rajarshi Rananjay Singh College",
                minPercentage: 50,
                interests: ["Arts", "Commerce", "Science"],
                specificKeywords: ["competitive prep", "NSS", "affordable"],
                courses: ["B.A.", "B.Sc", "B.Com", "M.A."],
                yearlyPrograms: ["Competitive Exam Prep", "NSS Camp", "Science Day"],
                admissionProcess: [
                    "1. CSJM portal",
                    "2. Merit",
                    "3. Counseling",
                    "4. Seat",
                    "5. Admission"
                ],
                highlights: [
                    "Affiliated to CSJM University",
                    "Multiple stream options",
                    "Affordable education",
                    "Good for competitive exam preparation",
                    "Active NSS unit"
                ],
                reviews: [
                    { author: "Ajay Verma", rating: 3, text: "Decent college for graduation. Faculty is experienced." },
                    { author: "Geeta Sharma", rating: 3, text: "Good for students looking for affordable education." }
                ]
            },
            {
                name: "Jagran College of Arts, Science & Commerce",
                minPercentage: 52,
                interests: ["Arts", "Commerce", "Science"],
                specificKeywords: ["media courses", "guest lectures", "library"],
                courses: ["B.A.", "B.Com", "B.Sc", "M.A.", "M.Com"],
                yearlyPrograms: ["Media Workshop", "Guest Lecture", "Library Week"],
                admissionProcess: [
                    "1. Online",
                    "2. Merit list",
                    "3. Counseling",
                    "4. Selection",
                    "5. Fee"
                ],
                highlights: [
                    "Part of Jagran media group",
                    "Modern infrastructure",
                    "Media and communication courses",
                    "Regular guest lectures from journalists",
                    "Good library resources"
                ],
                reviews: [
                    { author: "Shivam Singh", rating: 3, text: "Good college especially for mass communication. Faculty from industry." },
                    { author: "Ankita Mishra", rating: 3, text: "Nice college with focus on media education." }
                ]
            },
            {
                name: "IILM Academy of Higher Learning",
                minPercentage: 60,
                interests: ["Management", "Computer"],
                specificKeywords: ["corporate interactions", "personality focus", "collaborations"],
                courses: ["BBA", "BCA", "MBA"],
                yearlyPrograms: ["Corporate Interaction", "PD Camp", "International Seminar"],
                admissionProcess: [
                    "1. IILM test",
                    "2. Application",
                    "3. Interview",
                    "4. Offer",
                    "5. Enrollment"
                ],
                highlights: [
                    "Focus on management education",
                    "Industry-integrated curriculum",
                    "Regular corporate interactions",
                    "Personality development focus",
                    "International collaborations"
                ],
                reviews: [
                    { author: "Vishal Jain", rating: 3, text: "Good for management students. Faculty has corporate experience." },
                    { author: "Prerna Agarwal", rating: 3, text: "Expensive but provides good exposure to corporate world." }
                ]
            },
            {
                name: "Shri Ramswaroop Memorial University",
                minPercentage: 55,
                interests: ["Engineering", "Management", "Law", "Pharmacy"],
                specificKeywords: ["fests", "competitions", "sports"],
                courses: ["B.Tech", "MBA", "B.Pharma", "LL.B", "LL.M"],
                yearlyPrograms: ["University Fest", "Competition Day", "Sports Meet"],
                admissionProcess: [
                    "1. SRMU entrance",
                    "2. Online",
                    "3. Merit",
                    "4. Counseling",
                    "5. Admission"
                ],
                highlights: [
                    "Multi-faculty university",
                    "Large campus with various departments",
                    "Regular fests and competitions",
                    "Sports complex",
                    "Active placement cell"
                ],
                reviews: [
                    { author: "Arun Pandey", rating: 3, text: "Big university with many options. Campus life is good." },
                    { author: "Divya Rastogi", rating: 3, text: "Decent university. Placements vary by department." }
                ]
            },
            {
                name: "Dr. Ambedkar Institute of Technology for Handicapped",
                minPercentage: 50,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["inclusive facilities", "support staff", "barrier-free"],
                courses: ["B.Tech", "Diploma in Engineering", "BCA"],
                yearlyPrograms: ["Inclusive Event", "Support Seminar", "Tech Day"],
                admissionProcess: [
                    "1. Special counseling for handicapped",
                    "2. JEE Main",
                    "3. UPSEE",
                    "4. Allotment",
                    "5. Join"
                ],
                highlights: [
                    "Inclusive education institute",
                    "Special facilities for differently-abled",
                    "Government support",
                    "Barrier-free campus",
                    "Supportive faculty and staff"
                ],
                reviews: [
                    { author: "Ramesh Yadav", rating: 4, text: "Excellent initiative for inclusive education. Very supportive environment." },
                    { author: "Sunita Verma", rating: 4, text: "Great college with focus on empowering differently-abled students." }
                ]
            },
            {
                name: "Truba Institute of Engineering & IT",
                minPercentage: 53,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["coding competitions", "tech clubs", "mentorship"],
                courses: ["B.Tech", "M.Tech", "BCA", "MCA"],
                yearlyPrograms: ["Coding Competition", "Club Meet", "Mentor Session"],
                admissionProcess: [
                    "1. Application",
                    "2. Entrance",
                    "3. Merit",
                    "4. Counseling",
                    "5. Fee"
                ],
                highlights: [
                    "Focus on IT education",
                    "Modern computer infrastructure",
                    "Regular coding competitions",
                    "Industry mentorship",
                    "Active tech clubs"
                ],
                reviews: [
                    { author: "Gaurav Mishra", rating: 3, text: "Good for IT students. Faculty encourages coding culture." },
                    { author: "Neha Gupta", rating: 3, text: "Decent college with focus on technical skills." }
                ]
            },
            {
                name: "Ideal Institute of Management & Technology",
                minPercentage: 54,
                interests: ["Management", "Computer"],
                specificKeywords: ["corporate workshops", "soft skills", "entrepreneurship"],
                courses: ["BBA", "BCA", "MBA", "MCA"],
                yearlyPrograms: ["Workshop Series", "Soft Skills Camp", "Entrepreneur Day"],
                admissionProcess: [
                    "1. Online",
                    "2. Test",
                    "3. Interview",
                    "4. Selection",
                    "5. Admission"
                ],
                highlights: [
                    "Management and IT focused",
                    "Regular corporate workshops",
                    "Soft skills training",
                    "Good library facilities",
                    "Active entrepreneurship cell"
                ],
                reviews: [
                    { author: "Saurabh Jain", rating: 3, text: "Good for BBA and BCA. Faculty is supportive." },
                    { author: "Pallavi Saxena", rating: 3, text: "Decent college with focus on personality development." }
                ]
            },
            {
                name: "Kanpur Institute of Technology",
                minPercentage: 52,
                interests: ["Engineering"],
                specificKeywords: ["lab practicals", "industrial training", "affordable"],
                courses: ["B.Tech in CSE", "B.Tech in ME", "B.Tech in Civil", "B.Tech in EE"],
                yearlyPrograms: ["Lab Practical Day", "Industrial Training", "Engineering Fest"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Counseling",
                    "3. Allotment",
                    "4. Reporting",
                    "5. Fee"
                ],
                highlights: [
                    "Established engineering institute",
                    "Focus on core engineering",
                    "Regular lab practical sessions",
                    "Industrial training programs",
                    "Affordable fees"
                ],
                reviews: [
                    { author: "Ravi Shankar", rating: 3, text: "Budget engineering college. Good for students with limited resources." },
                    { author: "Kiran Verma", rating: 3, text: "Average college with basic facilities. Faculty tries to help." }
                ]
            },
            {
                name: "Saroj Institute of Technology & Management",
                minPercentage: 53,
                interests: ["Engineering", "Management"],
                specificKeywords: ["industry visits", "student clubs", "sports"],
                courses: ["B.Tech", "MBA", "BBA", "Diploma"],
                yearlyPrograms: ["Industry Visit", "Club Event", "Sports Day"],
                admissionProcess: [
                    "1. Application",
                    "2. Merit",
                    "3. Counseling",
                    "4. Seat",
                    "5. Join"
                ],
                highlights: [
                    "Combined technical and management education",
                    "Regular industry visits",
                    "Focus on practical training",
                    "Active student clubs",
                    "Sports facilities"
                ],
                reviews: [
                    { author: "Nitin Gupta", rating: 3, text: "Good college with variety of courses. Campus is decent." },
                    { author: "Pooja Mishra", rating: 3, text: "Average college. Placements could be better." }
                ]
            },
            {
                name: "GNIOT Greater Noida (Kanpur Extension)",
                minPercentage: 57,
                interests: ["Engineering", "Management"],
                specificKeywords: ["technical fests", "partnerships", "placements"],
                courses: ["B.Tech", "MBA", "BCA", "MCA"],
                yearlyPrograms: ["Technical Fest", "Partnership Seminar", "Placement Week"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Online",
                    "3. Choice",
                    "4. Allotment",
                    "5. Reporting"
                ],
                highlights: [
                    "Extension campus of Greater Noida college",
                    "Good infrastructure",
                    "Industry partnerships",
                    "Regular technical fests",
                    "Decent placement support"
                ],
                reviews: [
                    { author: "Abhishek Singh", rating: 3, text: "Good extension campus. Faculty is experienced." },
                    { author: "Swati Agarwal", rating: 3, text: "Decent college with growing reputation." }
                ]
            },
            {
                name: "Azad Institute of Engineering & Technology",
                minPercentage: 51,
                interests: ["Engineering"],
                specificKeywords: ["workshops", "lab facilities", "support"],
                courses: ["B.Tech", "Diploma in Engineering", "M.Tech"],
                yearlyPrograms: ["Workshop Series", "Lab Day", "Faculty Support Session"],
                admissionProcess: [
                    "1. Direct",
                    "2. Marks",
                    "3. Application",
                    "4. Verification",
                    "5. Fee"
                ],
                highlights: [
                    "Affordable technical education",
                    "Focus on fundamental concepts",
                    "Regular workshops",
                    "Good lab facilities for basic branches",
                    "Supportive faculty"
                ],
                reviews: [
                    { author: "Mukesh Yadav", rating: 3, text: "Budget-friendly engineering college. Good for average students." },
                    { author: "Rani Gupta", rating: 2, text: "Average college. Need better placement opportunities." }
                ]
            },
            {
                name: "Krishna Engineering College",
                minPercentage: 54,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["tech events", "coding community", "labs"],
                courses: ["B.Tech in CSE", "B.Tech in IT", "B.Tech in ECE", "B.Tech in ME"],
                yearlyPrograms: ["Tech Event", "Coding Meet", "Lab Workshop"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Counseling",
                    "3. Seat",
                    "4. Report",
                    "5. Admit"
                ],
                highlights: [
                    "Growing engineering institution",
                    "Modern labs",
                    "Regular tech events",
                    "Industry expert sessions",
                    "Active coding community"
                ],
                reviews: [
                    { author: "Sumit Verma", rating: 3, text: "Decent engineering college. Faculty is cooperative." },
                    { author: "Ritu Sharma", rating: 3, text: "Good for CSE students. Labs are well-maintained." }
                ]
            },
            {
                name: "Institute of Professional Studies",
                minPercentage: 55,
                interests: ["Management", "Computer"],
                specificKeywords: ["seminars", "industry connections", "soft skills"],
                courses: ["BBA", "BCA", "MBA", "PGDM"],
                yearlyPrograms: ["Professional Seminar", "Industry Connect", "Soft Skills Camp"],
                admissionProcess: [
                    "1. Application",
                    "2. Test",
                    "3. Interview",
                    "4. Merit",
                    "5. Join"
                ],
                highlights: [
                    "Professional education focus",
                    "Corporate training programs",
                    "Personality development",
                    "Regular seminars",
                    "Industry connections"
                ],
                reviews: [
                    { author: "Manish Jain", rating: 3, text: "Good for management education. Faculty has industry background." },
                    { author: "Sakshi Mishra", rating: 3, text: "Decent college with focus on soft skills." }
                ]
            },
            {
                name: "Rajkiya Engineering College Kanpur",
                minPercentage: 68,
                interests: ["Engineering"],
                specificKeywords: ["competitive prep", "quality education", "affordable"],
                courses: ["B.Tech", "M.Tech"],
                yearlyPrograms: ["Competitive Exam Camp", "Quality Seminar", "Engineering Day"],
                admissionProcess: [
                    "1. JEE Main",
                    "2. UPSEE",
                    "3. Counseling",
                    "4. Allotment",
                    "5. Join"
                ],
                highlights: [
                    "Government engineering college",
                    "Low fees structure",
                    "Quality technical education",
                    "Experienced faculty",
                    "Good for competitive exam preparation"
                ],
                reviews: [
                    { author: "Anil Kumar", rating: 4, text: "Best government engineering college. Very affordable." },
                    { author: "Preeti Singh", rating: 4, text: "Excellent for engineering at government rates. Faculty is knowledgeable." }
                ]
            },
            {
                name: "Arya College of Engineering & IT",
                minPercentage: 52,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["coding sessions", "workshops", "community"],
                courses: ["B.Tech", "BCA", "M.Tech", "MCA"],
                yearlyPrograms: ["Coding Session", "Workshop Day", "Community Meet"],
                admissionProcess: [
                    "1. Direct",
                    "2. Merit",
                    "3. Application",
                    "4. Seat",
                    "5. Fee"
                ],
                highlights: [
                    "IT focused engineering college",
                    "Modern computer labs",
                    "Regular coding sessions",
                    "Technical workshops",
                    "Active student community"
                ],
                reviews: [
                    { author: "Pankaj Gupta", rating: 3, text: "Good for CSE and IT. Faculty encourages practical learning." },
                    { author: "Anjali Verma", rating: 3, text: "Decent college with focus on programming skills." }
                ]
            },
            {
                name: "Shivalik College of Engineering",
                minPercentage: 53,
                interests: ["Engineering"],
                specificKeywords: ["industrial training", "workshop facilities", "placements"],
                courses: ["B.Tech in CSE", "B.Tech in ME", "B.Tech in Civil", "B.Tech in EE"],
                yearlyPrograms: ["Industrial Training", "Workshop Event", "Placement Fair"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Counseling",
                    "3. Allotment",
                    "4. Reporting",
                    "5. Admission"
                ],
                highlights: [
                    "Established engineering college",
                    "Focus on practical knowledge",
                    "Regular industrial training",
                    "Good workshop facilities",
                    "Placement assistance"
                ],
                reviews: [
                    { author: "Deepak Mishra", rating: 3, text: "Average engineering college. Faculty is supportive." },
                    { author: "Kavita Sharma", rating: 3, text: "Decent option for engineering education." }
                ]
            },
            {
                name: "Cambridge Institute of Technology",
                minPercentage: 56,
                interests: ["Engineering", "Computer"],
                specificKeywords: ["tech competitions", "collaborations", "placements"],
                courses: ["B.Tech", "M.Tech", "BCA", "MCA"],
                yearlyPrograms: ["Tech Competition", "Collaboration Seminar", "Placement Week"],
                admissionProcess: [
                    "1. Application",
                    "2. Entrance",
                    "3. Merit",
                    "4. Counseling",
                    "5. Fee"
                ],
                highlights: [
                    "Focus on technical excellence",
                    "Modern infrastructure",
                    "Regular tech competitions",
                    "Industry collaborations",
                    "Active placement cell"
                ],
                reviews: [
                    { author: "Rahul Jain", rating: 3, text: "Good engineering college. Placements are improving." },
                    { author: "Sneha Agarwal", rating: 3, text: "Decent college with good facilities." }
                ]
            },
            {
                name: "Hindustan College of Science & Technology",
                minPercentage: 54,
                interests: ["Engineering", "Science"],
                specificKeywords: ["research opportunities", "science exhibitions", "faculty"],
                courses: ["B.Tech", "B.Sc", "M.Tech", "M.Sc"],
                yearlyPrograms: ["Research Day", "Science Exhibition", "Tech Seminar"],
                admissionProcess: [
                    "1. UPSEE",
                    "2. Online",
                    "3. Choice",
                    "4. Seat",
                    "5. Join"
                ],
                highlights: [
                    "Science and technology institute",
                    "Good lab facilities",
                    "Research opportunities",
                    "Experienced faculty",
                    "Regular science exhibitions"
                ],
                reviews: [
                    { author: "Vikas Yadav", rating: 3, text: "Good for engineering and science. Faculty is knowledgeable." },
                    { author: "Nisha Gupta", rating: 3, text: "Decent college with focus on research." }
                ]
            }
        ];

        const scholarships = [
            {
                name: "UP Scholarship Scheme",
                eligibility: { minPercentage: 50, interests: ["All"], incomeLimit: 200000 },
                amount: "Up to ₹25,000 per year",
                description: "Government scholarship for UP students in higher education. Covers tuition and maintenance.",
                applyLink: "https://scholarship.up.gov.in/"
            },
            {
                name: "Central Sector Scheme of Scholarship",
                eligibility: { minPercentage: 80, interests: ["All"], incomeLimit: 800000 },
                amount: "₹12,000 - ₹20,000 per year",
                description: "Merit-based scholarship for top 20% students in Class 12. For undergraduate studies.",
                applyLink: "https://scholarships.gov.in/"
            },
            {
                name: "Inlaks Shivdasani Foundation Scholarship",
                eligibility: { minPercentage: 70, interests: ["Engineering", "Management", "Arts"], incomeLimit: null },
                amount: "Up to ₹10 lakhs",
                description: "For Indian students pursuing higher studies abroad in specified fields.",
                applyLink: "https://www.inlaksfoundation.org/"
            },
            {
                name: "Kishore Vaigyanik Protsahan Yojana (KVPY)",
                eligibility: { minPercentage: 75, interests: ["Science", "Engineering"], incomeLimit: null },
                amount: "₹5,000 - ₹7,000 monthly + contingency",
                description: "For students interested in research careers in basic sciences.",
                applyLink: "https://kvpy.iisc.ernet.in/main/index.htm"
            },
            {
                name: "Post-Matric Scholarship for SC/ST/OBC",
                eligibility: { minPercentage: 50, interests: ["All"], incomeLimit: 250000 },
                amount: "Full tuition + maintenance",
                description: "For reserved category students pursuing higher education.",
                applyLink: "https://scholarships.gov.in/"
            },
            {
                name: "INSPIRE Scholarship",
                eligibility: { minPercentage: 85, interests: ["Science"], incomeLimit: null },
                amount: "₹80,000 per year",
                description: "For top-performing students in sciences to pursue research.",
                applyLink: "https://www.inspire-dst.gov.in/"
            },
            {
                name: "AICTE Pragati Scholarship",
                eligibility: { minPercentage: 60, interests: ["Engineering"], incomeLimit: 800000 },
                amount: "₹50,000 per year",
                description: "For girl students in technical education.",
                applyLink: "https://www.aicte-india.org/schemes/students-development-schemes/pragati"
            },
            {
                name: "ONGC Scholarship",
                eligibility: { minPercentage: 60, interests: ["Engineering", "Management"], incomeLimit: 200000 },
                amount: "₹48,000 per year",
                description: "Merit-cum-means scholarship for professional courses.",
                applyLink: "https://www.ongcscholar.org/"
            },
            {
                name: "Sitaram Jindal Scholarship",
                eligibility: { minPercentage: 75, interests: ["All"], incomeLimit: 400000 },
                amount: "₹2,500 - ₹5,000 monthly",
                description: "For meritorious students from low-income families.",
                applyLink: "https://www.sitaramjindalfoundation.org/"
            },
            {
                name: "Narotam Sekhsaria Scholarship",
                eligibility: { minPercentage: 70, interests: ["Management", "Engineering"], incomeLimit: null },
                amount: "Up to ₹20 lakhs",
                description: "Interest-free loan scholarship for postgraduate studies.",
                applyLink: "https://www.nsscholarship.net/"
            }
        ];

        let allColleges = []; // To store filtered colleges for comparison
        let feesChart = null; // Global chart instance to destroy on update

        // Calculate total annual fee for each college (approximate, based on minPercentage and index for variation)
        colleges.forEach((college, index) => {
            college.totalAnnualFee = 40000 + (college.minPercentage * 800) + (index * 500); // Example formula for varied fees (INR)
        });

        document.getElementById('collegeForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const name = document.getElementById('studentName').value;
            const percentage = parseFloat(document.getElementById('percentage').value);
            const interest = document.getElementById('interest').value;
            const specificInterest = document.getElementById('specificInterest').value.toLowerCase();
            
            // Filter colleges
            let recommendedColleges = colleges.filter(college => {
                const interestMatch = college.interests.includes(interest);
                let specificMatch = true;
                if (specificInterest) {
                    specificMatch = college.specificKeywords.some(keyword => specificInterest.includes(keyword)) ||
                                    college.highlights.some(h => h.toLowerCase().includes(specificInterest)) ||
                                    college.yearlyPrograms.some(p => p.toLowerCase().includes(specificInterest));
                }
                return college.minPercentage <= percentage && interestMatch && specificMatch;
            });
            
            // Sort by match score
            recommendedColleges.sort((a, b) => calculateMatchScore(b, percentage, interest, specificInterest) - calculateMatchScore(a, percentage, interest, specificInterest));
            
            allColleges = recommendedColleges; // For comparison

            // Filter scholarships
            let recommendedScholarships = scholarships.filter(sch => {
                const percMatch = sch.eligibility.minPercentage <= percentage;
                const interestMatch = sch.eligibility.interests.includes("All") || sch.eligibility.interests.includes(interest);
                return percMatch && interestMatch;
            });

            recommendedScholarships.sort((a, b) => b.eligibility.minPercentage - a.eligibility.minPercentage); // Prioritize higher merit
            
            displayResults(name, recommendedColleges, recommendedScholarships, percentage, interest, specificInterest);
        });

        function displayResults(name, recommendedColleges, recommendedScholarships, percentage, interest, specificInterest) {
            const resultsDiv = document.getElementById('results');
            
            if (recommendedColleges.length === 0) {
                resultsDiv.innerHTML = `
                    <h2>Hello ${name}!</h2>
                    <p style="font-size: 1.2em; color: #666; margin: 20px 0;">
                        Unfortunately, we couldn't find colleges matching your criteria with ${percentage}% in ${interest}. 
                        Please try adjusting your search or consider improving your percentage for better options.
                    </p>
                `;
                resultsDiv.style.display = 'block';
                resultsDiv.scrollIntoView({ behavior: 'smooth' });
                return;
            }
            
            let html = `
                <h2 style="color: #667eea; font-size: 2em; margin-bottom: 20px;">
                    Perfect Matches for ${name}! 🎯
                </h2>
                <p style="font-size: 1.2em; color: #666; margin-bottom: 30px;">
                    Based on your ${percentage}% score and interest in ${interest}${specificInterest ? `, with focus on ${specificInterest}` : ''}, here are the best colleges for you:
                </p>
                
                <div class="best-selects">
                    <h3>🏆 Best Selects for You</h3>
                    <ul id="bestList">
                        ${recommendedColleges.slice(0, 3).map(college => `<li>${college.name}</li>`).join('')}
                    </ul>
                </div>
                
                <button type="button" class="compare-btn" onclick="openComparisonModal()">Compare Selected Colleges</button>
            `;
            
            recommendedColleges.forEach((college, index) => {
                const matchScore = calculateMatchScore(college, percentage, interest, specificInterest);
                html += `
                    <div class="college-card">
                        <input type="checkbox" class="college-checkbox" value="${college.name}" onchange="toggleComparison('${college.name}')">
                        ${index < 3 ? '<div class="recommended-badge">🏆 Top Recommendation</div>' : ''}
                        <div class="college-name" onclick="showFeesChart('${college.name}')">${college.name} 💰</div>
                        
                        <div class="college-info">
                            <div class="info-item">
                                <span class="info-label">Minimum Required:</span> ${college.minPercentage}% (You have ${percentage}%)
                            </div>
                            <div class="info-item">
                                <span class="info-label">Match Score:</span> ${matchScore}%
                            </div>
                            <div class="info-item">
                                <span class="info-label">Approx. Annual Fee:</span> ₹${college.totalAnnualFee.toLocaleString()}
                            </div>
                        </div>
                        
                        <div class="admission-section">
                            <h3>📋 Admission Process</h3>
                            <ul>
                                ${college.admissionProcess.map(step => `<li>${step}</li>`).join('')}
                            </ul>
                        </div>
                        
                        <div class="courses-section">
                            <h3 style="color: #333; margin-bottom: 15px;">📚 Available Courses</h3>
                            ${college.courses.map(course => `<span class="course-tag">${course}</span>`).join('')}
                        </div>
                        
                        <div class="yearly-programs-section">
                            <h3 style="color: #333; margin-bottom: 15px;">📅 Yearly Programs</h3>
                            ${college.yearlyPrograms.map(program => `<span class="course-tag">${program}</span>`).join('')}
                        </div>
                        
                        <div class="highlights">
                            <h3 style="color: #333; margin-bottom: 15px;">✨ Why Choose This College?</h3>
                            ${college.highlights.map(highlight => `<div class="highlight-item">${highlight}</div>`).join('')}
                        </div>
                        
                        <div class="reviews-section">
                            <h3 style="color: #333; margin-bottom: 15px;">💬 Student Reviews</h3>
                            ${college.reviews.map(review => `
                                <div class="review">
                                    <div class="review-author">${review.author}</div>
                                    <div class="star-rating">${'★'.repeat(review.rating)}${'☆'.repeat(5-review.rating)}</div>
                                    <div>${review.text}</div>
                                </div>
                            `).join('')}
                        </div>
                    </div>
                `;
            });

            // Add scholarships section
            let scholarshipsHtml = `
                <div class="scholarships-section">
                    <h3>💰 Recommended Scholarships for You</h3>
                    ${recommendedScholarships.slice(0, 5).map(sch => `
                        <div class="scholarship-card">
                            <div class="scholarship-name">${sch.name}</div>
                            <div class="scholarship-details">
                                Amount: ${sch.amount} | Eligibility: ${sch.eligibility.minPercentage}%+ in ${sch.eligibility.interests.join(', ')}<br>
                                ${sch.description}<br>
                                <a href="${sch.applyLink}" target="_blank" style="color: white; text-decoration: underline;">Apply Now</a>
                            </div>
                        </div>
                    `).join('')}
                    ${recommendedScholarships.length > 5 ? '<p style="text-align: center; margin-top: 10px;">...and more! Check eligibility on official sites.</p>' : ''}
                </div>
            `;

            html += scholarshipsHtml;
            
            resultsDiv.innerHTML = html;
            resultsDiv.style.display = 'block';
            resultsDiv.scrollIntoView({ behavior: 'smooth' });
        }

        function calculateMatchScore(college, percentage, interest, specificInterest) {
            let score = 0;
            score += 40;
            const excess = percentage - college.minPercentage;
            if (excess > 20) score += 30;
            else if (excess > 10) score += 20;
            else if (excess > 5) score += 10;
            else score += 5;
            if (college.interests.includes(interest)) score += 20;
            const avgRating = college.reviews.reduce((acc, r) => acc + r.rating, 0) / college.reviews.length;
            score += Math.floor(avgRating * 2);
            
            // Specific interest bonus
            if (specificInterest) {
                const matches = college.specificKeywords.filter(k => specificInterest.includes(k.toLowerCase())).length +
                                college.highlights.filter(h => h.toLowerCase().includes(specificInterest)).length +
                                college.yearlyPrograms.filter(p => p.toLowerCase().includes(specificInterest)).length;
                score += matches * 5;
            }
            
            return Math.min(score, 100);
        }

        let selectedColleges = [];

        function toggleComparison(collegeName) {
            const index = selectedColleges.indexOf(collegeName);
            if (index > -1) {
                selectedColleges.splice(index, 1);
            } else {
                selectedColleges.push(collegeName);
            }
        }

        function openComparisonModal() {
            if (selectedColleges.length < 2) {
                alert('Please select at least 2 colleges to compare.');
                return;
            }

            const modal = document.getElementById('compareModal');
            const tableDiv = document.getElementById('comparisonTable');
            let tableHtml = '<table><tr><th>Feature</th>';
            selectedColleges.forEach(collegeName => {
                const college = allColleges.find(c => c.name === collegeName);
                tableHtml += `<th>${collegeName}</th>`;
            });
            tableHtml += '</tr>';

            // Compare courses
            tableHtml += '<tr><td>Courses</td>';
            selectedColleges.forEach(collegeName => {
                const college = allColleges.find(c => c.name === collegeName);
                tableHtml += `<td>${college.courses.join(', ')}</td>`;
            });
            tableHtml += '</tr>';

            // Compare highlights
            tableHtml += '<tr><td>Highlights</td>';
            selectedColleges.forEach(collegeName => {
                const college = allColleges.find(c => c.name === collegeName);
                tableHtml += `<td>${college.highlights.slice(0,3).join('<br>')}</td>`;
            });
            tableHtml += '</tr>';

            // Compare yearly programs
            tableHtml += '<tr><td>Yearly Programs</td>';
            selectedColleges.forEach(collegeName => {
                const college = allColleges.find(c => c.name === collegeName);
                tableHtml += `<td>${college.yearlyPrograms.join(', ')}</td>`;
            });
            tableHtml += '</tr>';

            // Compare avg rating
            tableHtml += '<tr><td>Avg Rating</td>';
            selectedColleges.forEach(collegeName => {
                const college = allColleges.find(c => c.name === collegeName);
                const avg = college.reviews.reduce((acc, r) => acc + r.rating, 0) / college.reviews.length;
                tableHtml += `<td>${avg.toFixed(1)}</td>`;
            });
            tableHtml += '</tr>';

            // Compare fees
            tableHtml += '<tr><td>Approx. Annual Fee (INR)</td>';
            selectedColleges.forEach(collegeName => {
                const college = allColleges.find(c => c.name === collegeName);
                tableHtml += `<td>${college.totalAnnualFee.toLocaleString()}</td>`;
            });
            tableHtml += '</tr></table>';

            tableDiv.innerHTML = tableHtml;
            modal.style.display = 'block';
        }

        function showFeesChart(collegeName) {
            const college = colleges.find(c => c.name === collegeName);
            if (!college) return;

            const modal = document.getElementById('feesModal');
            document.getElementById('feesTitle').textContent = `${college.name} - Annual Fee Breakdown (Total: ₹${college.totalAnnualFee.toLocaleString()})`;

            const ctx = document.getElementById('feesChart').getContext('2d');

            // Destroy previous chart if exists
            if (feesChart) {
                feesChart.destroy();
            }

            const total = college.totalAnnualFee;
            const data = {
                labels: ['Tuition (70%)', 'Hostel & Mess (20%)', 'Other Fees (10%)'],
                datasets: [{
                    data: [total * 0.7, total * 0.2, total * 0.1],
                    backgroundColor: [
                        '#667eea',
                        '#764ba2',
                        '#f093fb'
                    ],
                    borderWidth: 1
                }]
            };

            feesChart = new Chart(ctx, {
                type: 'doughnut',
                data: data,
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                        },
                        tooltip: {
                            callbacks: {
                                label: function(context) {
                                    return `${context.label}: ₹${Math.round(context.parsed).toLocaleString()}`;
                                }
                            }
                        }
                    }
                }
            });

            modal.style.display = 'block';
        }

        // Modal close handlers
        window.addEventListener('load', function() {
            // Compare modal close
            const compareCloseBtn = document.querySelector('#compareModal .close');
            if (compareCloseBtn) {
                compareCloseBtn.onclick = function() {
                    document.getElementById('compareModal').style.display = 'none';
                }
            }

            // Fees modal close
            const feesCloseBtn = document.querySelector('#feesModal .close');
            if (feesCloseBtn) {
                feesCloseBtn.onclick = function() {
                    document.getElementById('feesModal').style.display = 'none';
                    if (feesChart) {
                        feesChart.destroy();
                        feesChart = null;
                    }
                }
            }
        });

        // Close modals on outside click
        window.onclick = function(event) {
            const compareModal = document.getElementById('compareModal');
            const feesModal = document.getElementById('feesModal');
            if (event.target == compareModal) {
                compareModal.style.display = 'none';
            }
            if (event.target == feesModal) {
                feesModal.style.display = 'none';
                if (feesChart) {
                    feesChart.destroy();
                    feesChart = null;
                }
            }
        }
    </script>
</body>
</html>
