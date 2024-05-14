<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Resume Builder</title>
<style>
    body {
        font-family: Arial, sans-serif;
        margin: 0;
        padding: 0;
    }
    .container {
        max-width: 800px;
        margin: 20px auto;
        padding: 20px;
        border: 1px solid #ccc;
        border-radius: 5px;
        box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    }
    h1 {
        text-align: center;
    }
    form {
        margin-top: 20px;
    }
    label, input, textarea {
        display: block;
        margin-bottom: 10px;
    }
    input[type="submit"] {
        padding: 10px 20px;
        background-color: #007bff;
        color: #fff;
        border: none;
        border-radius: 5px;
        cursor: pointer;
    }
    input[type="submit"]:hover {
        background-color: #0056b3;
    }
</style>
</head>
<body>
<div class="container">
    <h1>Resume Builder</h1>
    <form id="resumeForm">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>

        <label for="email">Email:</label>
        <input type="email" id="email" name="email" required>

        <label for="phone">Phone:</label>
        <input type="tel" id="phone" name="phone" required>

        <label for="summary">Summary:</label>
        <textarea id="summary" name="summary" rows="4" required></textarea>

        <label for="experience">Experience:</label>
        <textarea id="experience" name="experience" rows="4" required></textarea>

        <label for="education">Education:</label>
        <textarea id="education" name="education" rows="4" required></textarea>

        <label for ="skills">skills:</label>
        <textarea id="skills" name="skills" rows="4"  required></textarea>

        <label for ="profile">profile:</label>
        <textarea id="profile" name="profile"  required></textarea>

        <input type="submit" value="Generate Resume">
    </form>
    <div id="output"></div>
</div>

<script>
    document.getElementById('resumeForm').addEventListener('submit', function(event) {
        event.preventDefault();

        // Get form values
        const name = document.getElementById('name').value;
        const email = document.getElementById('email').value;
        const phone = document.getElementById('phone').value;
        const summary = document.getElementById('summary').value;
        const experience = document.getElementById('experience').value;
        const education = document.getElementById('education').value;
        const skills = document.getElementById('skills').value;
        const profile = document.getElementById('profile').value;

        // Generate resume HTML
        const resumeHTML = `
            <h2>${name}</h2>
            <p>Email: ${email}</p>
            <p>Phone: ${phone}</p>
            <h3>Summary</h3>
            <p>${summary}</p>
            <h3>Experience</h3>
            <p>${experience}</p>
            <h3>Education</h3>
            <p>${education}</p>
            <h3>skills</h3>
            <p>${skills}</p>
            <h3>profile</h3>
            <p>${profile}</p>

        `;

        // Display generated resume
        document.getElementById('output').innerHTML = resumeHTML;
    });
</script>
</body>
</html>
- 

<!---
sandhyaprasanna2003/sandhyaprasanna2003 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
