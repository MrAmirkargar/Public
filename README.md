<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<title>تست شخصیت‌شناسی انتخاب رشته علوم تجربی</title>
<style>
    body {
        font-family: tahoma, sans-serif;
        background-color: #f5f5f5;
        direction: rtl;
        padding: 20px;
        line-height: 1.8;
    }
    h1 {
        text-align: center;
        color: #333;
    }
    .question {
        background: #fff;
        padding: 15px;
        border-radius: 10px;
        margin-bottom: 10px;
        box-shadow: 0 0 5px rgba(0,0,0,0.1);
    }
    .question p {
        margin: 0 0 10px;
    }
    button {
        background-color: #4CAF50;
        color: white;
        padding: 10px 20px;
        font-size: 16px;
        border: none;
        border-radius: 8px;
        cursor: pointer;
    }
    button:hover {
        background-color: #45a049;
    }
    .result {
        margin-top: 20px;
        padding: 15px;
        background: #fff;
        border-radius: 10px;
        box-shadow: 0 0 5px rgba(0,0,0,0.1);
    }
</style>
</head>
<body>

<h1>تست شخصیت‌شناسی انتخاب رشته علوم تجربی</h1>

<form id="quizForm">
    <div id="questions"></div>
    <button type="button" onclick="calculateScore()">محاسبه نتیجه</button>
</form>

<div class="result" id="result"></div>

<script>
const questions = [
    "رشته‌های پزشکی، دندان‌پزشکی، داروسازی یا مشابه باعث هیجان من می‌شوند.",
    "از مطالعه زیست‌شناسی، شیمی و آناتومی لذت می‌برم، حتی خارج از مدرسه.",
    "به کشف، تحقیق یا آزمایش علاقه دارم.",
    "دیدن خون یا جراحی برایم مشکلی ندارد.",
    "می‌توانم حجم زیادی از مطالب را حفظ کنم.",
    "در کارهای دقیق و ظریف (مثل آزمایش) مهارت دارم.",
    "در مدیریت زمان برای درس‌های سنگین موفق هستم.",
    "در کار تیمی فعال و مؤثر هستم.",
    "حاضر هستم چند سال سخت تحصیل کنم تا شغلی خاص داشته باشم.",
    "خدمت به مردم برایم مهم‌تر از درآمد بالاست.",
    "دوست دارم شغلم ساعت کاری منظم داشته باشد.",
    "حاضر هستم برای شغلم مهاجرت کنم.",
    "در شرایط استرس‌زا آرامش خودم را حفظ می‌کنم.",
    "در پروژه‌های طولانی‌مدت صبور هستم.",
    "اهل برنامه‌ریزی دقیق هستم.",
    "از شکست انگیزه می‌گیرم تا بهتر شوم.",
    "خانواده‌ام از ادامه تحصیل طولانی‌مدت من حمایت می‌کنند.",
    "از نظر مالی برای تحصیل چند ساله مشکلی ندارم.",
    "فرد موفقی در رشته‌های علوم تجربی در اطرافم هست که می‌توانم از او مشورت بگیرم.",
    "اگر در رشته‌های تاپ قبول نشوم، همچنان به ادامه مسیر در شاخه‌های دیگر علوم تجربی علاقه دارم."
];

const container = document.getElementById("questions");

questions.forEach((q, i) => {
    const div = document.createElement("div");
    div.classList.add("question");
    div.innerHTML = `
        <p>${i+1}. ${q}</p>
        <label><input type="radio" name="q${i}" value="1"> ۱ (اصلاً درست نیست)</label><br>
        <label><input type="radio" name="q${i}" value="2"> ۲</label><br>
        <label><input type="radio" name="q${i}" value="3"> ۳</label><br>
        <label><input type="radio" name="q${i}" value="4"> ۴</label><br>
        <label><input type="radio" name="q${i}" value="5"> ۵ (کاملاً درست است)</label>
    `;
    container.appendChild(div);
});

function calculateScore() {
    let total = 0;
    let answered = 0;
    questions.forEach((_, i) => {
        const selected = document.querySelector(`input[name="q${i}"]:checked`);
        if (selected) {
            total += parseInt(selected.value);
            answered++;
        }
    });

    if (answered < questions.length) {
        alert("لطفاً به همه سوال‌ها پاسخ دهید.");
        return;
    }

    let resultText = `امتیاز شما: ${total} از 100<br><br>`;
    if (total >= 80) {
        resultText += "✅ شما برای رشته‌های سنگین و رقابتی علوم تجربی (پزشکی، دندان‌پزشکی، داروسازی) مناسب هستید.";
    } else if (total >= 60) {
        resultText += "⚖️ توانایی و علاقه دارید، ولی بهتر است رشته‌هایی انتخاب کنید که با سبک زندگی و توان تحملتان سازگارتر باشد (پرستاری، فیزیوتراپی، علوم آزمایشگاهی).";
    } else if (total >= 40) {
        resultText += "💡 بهتر است رشته‌هایی با فشار کمتر یا حوزه‌های پژوهشی و محیطی را در نظر بگیرید (زیست‌شناسی، محیط‌زیست، صنایع غذایی).";
    } else {
        resultText += "❗ احتمالاً مسیر علوم تجربی با شخصیت و شرایطتان همخوانی زیادی ندارد و بررسی شاخه‌های دیگر پیشنهاد می‌شود.";
    }

    document.getElementById("result").innerHTML = resultText;
}
</script>

</body>
</html>
