<!DOCTYPE html>
<html lang="zh-Hant">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>國中簡易英文單字測驗系統（Google 試算表連線版）</title>
  <!-- 引入 Google Fonts 的 Yusei Magic 字體 -->
  <link href="https://fonts.googleapis.com/css2?family=Yusei+Magic&display=swap" rel="stylesheet">
  <!-- 引入 p5.js 核心庫 -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/1.6.0/p5.js"></script>
  <style>
    /* 設定全螢幕樣式，取消預設邊距並隱藏捲軸，套用 Yusei Magic 字體 */
    html, body {
      margin: 0;
      padding: 0;
      overflow: hidden;
      width: 100%;
      height: 100%;
      background-color: #1e1e1e;
      font-family: 'Yusei Magic', sans-serif;
    }
  </style>
</head>
<body>
  <script>
    // 宣告全域變數
    let allQuestions = [];   // 從 Google 試算表載入的完整題庫
    let questions = [];      // 每次隨機抽出的 5 題陣列
    let currentQ = 0;        // 當前題目索引 (0 到 4)
    let score = 0;          // 紀錄答對的題數
    let state = "LOADING";   // 當前測驗狀態："LOADING" (讀取中)、"QUESTION" (答題中)、"ANSWERED" (已回答)、"END" (測驗結束)
    let selectedOption = -1; // 使用者選擇的選項索引 (-1 表示未選擇)
    let nextBtn;             // 下一題 / 重新開始按鈕元件

    // 設定您的 Google 試算表發布 CSV 網址
    let sheetCSVUrl = 'https://docs.google.com/spreadsheets/d/e/2PACX-1vRgSo1pxGbso471DyiKTjHF0xY8F-stjYP3V6jjnJpp0zDqpgspug7sytIKHsX4XlaRtyI3kHJniY7h/pub?gid=715029714&single=true&output=csv';

    function preload() {
      // 使用 p5.js 的 loadTable 非同步讀取線上 Google 試算表 CSV，設定 header: true
      allQuestions = loadTable(sheetCSVUrl, 'csv', 'header', 
        () => { 
          console.log("Google 試算表題庫載入成功！"); 
          initQuiz(); // 載入成功後初始化測驗
        },
        (err) => { 
          console.error("載入失敗，請檢查網址或發布狀態", err); 
        }
      );
    }

    function setup() {
      // 建立與視窗同等大小的全螢幕畫布
      createCanvas(windowWidth, windowHeight);
      // 設定文字對齊方式為水平與垂直居中
      textAlign(CENTER, CENTER);
      // 設定全域文字字型為 Yusei Magic
      textFont('Yusei Magic');

      // 建立「下一題」按鈕並設定樣式與點擊事件
      nextBtn = createButton("下一題");
      nextBtn.style("font-family", "'Yusei Magic', sans-serif");
      nextBtn.style("font-size", "20px");
      nextBtn.style("padding", "10px 24px");
      nextBtn.style("cursor", "pointer");
      nextBtn.style("border-radius", "8px");
      nextBtn.style("border", "none");
      nextBtn.style("background-color", "#ffffff");
      nextBtn.mousePressed(handleNextButton);
      nextBtn.hide(); // 剛開始載入時先隱藏按鈕

      // 若 preload 已經快速完成，在此預防性初始化
      if (allQuestions && allQuestions.getRowCount() > 0) {
        initQuiz();
      }
    }

    // 初始化測驗：解析試算表資料、隨機打亂並抽出 5 題
    function initQuiz() {
      let tempArray = [];

      // 如果有成功載入 Google 試算表資料
      if (allQuestions && allQuestions.getRowCount() > 0) {
        for (let i = 0; i < allQuestions.getRowCount(); i++) {
          let row = allQuestions.getRow(i);
          tempArray.push({
            q: row.get('q'),
            options: [row.get('opt0'), row.get('opt1'), row.get('opt2'), row.get('opt3')],
            correct: int(row.get('correct'))
          });
        }
      }

      // 如果題庫不為空，隨機打亂並抽出 5 題
      if (tempArray.length > 0) {
        tempArray = shuffle(tempArray);
        questions = tempArray.slice(0, 5);
        
        // 重設測驗狀態變數
        currentQ = 0;
        score = 0;
        selectedOption = -1;
        state = "QUESTION";
      }
    }

    function draw() {
      // 設定深灰色背景，突顯色彩對比
      background(30);

      // 判斷當前畫面狀態進行繪製
      if (state === "LOADING") {
        fill(255);
        textSize(28);
        text("正在從 Google 試算表載入題庫...", width / 2, height / 2);
      } else if (state === "END") {
        // 繪製測驗結束結算畫面
        drawEndScreen();
      } else {
        // 繪製題目與選項畫面
        drawQuestionScreen();
      }
    }

    // 繪製題目與選項畫面的函式 (支援響應式排版)
    function drawQuestionScreen() {
      if (questions.length === 0) return;
      let qData = questions[currentQ];

      // 依據螢幕尺寸動態計算字體與按鈕大小 (適應電腦、平板、手機直橫向)
      let qTextSize = constrain(width * 0.03, 18, 28);
      let btnTextSize = constrain(width * 0.022, 14, 20);
      let btnW = constrain(width * 0.7, 280, 500);
      let btnH = constrain(height * 0.08, 45, 65);
      let startY = height * 0.32;
      let spacing = btnH + 15;

      // 繪製上方題目文字
      fill(255);
      textSize(qTextSize);
      text(qData.q, width / 2, height * 0.18);

      // 迴圈繪製 4 個選項
      for (let i = 0; i < 4; i++) {
        let x = width / 2 - btnW / 2;
        let y = startY + i * spacing;

        // 判斷選項填色邏輯
        if (state === "QUESTION") {
          // 答題前：滑鼠懸停變色效果
          if (mouseX > x && mouseX < x + btnW && mouseY > y && mouseY < y + btnH) {
            fill(100);
          } else {
            fill(60);
          }
        } else if (state === "ANSWERED") {
          // 答題後：顯示正確與錯誤顏色
          if (i === qData.correct) {
            fill("#cad182"); // 正確答案顏色 (#cad182)
          } else if (i === selectedOption) {
            fill("#c1121f"); // 選擇錯誤的選項顏色 (#c1121f)
          } else {
            fill(50);        // 其他未選中的非正確選項
          }
        }

        // 繪製圓角選項框
        noStroke();
        rect(x, y, btnW, btnH, 10);

        // 繪製選項文字 (根據背景深淺調整文字顏色)
        fill(state === "ANSWERED" && (i === qData.correct || i === selectedOption) ? (i === qData.correct ? 30 : 255) : 255);
        textSize(btnTextSize);
        text(qData.options[i], width / 2, y + btnH / 2);
      }

      // 若已回答，更新並顯示「下一題」按鈕位置
      if (state === "ANSWERED") {
        nextBtn.position(width / 2 - nextBtn.width / 2, height * 0.82);
        nextBtn.show();
      }
    }

    // 繪製最終結算畫面的函式
    function drawEndScreen() {
      let titleSize = constrain(width * 0.04, 24, 38);
      let scoreSize = constrain(width * 0.035, 20, 32);

      fill(255);
      textSize(titleSize);
      text("測驗結束！", width / 2, height * 0.35);

      // 顯示最終答對題數與總題數
      textSize(scoreSize);
      fill("#cad182");
      text("您一共答對了 " + score + " / " + questions.length + " 題", width / 2, height * 0.48);

      // 設定並顯示重新開始按鈕
      nextBtn.html("重新測驗");
      nextBtn.position(width / 2 - nextBtn.width / 2, height * 0.62);
      nextBtn.show();
    }

    // 滑鼠點擊事件處理
    function mousePressed() {
      // 僅在「答題中」狀態接受選項點擊
      if (state !== "QUESTION") return;

      let btnW = constrain(width * 0.7, 280, 500);
      let btnH = constrain(height * 0.08, 45, 65);
      let startY = height * 0.32;
      let spacing = btnH + 15;

      // 檢測點擊了哪一個選項
      for (let i = 0; i < 4; i++) {
        let x = width / 2 - btnW / 2;
        let y = startY + i * spacing;

        if (mouseX > x && mouseX < x + btnW && mouseY > y && mouseY < y + btnH) {
          selectedOption = i;
          // 檢查答案是否正確，正確則加分
          if (i === questions[currentQ].correct) {
            score++;
          }
          // 切換狀態為「已回答」
          state = "ANSWERED";
          break;
        }
      }
    }

    // 按鈕點擊事件處理 (下一題 / 重新測驗)
    function handleNextButton() {
      if (state === "ANSWERED") {
        currentQ++; // 切換至下一題
        if (currentQ < questions.length) {
          // 仍有題目：重置狀態為答題中
          state = "QUESTION";
          selectedOption = -1;
          nextBtn.hide();
        } else {
          // 五題皆已做完：切換至結算狀態
          state = "END";
        }
      } else if (state === "END") {
        // 重新開始測驗：重新隨機抽取 5 題並重置變數
        initQuiz();
        nextBtn.html("下一題");
        nextBtn.hide();
      }
    }

    // 當瀏覽器視窗大小改變時，自動修正畫布為全螢幕
    function windowResized() {
      resizeCanvas(windowWidth, windowHeight);
    }
  </script>
</body>
</html>