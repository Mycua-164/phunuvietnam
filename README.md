
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hành trình rực rỡ - 20/10</title>

<style>
:root {
  --pink: #ed4f91;
  --dark: #87345f;
  --purple: #a77ce0;
  --green: #218b68;
}
* { box-sizing: border-box; }

body {
  margin: 0;
  padding: 22px 12px;
  min-height: 100vh;
  font-family: Arial, Helvetica, sans-serif;
  color: #563449;
  background: linear-gradient(135deg,#fff2f7,#f4efff,#fff8e9);
}
button, input { font: inherit; }
button { cursor: pointer; }
button:disabled { cursor: default; }

.app { max-width: 780px; margin: auto; }
.top { text-align: center; margin-bottom: 20px; }
.flower { font-size: 34px; }

h1 {
  color: var(--dark);
  font-size: clamp(26px,5vw,40px);
  margin: 8px 0;
  line-height: 1.25;
}
.subtitle { color: #9c6380; line-height: 1.7; }

.card {
  background: rgba(255,255,255,.97);
  border: 1px solid #f4d5e4;
  border-radius: 25px;
  padding: clamp(18px,4vw,32px);
  box-shadow: 0 12px 35px #8c456514;
}
.hidden { display: none !important; }

.eyebrow {
  color: var(--pink);
  font-size: 13px;
  font-weight: bold;
  letter-spacing: 1.3px;
}
h2 { color: var(--dark); line-height: 1.45; }

input[type="text"], input[type="number"] {
  width: 100%;
  padding: 15px;
  border: 2px solid #f0d4e2;
  border-radius: 13px;
  outline: none;
  margin: 10px 0 16px;
  background: #fffafd;
}
input:focus { border-color: var(--pink); }

.btn {
  border: 0;
  border-radius: 13px;
  padding: 14px 19px;
  font-weight: bold;
}
.primary {
  background: linear-gradient(100deg,#ed4f91,#a77ce0);
  color: white;
  box-shadow: 0 5px 12px #e94f9130;
}
.secondary { background: #f9eaf2; color: var(--dark); }
.full { width: 100%; margin-top: 8px; }

.rules {
  background: #fff5f9;
  border-radius: 15px;
  padding: 15px 18px;
  line-height: 1.9;
  margin: 20px 0;
  font-size: 14px;
}

.headline {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}
.pill {
  padding: 8px 12px;
  border-radius: 30px;
  background: #fce6f0;
  color: #a13c6c;
  font-size: 13px;
  font-weight: bold;
}

.timer-wrap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 4px;
}
.timer-label {
  font-size: 11px;
  font-weight: bold;
  color: #9c6380;
}
.timer {
  width: 72px;
  height: 72px;
  border-radius: 50%;
  border: 5px solid #f6c7dc;
  display: grid;
  place-items: center;
  color: var(--pink);
  font-size: 26px;
  font-weight: bold;
  flex-shrink: 0;
  background: #fff8fb;
}
.timer.urgent {
  border-color: #e34e4e;
  color: #e34e4e;
  background: #fff0f0;
  animation: pulse .5s infinite alternate;
}
@keyframes pulse {
  to { transform: scale(1.05); }
}

.track {
  height: 8px;
  background: #f6e5ee;
  border-radius: 10px;
  overflow: hidden;
  margin: 18px 0 24px;
}
.bar {
  height: 100%;
  width: 0;
  background: linear-gradient(90deg,#ef659e,#a77ce0);
  transition: width .2s;
}

.question {
  font-size: clamp(20px,4vw,27px);
  line-height: 1.5;
  margin: 20px 0;
  color: #57334a;
}
.options {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
}
.option {
  display: flex;
  align-items: flex-start;
  gap: 10px;
  text-align: left;
  padding: 15px 13px;
  border: 2px solid #f0dbe6;
  border-radius: 15px;
  background: white;
  color: #68445a;
  min-height: 65px;
  line-height: 1.5;
}
.letter {
  display: grid;
  place-items: center;
  width: 30px;
  height: 30px;
  flex-shrink: 0;
  border-radius: 9px;
  background: #fce8f1;
  color: #b73c76;
  font-weight: bold;
}
.option:hover:not(:disabled) {
  border-color: var(--pink);
  background: #fff7fb;
}
.option.correct {
  border-color: #35a57b;
  background: #eaf9f2;
}
.option.correct .letter {
  background: #35a57b;
  color: white;
}
.option.wrong {
  border-color: #e66b75;
  background: #fff0f0;
}
.option.wrong .letter {
  background: #e66b75;
  color: white;
}
.option:disabled { opacity: 1; }

.feedback {
  margin-top: 18px;
  padding: 15px;
  border-radius: 13px;
  line-height: 1.7;
}
.feedback.good { background: #eaf9f2; color: #176b4c; }
.feedback.bad { background: #fff0f0; color: #9a343c; }
.feedback.neutral { background: #fff6e8; color: #855c19; }

.actions {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 18px;
}
.actions .btn { flex: 1; }

.numeric {
  max-width: 240px;
  font-size: 25px !important;
  text-align: center;
}
.result-score {
  font-size: 54px;
  font-weight: bold;
  color: var(--pink);
  text-align: center;
  margin: 15px 0;
}
.result-grid {
  display: grid;
  grid-template-columns: repeat(2,1fr);
  gap: 12px;
  margin: 22px 0;
}
.stat {
  background: #fff4f8;
  padding: 17px 10px;
  border-radius: 15px;
  text-align: center;
}
.stat strong {
  display: block;
  font-size: 25px;
  color: var(--dark);
  margin-bottom: 6px;
}
.stat span { font-size: 13px; color: #91627b; }
.note {
  font-size: 13px;
  color: #987a8c;
  line-height: 1.7;
}
.champion { font-size: 46px; text-align: center; }

@media(max-width:540px) {
  .options { grid-template-columns: 1fr; }
  .option { min-height: 55px; }
  .actions { flex-direction: column; }
  .actions .btn { width: 100%; }
}
</style>
</head>

<body>
<div class="app">

<header class="top">
  <div class="flower">🌷 🌸 ✨ 🌸 🌷</div>
  <h1>HÀNH TRÌNH RỰC RỠ</h1>
  <div class="subtitle">
    Chào mừng Ngày Phụ nữ Việt Nam 20/10<br>
    Tôn vinh vẻ đẹp, bản lĩnh và những đóng góp của phụ nữ Việt Nam
  </div>
</header>

<!-- MÀN HÌNH BẮT ĐẦU -->
<main class="card" id="intro">
  <div class="eyebrow">🌸 SẴN SÀNG CHINH PHỤC?</div>
  <h2>Chào mừng bạn đến với Hành trình rực rỡ!</h2>
  Hãy cùng khám phá lịch sử, những tấm gương phụ nữ Việt Nam
  và các câu đố vui thú vị.

  <label for="playerName"><strong>Họ và tên người chơi</strong></label>
  <input id="playerName" type="text" maxlength="100"
    placeholder="Nhập họ tên của bạn..." autocomplete="name">

  <div class="rules">
    <strong>📌 THỂ LỆ TRÒ CHƠI</strong><br>
    ⏱️ Mỗi câu có 20 giây suy nghĩ và trả lời.<br>
    🌸 Có 10 câu hỏi, chia thành 3 chặng.<br>
    🏆 Mỗi câu đúng được 1 điểm, tối đa 10 điểm.<br>
    💗 Trả lời sai sẽ hiện đáp án đúng.<br>
    ↷ Được bỏ qua câu hỏi nhưng không được quay lại.<br>
    🎉 Kết thúc, xem số câu đúng và thời gian tham gia.
  </div>

  <button class="btn primary full" id="startBtn">
    BẮT ĐẦU HÀNH TRÌNH ✨
  </button>
</main>

<!-- MÀN HÌNH CÂU HỎI -->
<main class="card hidden" id="quiz">
  <div class="headline">
    <span class="pill" id="stage">CHẶNG 1/3</span>
    <span class="pill" id="progressText">Câu 1/10</span>
    <div class="timer-wrap">
      <span class="timer-label">THỜI GIAN</span>
      <div class="timer" id="timer">20</div>
    </div>
  </div>

  <div class="track"><div class="bar" id="bar"></div></div>
  <div class="eyebrow" id="stageName"></div>
  <h2 class="question" id="questionText"></h2>

  <div id="answerArea"></div>
  <div id="feedback" class="feedback hidden" aria-live="polite"></div>

  <div class="actions">
    <button class="btn secondary" id="skipBtn">Bỏ qua câu này ↷</button>
    <button class="btn primary hidden" id="nextBtn">Câu tiếp theo →</button>
  </div>

  <p class="note">
    Sau khi trả lời hoặc bỏ qua, bạn không thể quay lại câu trước.
  </p>
</main>

<!-- MÀN HÌNH KẾT QUẢ -->
<main class="card hidden" id="result">
  <div class="champion" id="resultEmoji">🌷</div>
  <div class="eyebrow" style="text-align:center">
    HOÀN THÀNH HÀNH TRÌNH
  </div>
  <h2 id="resultTitle" style="text-align:center"></h2>
  <div class="result-score" id="scoreText"></div>
  <div style="text-align:center;color:#9c6380">Số câu trả lời đúng</div>

  <div class="result-grid">
    <div class="stat">
      <strong id="correctStat">0/10</strong>
      <span>Câu đúng</span>
    </div>
    <div class="stat">
      <strong id="wrongStat">0</strong>
      <span>Câu sai</span>
    </div>
    <div class="stat">
      <strong id="skipStat">0</strong>
      <span>Bỏ qua / hết giờ</span>
    </div>
    <div class="stat">
      <strong id="timeStat">00:00</strong>
      <span>Thời gian tham gia</span>
    </div>
  </div>

  <div id="message" class="feedback good"></div>
  <p class="note" id="finishedAt" style="text-align:center"></p>

  <button class="btn primary full" id="downloadBtn">
    TẢI KẾT QUẢ VỀ MÁY (.CSV)
  </button>
  <button class="btn secondary full" id="restartBtn">
    CHƠI LẠI 🔄
  </button>

  <p class="note">
    Kết quả được tải xuống thiết bị người chơi.
    Phiên bản này chưa tự động gửi kết quả về ban tổ chức.
  </p>
</main>

</div>

<script>
"use strict";

const TOTAL = 10;
const TIME_PER_QUESTION = 20;

const questions = [
  {
    stage: 1,
    title: "Dấu ấn lịch sử",
    q: "Hội Liên hiệp Phụ nữ Việt Nam được chính thức thành lập vào ngày nào?",
    opts: ["20/10/1930", "8/3/1930", "20/10/1945", "19/5/1930"],
    a: 0,
    explain: "Hội được thành lập ngày 20/10/1930."
  },
  {
    stage: 1,
    title: "Dấu ấn lịch sử",
    q: "Tên gọi tiền thân của Hội khi mới thành lập năm 1930 là gì?",
    opts: [
      "Hội Phụ nữ Cứu quốc",
      "Hội Phụ nữ Phản đế Việt Nam",
      "Hội Nữ thanh niên",
      "Hội Phụ nữ Giải phóng"
    ],
    a: 1,
    explain: "Tên gọi là Hội Phụ nữ Phản đế Việt Nam."
  },
  {
    stage: 1,
    title: "Dấu ấn lịch sử",
    q: "Bác Hồ từng tặng phụ nữ Việt Nam tám chữ vàng nào?",
    opts: [
      "Cần cù – Sáng tạo – Kiên cường – Nhân ái",
      "Trung thành – Dũng cảm – Khiêm tốn – Đảm đang",
      "Anh hùng – Bất khuất – Trung hậu – Đảm đang",
      "Độc lập – Tự do – Hạnh phúc – Bình đẳng"
    ],
    a: 2,
    explain: "Tám chữ vàng: Anh hùng – Bất khuất – Trung hậu – Đảm đang."
  },
  {
    stage: 2,
    title: "Những đóa hoa anh hùng",
    q: "Nữ tướng tiêu biểu nào được biết đến là nữ tướng đầu tiên của Quân đội nhân dân Việt Nam?",
    opts: [
      "Võ Thị Sáu",
      "Nguyễn Thị Bình",
      "Nguyễn Thị Định",
      "Nguyễn Thị Minh Khai"
    ],
    a: 2,
    explain: "Đáp án: Nguyễn Thị Định, nữ tướng tiêu biểu của Việt Nam."
  },
  {
    stage: 2,
    title: "Những đóa hoa anh hùng",
    q: "Chị Võ Thị Sáu hy sinh tại Côn Đảo khi bao nhiêu tuổi?",
    type: "number",
    a: 16,
    explain: "Chị Võ Thị Sáu hy sinh khi mới 16 tuổi."
  },
  {
    stage: 2,
    title: "Những đóa hoa anh hùng",
    q: "Tứ đức của người phụ nữ truyền thống Việt Nam gồm những gì?",
    opts: [
      "Nhân – Nghĩa – Lễ – Trí",
      "Công – Dung – Ngôn – Hạnh",
      "Cần – Kiệm – Liêm – Chính",
      "Hiếu – Trung – Tiết – Nghĩa"
    ],
    a: 1,
    explain: "Tứ đức truyền thống: Công – Dung – Ngôn – Hạnh."
  },
  {
    stage: 3,
    title: "Hiểu biết và nụ cười",
    q: "Người phụ nữ Việt Nam nào tham gia ký Hiệp định Paris năm 1973 về chấm dứt chiến tranh, lập lại hòa bình ở Việt Nam?",
    opts: [
      "Nguyễn Thị Định",
      "Nguyễn Thị Bình",
      "Võ Thị Sáu",
      "Nguyễn Thị Minh Khai"
    ],
    a: 1,
    explain: "Bà Nguyễn Thị Bình đại diện Chính phủ Cách mạng lâm thời Cộng hòa miền Nam Việt Nam tại Hội nghị Paris."
  },
  {
    stage: 3,
    title: "Hiểu biết và nụ cười",
    q: "Câu đố vui: Bộ phận nào thường nhô rõ ở cổ nam giới và được gọi là yết hầu?",
    opts: [
      "Xương quai xanh",
      "Xương gò má",
      "Sụn giáp ở thanh quản",
      "Xương đòn"
    ],
    a: 2,
    explain: "Yết hầu là phần sụn giáp ở thanh quản nhô ra phía trước cổ. Phụ nữ cũng có cấu trúc này."
  },
  {
    stage: 3,
    title: "Hiểu biết và nụ cười",
    q: "Ở nhóm người nào, tóc xoăn chặt tự nhiên thường phổ biến hơn do đặc điểm di truyền?",
    opts: [
      "Người có tổ tiên vùng hạ Sahara châu Phi",
      "Người có tổ tiên Bắc Âu",
      "Người có tổ tiên Đông Á",
      "Người có tổ tiên vùng Bắc Cực"
    ],
    a: 0,
    explain: "Tóc xoăn chặt tự nhiên phổ biến ở nhiều cộng đồng có tổ tiên vùng hạ Sahara châu Phi. Đặc điểm tóc vẫn đa dạng giữa từng người."
  },
  {
    stage: 3,
    title: "Hiểu biết và nụ cười",
    q: "Ngày 20/10 hằng năm là dịp kỷ niệm và tôn vinh điều gì?",
    opts: [
      "Ngày thành lập Đoàn Thanh niên Cộng sản Hồ Chí Minh",
      "Ngày Phụ nữ Việt Nam",
      "Ngày Nhà giáo Việt Nam",
      "Ngày Quốc tế Thiếu nhi"
    ],
    a: 1,
    explain: "Ngày 20/10 hằng năm là Ngày Phụ nữ Việt Nam, dịp tôn vinh phụ nữ Việt Nam."
  }
];

let index = 0;
let score = 0;
let wrong = 0;
let skipped = 0;
let startedAt = 0;
let deadline = 0;
let timerId = null;
let locked = false;
let player = "";
let finalRecord = null;

const $ = id => document.getElementById(id);
const intro = $("intro");
const quiz = $("quiz");
const result = $("result");

function formatTime(seconds) {
  seconds = Math.max(0, Math.floor(seconds));
  const m = String(Math.floor(seconds / 60)).padStart(2, "0");
  const s = String(seconds % 60).padStart(2, "0");
  return `${m}:${s}`;
}

function elapsed() {
  return Math.floor((Date.now() - startedAt) / 1000);
}

function showPanel(panel) {
  [intro, quiz, result].forEach(p => p.classList.add("hidden"));
  panel.classList.remove("hidden");
  window.scrollTo({ top: 0, behavior: "smooth" });
}

/* BẮT ĐẦU TRÒ CHƠI */
$("startBtn").addEventListener("click", () => {
  player = $("playerName").value.trim();

  if (!player) {
    alert("Bạn vui lòng nhập họ tên trước khi bắt đầu nhé!");
    $("playerName").focus();
    return;
  }

  clearInterval(timerId);
  index = 0;
  score = 0;
  wrong = 0;
  skipped = 0;
  startedAt = Date.now();
  finalRecord = null;

  showPanel(quiz);
  renderQuestion();
});

/* HIỂN THỊ CÂU HỎI VÀ KHỞI ĐỘNG ĐỒNG HỒ */
function renderQuestion() {
  clearInterval(timerId);
  locked = false;

  const item = questions[index];

  $("stage").textContent = `CHẶNG ${item.stage}/3`;
  $("stageName").textContent = item.title.toUpperCase();
  $("progressText").textContent = `Câu ${index + 1}/${TOTAL}`;
  $("bar").style.width = `${index / TOTAL * 100}%`;
  $("questionText").textContent = item.q;

  $("feedback").className = "feedback hidden";
  $("feedback").textContent = "";
  $("nextBtn").classList.add("hidden");
  $("skipBtn").classList.remove("hidden");
  $("skipBtn").disabled = false;

  $("timer").textContent = TIME_PER_QUESTION;
  $("timer").classList.remove("urgent");

  const area = $("answerArea");
  area.innerHTML = "";

  if (item.type === "number") {
    const form = document.createElement("form");
    const input = document.createElement("input");

    input.type = "number";
    input.id = "numericAnswer";
    input.className = "numeric";
    input.placeholder = "Nhập số tuổi";
    input.min = "0";
    input.max = "120";
    input.required = true;
    input.setAttribute("aria-label", "Nhập đáp án bằng số");

    const submit = document.createElement("button");
    submit.className = "btn primary";
    submit.type = "submit";
    submit.textContent = "XÁC NHẬN ĐÁP ÁN";

    form.append(input, submit);
    form.addEventListener("submit", e => {
      e.preventDefault();
      if (locked) return;
      if (input.value.trim() === "") return;
      checkAnswer(Number(input.value));
    });
    area.append(form);
  } else {
    const options = document.createElement("div");
    options.className = "options";

    item.opts.forEach((text, i) => {
      const button = document.createElement("button");
      button.type = "button";
      button.className = "option";

      const letter = document.createElement("span");
      letter.className = "letter";
      letter.textContent = "ABCD"[i];

      const label = document.createElement("span");
      label.textContent = text;

      button.append(letter, label);
      button.addEventListener("click", () => checkAnswer(i));
      options.append(button);
    });

    area.append(options);
  }

  /*
    Dùng mốc thời gian thực để tính số giây còn lại.
    Không giảm biến đếm từng giây, tránh lệch thời gian.
  */
  deadline = Date.now() + TIME_PER_QUESTION * 1000;

  // Chạy cập nhật ngay lập tức, sau đó cập nhật liên tục.
  updateTimer();
  timerId = window.setInterval(updateTimer, 100);
}

/* ĐỒNG HỒ ĐẾM NGƯỢC */
function updateTimer() {
  if (locked) return;

  const millisecondsLeft = deadline - Date.now();
  const remaining = Math.max(
    0,
    Math.ceil(millisecondsLeft / 1000)
  );

  $("timer").textContent = remaining;
  $("timer").classList.toggle("urgent", remaining <= 5);

  if (millisecondsLeft <= 0) {
    clearInterval(timerId);
    lockAsTimeout();
  }
}

/* KHÓA TOÀN BỘ Ô TRẢ LỜI */
function disableAnswers() {
  $("answerArea").querySelectorAll("button, input").forEach(el => {
    el.disabled = true;
  });
  $("skipBtn").disabled = true;
}

/* LẤY ĐÁP ÁN ĐÚNG */
function getCorrectAnswer(item) {
  if (item.type === "number") return String(item.a);
  return "ABCD"[item.a] + ". " + item.opts[item.a];
}

/* TÔ MÀU ĐÁP ÁN ĐÚNG */
function highlightCorrect(item) {
  $("answerArea").querySelectorAll(".option").forEach((button, i) => {
    if (i === item.a) button.classList.add("correct");
  });
}

/* HIỆN NÚT ĐI TIẾP */
function showNextButton() {
  $("skipBtn").classList.add("hidden");
  $("nextBtn").classList.remove("hidden");
  $("nextBtn").textContent =
    index === TOTAL - 1 ? "XEM KẾT QUẢ 🏆" : "CÂU TIẾP THEO →";
}

/* KIỂM TRA ĐÁP ÁN */
function checkAnswer(value) {
  if (locked) return;

  // Chặn trả lời nếu thời hạn đã kết thúc,
  // kể cả khi trình duyệt chưa kịp chạy bộ đếm.
  if (Date.now() >= deadline) {
    lockAsTimeout();
    return;
  }

  locked = true;
  clearInterval(timerId);

  const item = questions[index];
  const correct = Number(value) === item.a;

  disableAnswers();

  if (correct) {
    score++;
    $("feedback").className = "feedback good";
    $("feedback").textContent = "🎉 Chính xác! " + item.explain;
  } else {
    wrong++;
    $("feedback").className = "feedback bad";
    $("feedback").textContent =
      "💗 Rất tiếc, chưa chính xác. Đáp án đúng: " +
      getCorrectAnswer(item) + ". " + item.explain;
    highlightCorrect(item);
  }

  $("feedback").classList.remove("hidden");
  showNextButton();
}

/* HẾT 20 GIÂY */
function lockAsTimeout() {
  if (locked) return;

  locked = true;
  clearInterval(timerId);
  skipped++;

  const item = questions[index];
  disableAnswers();

  $("timer").textContent = "0";
  $("timer").classList.add("urgent");

  $("feedback").className = "feedback neutral";
  $("feedback").textContent =
    "⏰ Hết giờ! Đáp án đúng: " +
    getCorrectAnswer(item) + ". " + item.explain;

  $("feedback").classList.remove("hidden");
  highlightCorrect(item);
  showNextButton();
}

/* BỎ QUA CÂU HỎI */
$("skipBtn").addEventListener("click", () => {
  if (locked) return;

  // Nếu đã hết hạn thì xử lý là hết giờ.
  if (Date.now() >= deadline) {
    lockAsTimeout();
    return;
  }

  locked = true;
  clearInterval(timerId);
  skipped++;

  const item = questions[index];
  disableAnswers();

  $("feedback").className = "feedback neutral";
  $("feedback").textContent =
    "Bạn đã bỏ qua câu này. Đáp án đúng: " +
    getCorrectAnswer(item) + ". " + item.explain;

  $("feedback").classList.remove("hidden");
  highlightCorrect(item);
  showNextButton();
});

/* SANG CÂU TIẾP THEO */
$("nextBtn").addEventListener("click", () => {
  if (!locked) return;

  if (index < TOTAL - 1) {
    index++;
    renderQuestion();
  } else {
    finishGame();
  }
});

/* TỔNG KẾT */
function finishGame() {
  clearInterval(timerId);

  const finishedAt = new Date();
  const totalSeconds = elapsed();

  $("bar").style.width = "100%";
  $("resultTitle").textContent = `Chúc mừng ${player}!`;
  $("scoreText").textContent = `${score}/${TOTAL}`;
  $("correctStat").textContent = `${score}/${TOTAL}`;
  $("wrongStat").textContent = wrong;
  $("skipStat").textContent = skipped;
  $("timeStat").textContent = formatTime(totalSeconds);

  $("finishedAt").textContent =
    "Hoàn thành lúc: " + finishedAt.toLocaleString("vi-VN");

  $("resultEmoji").textContent =
    score === TOTAL ? "🏆🌸" :
    score >= 7 ? "🌷💗" : "🌸";

  $("message").textContent =
    score === TOTAL
      ? "Xuất sắc! Bạn đã chinh phục cả 10 câu hỏi. Chúc mừng ngày 20/10!"
      : score >= 7
      ? "Rất đáng tự hào! Chúc bạn luôn tỏa sáng và lan tỏa yêu thương."
      : "Cảm ơn bạn đã tham gia. Chúc bạn một ngày 20/10 thật vui và ý nghĩa!";

  finalRecord = {
    name: player,
    score,
    total: TOTAL,
    wrong,
    skipped,
    duration: formatTime(totalSeconds),
    finishedAt: finishedAt.toLocaleString("vi-VN")
  };

  showPanel(result);
}

/* CHƠI LẠI */
$("restartBtn").addEventListener("click", () => {
  clearInterval(timerId);
  $("playerName").value = player;
  showPanel(intro);
});

/* TẢI KẾT QUẢ CSV */
$("downloadBtn").addEventListener("click", () => {
  if (!finalRecord) return;

  const r = finalRecord;
  const rows = [
    [
      "Họ và tên",
      "Số câu đúng",
      "Tổng số câu",
      "Số câu sai",
      "Bỏ qua/hết giờ",
      "Thời gian",
      "Thời điểm hoàn thành"
    ],
    [
      r.name,
      r.score,
      r.total,
      r.wrong,
      r.skipped,
      r.duration,
      r.finishedAt
    ]
  ];

  const csv = "\uFEFF" + rows.map(row =>
    row.map(value =>
      '"' + String(value).replace(/"/g, '""') + '"'
    ).join(",")
  ).join("\r\n");

  const blob = new Blob([csv], {
    type: "text/csv;charset=utf-8;"
  });

  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");

  a.href = url;
  a.download = "ket-qua-hanh-trinh-ruc-ro-20-10.csv";
  document.body.appendChild(a);
  a.click();
  a.remove();

  setTimeout(() => URL.revokeObjectURL(url), 1000);
});
</script>
</body>
</html>
