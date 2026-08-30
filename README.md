<!DOCTYPE html>
<html lang="zh-TW" data-theme="light">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>會員中心</title>
  <!-- 引入 Tailwind CSS + DaisyUI -->
  <link href="https://cdn.jsdelivr.net/npm/daisyui@4.7.2/dist/full.min.css" rel="stylesheet" type="text/css" />
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- 引入 LINE LIFF SDK -->
  <script charset="utf-8" src="https://static.line-scdn.net/liff/edge/2/sdk.js"></script>
</head>
<body class="bg-slate-100 min-h-screen pb-10">

  <!-- 頂部品牌 Header (Logo + 標題) -->
  <header class="bg-white px-4 py-3 shadow-sm flex items-center justify-center space-x-2 sticky top-0 z-50">
    <img 
      src="https://raw.githubusercontent.com/x6413397-commits/-LOGO/main/cfec8388-0099-425a-956e-fa1e93c2a666.jpg" 
      alt="Company Logo" 
      class="w-8 h-8 object-contain rounded-full border"
    >
    <span class="font-bold text-slate-800 text-lg">會員服務中心</span>
  </header>

  <main class="max-w-md mx-auto px-4">
    
    <!-- 區塊 A：會員卡片 (融入 Logo 作為質感背景與標誌) -->
    <div id="memberCardSection" class="relative bg-gradient-to-br from-purple-800 via-purple-600 to-pink-600 rounded-2xl p-6 text-white shadow-xl my-5 overflow-hidden">
      <!-- 內容層 -->
      <div class="relative z-10 flex flex-col justify-between h-36">
        <div class="flex justify-between items-start">
          <div>
            <p class="text-xs tracking-widest opacity-75 uppercase">VIP MEMBER</p>
            <h2 id="cardUserName" class="text-2xl font-bold mt-1">載入中...</h2>
          </div>
          <!-- 右上角小 Logo -->
          <img 
            src="https://raw.githubusercontent.com/x6413397-commits/-LOGO/main/cfec8388-0099-425a-956e-fa1e93c2a666.jpg" 
            class="w-10 h-10 rounded-full border-2 border-white/50 object-cover shadow"
          >
        </div>
        <p id="cardUserId" class="text-xs opacity-60 font-mono">ID: Loading...</p>
      </div>

      <!-- 背景浮水印 Logo 裝飾 (微調透明度與大小，打造高級感) -->
      <img 
        src="https://raw.githubusercontent.com/x6413397-commits/-LOGO/main/cfec8388-0099-425a-956e-fa1e93c2a666.jpg" 
        class="absolute -right-8 -bottom-8 w-44 h-44 object-cover rounded-full opacity-15 pointer-events-none mix-blend-overlay filter blur-[1px]"
      >
    </div>

    <!-- 快速選單按鈕區 (截圖一對應功能) -->
    <div id="menuGrid" class="grid grid-cols-3 gap-3 my-6">
      <button class="bg-white p-4 rounded-xl shadow-sm hover:shadow-md transition flex flex-col items-center justify-center active:scale-95">
        <span class="text-2xl mb-1">📅</span>
        <span class="text-xs text-slate-600 font-medium">預約紀錄</span>
      </button>
      <button class="bg-white p-4 rounded-xl shadow-sm hover:shadow-md transition flex flex-col items-center justify-center active:scale-95">
        <span class="text-2xl mb-1">🧾</span>
        <span class="text-xs text-slate-600 font-medium">消費紀錄</span>
      </button>
      <button class="bg-white p-4 rounded-xl shadow-sm hover:shadow-md transition flex flex-col items-center justify-center active:scale-95">
        <span class="text-2xl mb-1">👤</span>
        <span class="text-xs text-slate-600 font-medium">個人資料</span>
      </button>
    </div>

    <!-- 區塊 B：編輯/填寫會員資料表單 (比照截圖二設計，預設隱藏，新客開啟) -->
    <div id="formSection" class="bg-white rounded-2xl p-6 shadow-sm border border-slate-100 hidden">
      <h3 class="text-lg font-bold text-slate-800 mb-2">編輯會員資訊</h3>
      <p class="text-xs text-slate-500 mb-6">為確保特殊狀況時能與您聯繫，請正確填寫資料以保障您的權益。</p>

      <form id="profileForm" class="space-y-4">
        <!-- 姓名 -->
        <div class="form-control">
          <label class="label"><span class="label-text font-medium">姓名 (Name) <span class="text-error">*</span></span></label>
          <input type="text" id="inputName" required placeholder="請輸入姓名" class="input input-bordered w-full bg-slate-50" />
        </div>

        <!-- 性別 -->
        <div class="form-control">
          <label class="label"><span class="label-text font-medium">性別 (Gender) <span class="text-error">*</span></span></label>
          <div class="grid grid-cols-3 gap-2">
            <label class="btn btn-outline btn-sm has-[:checked]:btn-primary">
              <input type="radio" name="gender" value="男" class="hidden" checked /> 男
            </label>
            <label class="btn btn-outline btn-sm has-[:checked]:btn-primary">
              <input type="radio" name="gender" value="女" class="hidden" /> 女
            </label>
            <label class="btn btn-outline btn-sm has-[:checked]:btn-primary">
              <input type="radio" name="gender" value="其他" class="hidden" /> 其他
            </label>
          </div>
        </div>

        <!-- 生日 -->
        <div class="form-control">
          <label class="label"><span class="label-text font-medium">生日 (Birthday) <span class="text-error">*</span></span></label>
          <input type="date" id="inputBirthday" required class="input input-bordered w-full bg-slate-50" />
        </div>

        <!-- Email -->
        <div class="form-control">
          <label class="label"><span class="label-text font-medium">Email</span></label>
          <input type="email" id="inputEmail" placeholder="example@email.com" class="input input-bordered w-full bg-slate-50" />
        </div>

        <!-- 同意條款與送出 -->
        <div class="form-control mt-4">
          <label class="label cursor-pointer justify-start space-x-2">
            <input type="checkbox" required class="checkbox checkbox-primary checkbox-sm" />
            <span class="label-text text-xs">我已閱讀並同意《個人資料使用條款》</span>
          </label>
        </div>

        <button type="submit" class="btn btn-primary w-full text-white mt-4">確認儲存</button>
      </form>
    </div>

  </main>

  <!-- LIFF 與 n8n 邏輯 Script -->
  <script>
    const N8N_WEBHOOK_URL = 'https://YOUR_N8N_DOMAIN/webhook/liff-user-check'; // 換成您的 n8n URL

    async function initLiff() {
      try {
        await liff.init({ liffId: "YOUR_LIFF_ID" }); // 換成您的 LIFF ID
        if (!liff.isLoggedIn()) {
          liff.login();
          return;
        }

        const profile = await liff.getProfile();
        document.getElementById('cardUserName').innerText = profile.displayName;
        document.getElementById('cardUserId').innerText = `ID: ${profile.userId}`;
        document.getElementById('inputName').value = profile.displayName;

        // 向 n8n 驗證會員身分
        checkUserStatus(profile.userId);

      } catch (error) {
        console.error("LIFF 初始化失敗:", error);
      }
    }

    async function checkUserStatus(userId) {
      try {
        const response = await fetch(N8N_WEBHOOK_URL, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ userId: userId })
        });
        
        const data = await response.json();
        
        // 若為新會員，顯示填表區塊
        if (data.isRegistered === false) {
          document.getElementById('formSection').classList.remove('hidden');
        }
      } catch (err) {
        console.log("n8n 連線檢查：預設允許填寫表單");
        document.getElementById('formSection').classList.remove('hidden');
      }
    }

    // 監聽表單送出
    document.getElementById('profileForm').addEventListener('submit', async (e) => {
      e.preventDefault();
      // 這裡發送資料給 n8n 表單寫入 Webhook
      alert("資料已成功儲存！");
    });

    initLiff();
  </script>
</body>
</html>
