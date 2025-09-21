# resumecode
newrepo
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Resume Relevance Checker</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <div class="container">
    <h2>Resume Relevance Checker</h2>

    <form id="resumeForm">
      <label for="resume">Paste Resume Text:</label>
      <textarea id="resume" name="resume" placeholder="Copy-paste your resume text here..." required></textarea><br>

      <label for="keywords">Enter Job Description Keywords (comma separated):</label>
      <textarea id="keywords" name="keywords" placeholder="e.g. Python, JavaScript, HTML" required></textarea><br>

      <button type="submit">Check Relevance</button>
    </form>

    <div id="result"></div>
  </div>

  <script>
    document.getElementById("resumeForm").addEventListener("submit", function(e) {
      e.preventDefault();

      let resumeText = document.getElementById("resume").value.toLowerCase();
      let jdKeywords = document.getElementById("keywords").value.toLowerCase().split(",");

      let matched = [];
      jdKeywords.forEach(keyword => {
        let kw = keyword.trim();
        if (kw && resumeText.includes(kw)) {
          matched.push(kw);
        }
      });

      let score = matched.length + "/" + jdKeywords.length;
      document.getElementById("result").innerHTML = `
        <h3>Result:</h3>
        <p><strong>Score:</strong> ${score}</p>
        <p><strong>Matched Keywords:</strong> ${matched.join(", ") || "None"}</p>
      `;
    });
  </script>
</body>
</html>
