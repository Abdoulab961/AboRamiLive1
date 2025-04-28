<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <title>جدول المباريات</title>
</head>
<body style="direction: rtl; font-family: Cairo, sans-serif; background-color: #121212; color: white; text-align: center;">
  <h1>جدول مباريات اليوم</h1>
  <div id="matches"></div>

  <script>
    fetch('https://drive.google.com/uc?export=download&id=1yzp6eZPo7Ng7_7j3PdyVtlP0HTbVzbGk')
      .then(response => response.json())
      .then(data => {
        let output = '<ul>';
        data.matches.forEach(match => {
          output += `<li>${match.homeTeam} ضد ${match.awayTeam} - الساعة ${match.time} (${match.competition})</li>`;
        });
        output += '</ul>';
        document.getElementById('matches').innerHTML = output;
      })
      .catch(error => {
        console.error('حدث خطأ:', error);
        document.getElementById('matches').innerHTML = 'فشل تحميل المباريات.';
      });
  </script>
</body>
</html>
