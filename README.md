<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نتائج الامتحانات</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            direction: rtl;
            background-color: #007bff;
            text-align: center;
        }
        .container {
            max-width: 800px;
            margin: 20px auto;
            padding: 20px;
            background-color: #fff;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            background-color: #007bff;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            margin-top: 20px;
            padding: 10px;
            background-color: #f4f4f4;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
        }
        th, td {
            padding: 8px;
            border: 1px solid #ccc;
            text-align: center;
            font-size: 0.9em;
        }
        th {
            background-color: #007bff;
            color: #fff;
        }
        .average-box {
            margin-top: 20px;
            padding: 10px;
            background-color: #e9ecef;
            border: 1px solid #ccc;
            border-radius: 5px;
            display: inline-block;
        }
    </style>
</head>
<body>
    <div class="container">
        <header style="margin-bottom: 20px;">
            <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Flag_of_Libya.svg" alt="Logo" style="width: 100px; margin-bottom: 10px;">
            <h1 style="margin: 0;">دولة ليبيا</h1>
            <h2 style="margin: 0;">حكومة الوحدة الوطنية</h2>
            <h3 style="margin: 0;">وزارة التربية والتعليم</h3>
        </header>
        <main>
            <h2>نتائج امتحانات شهادة إتمام مرحلة التعليم الأساسي والثانوي للعام الدراسي 2023 / 2024</h2>
            <form id="results-form" onsubmit="showResults(event)">
                <div style="margin: 10px 0;">
                    <label for="student-number">رقم الجلوس</label>
                    <input type="text" id="student-number" name="student-number" style="width: 80%; padding: 10px; margin-top: 5px; border: 1px solid #ccc; border-radius: 5px;">
                </div>
                <button type="submit">عرض الدرجات</button>
            </form>
            <div id="result" class="result" style="display: none;"></div>
            <div id="average-box" class="average-box" style="display: none;"></div>
            <button onclick="window.location.reload();">إعادة تحميل الصفحة</button>
        </main>
        <footer style="margin-top: 20px;">
            <p>تنفيذ عمر فوزي عمر الحاج لنظم المعلومات | جميع الحقوق محفوظة 2010-2024</p>
        </footer>
    </div>
    <script>
        function showResults(event) {
            event.preventDefault();
            const studentNumber = document.getElementById('student-number').value;
            const results = {
                '12345': {
                    'name': 'عمر فوزي',
                    'subjects': [
                        { 'subject': 'الرياضيات', 'score': '56/55', 'status': 'ناجح', 'average': '80', 'exam': '40', 'work': '40' },
                        { 'subject': 'اللغة العربية', 'score': '56/54', 'status': 'ناجح', 'average': '75', 'exam': '35', 'work': '40' },
                        { 'subject': 'اللغة الإنجليزية', 'score': '56/53', 'status': 'ناجح', 'average': '70', 'exam': '30', 'work': '40' },
                        { 'subject': 'العلوم', 'score': '56/52', 'status': 'ناجح', 'average': '65', 'exam': '25', 'work': '40' },
                        { 'subject': 'التاريخ', 'score': '56/51', 'status': 'ناجح', 'average': '60', 'exam': '20', 'work': '40' }
                        // يمكن إضافة المزيد من المواد هنا
                    ]
                },
                '23456': {
                    'name': 'محمد سعيد',
                    'subjects': [
                        { 'subject': 'الرياضيات', 'score': '56/50', 'status': 'ناجح', 'average': '85', 'exam': '45', 'work': '40' },
                        { 'subject': 'اللغة العربية', 'score': '56/48', 'status': 'ناجح', 'average': '80', 'exam': '40', 'work': '40' },
                        // يمكن إضافة المزيد من المواد هنا
                    ]
                },
                '34567': {
                    'name': 'علي محمود',
                    'subjects': [
                        { 'subject': 'الرياضيات', 'score': '56/52', 'status': 'ناجح', 'average': '75', 'exam': '35', 'work': '40' },
                        { 'subject': 'اللغة العربية', 'score': '56/49', 'status': 'ناجح', 'average': '70', 'exam': '30', 'work': '40' },
                        // يمكن إضافة المزيد من المواد هنا
                    ]
                },
                '45678': {
                    'name': 'سامي يوسف',
                    'subjects': [
                        { 'subject': 'الرياضيات', 'score': '56/30', 'status': 'راسب', 'average': '50', 'exam': '10', 'work': '40' },
                        { 'subject': 'اللغة العربية', 'score': '56/20', 'status': 'راسب', 'average': '40', 'exam': '0', 'work': '40' },
                        // يمكن إضافة المزيد من المواد هنا
                    ]
                }
            };
            const resultDiv = document.getElementById('result');
            const averageBox = document.getElementById('average-box');
            if (results[studentNumber]) {
                const student = results[studentNumber];
                let resultHTML = `<h3>الاسم: ${student.name}</h3>`;
                resultHTML += `<table>`;
                resultHTML += `<tr><th>المادة</th><th>الدرجة</th><th>الحالة</th><th>المعدل</th><th>الامتحان</th><th>الأعمال</th></tr>`;
                let totalScore = 0;
                let totalMaxScore = 0;
                student.subjects.forEach(subject => {
                    const [maxScore, score] = subject.score.split('/').map(Number);
                    totalScore += score;
                    totalMaxScore += maxScore;
                    resultHTML += `<tr><td>${subject.subject}</td><td>${subject.score}</td><td>${subject.status}</td><td>${subject.average}</td><td>${subject.exam}</td><td>${subject.work}</td></tr>`;
                });
                resultHTML += `</table>`;
                const average = (totalScore / totalMaxScore * 100).toFixed(2);
                averageBox.textContent = `المعدل: ${average}%`;
                averageBox.style.display = 'block';
                resultDiv.innerHTML = resultHTML;
                resultDiv.style.display = 'block';
            } else {
                resultDiv.textContent = 'رقم الجلوس غير موجود';
                resultDiv.style.display = 'block';
                averageBox.style.display = 'none';
            }
        }
    </script>
</body>
</html>
