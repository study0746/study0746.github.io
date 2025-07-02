<!DOCTYPE html>
<html lang="zh-Hant" class="scroll-smooth">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>科學探究與實作 | 學期成果報告</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@400;500;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Calm Harmony -->
    <!-- Application Structure Plan: 本應用程式採用單頁滾動式佈局，搭配頂部固定導覽列。此結構能讓使用者對整個學期的內容一目了然，並能快速跳轉至任一專案。選擇此結構而非傳統投影片是為了提供非線性的探索體驗，讓使用者能自由地探索感興趣的內容。每個專案區塊都設計為左右兩欄：左側為文字說明（學習目標、實作挑戰），右側為互動式視覺化元件。這個設計旨在將靜態的報告內容轉化為動態的、可操作的體驗，加深使用者對實驗核心概念的理解。 -->
    <!-- Visualization & Content Choices: 
        - 專案一(抹茶): 目標為展示變因對結果的影響。採用按鈕與滑桿來模擬實驗操作，直接改變色塊顏色並顯示文字說明。此互動方式直觀地重現了實驗的因果關係。
        - 專案二(翻滾仔): 目標為比較不同條件下的結果。使用Chart.js長條圖展示「黏土重量」與「轉動時間」的關係，清晰地呈現比較數據。
        - 專案三(單擺): 目標為展示變數間的趨勢關係。使用Chart.js折線圖呈現「擺長」與「週期」的關係，並加入按鈕切換不同數據集（螺帽 vs 手機），強化了報告中提到的比較分析。
        - 專案四(橡皮筋): 目標為展示科學模型的預測能力。使用Chart.js散佈圖加上趨勢線，並搭配滑桿互動。使用者可透過滑桿輸入變數，即時看到模型預測的結果，這完美地詮釋了實驗的精髓。
        - 專案五(SHM): 目標為展示數據處理的流程。透過圖示化的流程圖（HTML/CSS）搭配按鈕互動，使用者點擊後會顯示計算結果（平均值、標準差等），將抽象的數據分析過程具象化。
        - 總結: 使用卡片式網格佈局展示學到的各項綜合能力，視覺上清晰且易於吸收。-->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Noto Sans TC', sans-serif;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .nav-link {
            transition: all 0.3s ease;
            @apply px-3 py-2 text-sm font-medium text-gray-500 rounded-md hover:bg-emerald-50 hover:text-emerald-700;
        }
        .nav-link.active {
            @apply bg-emerald-100 text-emerald-800;
        }
    </style>
</head>
<body class="bg-stone-50 text-stone-800">

    <nav id="navbar" class="bg-white/80 backdrop-blur-md sticky top-0 z-50 shadow-sm">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex items-center">
                    <span class="text-xl font-bold text-emerald-800">科學探究之旅</span>
                </div>
                <div class="hidden md:block">
                    <div class="ml-10 flex items-baseline space-x-4">
                        <a href="#overview" class="nav-link">課程總覽</a>
                        <a href="#project5" class="nav-link">有效數字與不確定度</a>
                        <a href="#project3" class="nav-link">單擺週期實驗</a>
                        <a href="#project4" class="nav-link">利用橡皮筋秤重</a>
                        <a href="#project2" class="nav-link">翻滾仔變因探討</a>
                        <a href="#project1" class="nav-link">抹茶顏色變化</a>
                        <a href="#summary" class="nav-link">總結</a>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <main class="max-w-7xl mx-auto p-4 sm:p-6 lg:p-8">

        <section id="overview" class="min-h-screen flex flex-col justify-center items-center text-center py-20">
            <h1 class="text-4xl md:text-6xl font-bold text-emerald-900 mb-4">一學期科學探究與實作</h1>
            <p class="text-xl md:text-2xl text-stone-600 mb-8">學習內容與實踐成果</p>
            <div class="w-full max-w-4xl bg-white p-8 rounded-xl shadow-lg">
                <h2 class="text-2xl font-bold text-emerald-800 mb-4">課程總覽</h2>
                <p class="text-stone-700 text-left md:text-center mb-6">本學期的課程核心在於透過一系列的動手實作與數據分析專案，提升學生的科學探究能力。我們不僅學習理論，更將知識應用於解決實際問題，從中培養實驗設計、數據處理及團隊合作的綜合素養。</p>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-4 text-left">
                    <div class="bg-emerald-50 p-4 rounded-lg">
                        <h3 class="font-bold text-emerald-700">🎯 理解物理原理</h3>
                        <p class="text-sm text-emerald-900">深入探討現象背後的科學規律。</p>
                    </div>
                    <div class="bg-emerald-50 p-4 rounded-lg">
                        <h3 class="font-bold text-emerald-700">🔬 掌握實驗設計</h3>
                        <p class="text-sm text-emerald-900">學習規劃、執行與控制變因。</p>
                    </div>
                    <div class="bg-emerald-50 p-4 rounded-lg">
                        <h3 class="font-bold text-emerald-700">📊 學習數據分析</h3>
                        <p class="text-sm text-emerald-900">從數據收集到圖表呈現的完整流程。</p>
                    </div>
                    <div class="bg-emerald-50 p-4 rounded-lg">
                        <h3 class="font-bold text-emerald-700">🤝 培養合作能力</h3>
                        <p class="text-sm text-emerald-900">透過團隊合作解決挑戰與難題。</p>
                    </div>
                </div>
            </div>
        </section>

        <div class="space-y-24">
            
            <section id="project5" class="py-16">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-emerald-800">專案一：有效數字與不確定度</h2>
                    <p class="mt-2 text-lg text-stone-600">運用科技工具進行數據分析與圖表呈現</p>
                    <p class="max-w-3xl mx-auto mt-4 text-stone-700">我們利用智慧型手機內建的感測器和Phyphox應用程式，將手機變成一個強大的科學測量工具，用來記錄簡諧運動(SHM)的數據。本專案的重點在於後續的數據處理，我們在Google試算表中，學習了如何計算平均值、標準差與不確定度，並繪製出符合學術規範的科學圖表。</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">學習目標</h3>
                        <ul class="list-disc list-inside space-y-2 text-stone-700 mb-6">
                            <li><b>手機感測器應用</b>：學習利用手機內建感測器進行科學測量。</li>
                            <li><b>數據處理</b>：掌握試算表函數計算平均值、標準差、不確定度。</li>
                            <li><b>科學圖表繪製</b>：學習繪製包含完整元素（標題、座標軸、單位）的圖表。</li>
                        </ul>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">實作挑戰</h3>
                        <p class="text-stone-700">最大的學習點是從原始數據到最終結論的完整流程。起初，我們面對大量的原始數據感到不知所措。透過課程引導，我們學會使用試算表函數系統性地整理數據，並將計算結果視覺化。這個過程讓我們深刻體會到，數據本身沒有意義，是分析與呈現賦予了它意義。</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg text-center">
                        <h3 class="text-lg font-bold mb-4">數據分析流程模擬</h3>
                        <div class="flex items-center justify-center space-x-4 md:space-x-8 mb-6">
                            <div class="text-center">
                                <div class="text-4xl">📱</div>
                                <p class="text-sm mt-1">手機測量</p>
                            </div>
                            <div class="text-2xl text-stone-400">➡️</div>
                             <div class="text-center">
                                <div class="text-4xl">📊</div>
                                <p class="text-sm mt-1">數據輸入</p>
                            </div>
                            <div class="text-2xl text-stone-400">➡️</div>
                            <div class="text-center">
                                <div class="text-4xl">📈</div>
                                <p class="text-sm mt-1">分析呈現</p>
                            </div>
                        </div>
                        <button id="calculate-shm" class="bg-emerald-600 hover:bg-emerald-700 text-white font-bold py-2 px-6 rounded-full">模擬計算</button>
                        <div id="shm-results" class="mt-4 space-y-2 text-left hidden p-4 bg-emerald-50 rounded-lg">
                           <p><strong>平均週期:</strong> <span id="shm-avg"></span> s</p>
                           <p><strong>標準差:</strong> <span id="shm-std"></span></p>
                           <p><strong>A類不確定度:</strong> <span id="shm-uncertainty"></span></p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="project3" class="py-16">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-emerald-800">專案二：單擺週期實驗與比賽</h2>
                    <p class="mt-2 text-lg text-stone-600">掌握測量不確定度與實驗誤差分析</p>
                    <p class="max-w-3xl mx-auto mt-4 text-stone-700">單擺實驗是物理學的經典。我們不僅僅是驗證理論，更深入學習了「不確定度」的概念，並比較了使用不同擺錘（螺帽 vs. 手機）對測量穩定性的影響。最終，我們將所學應用在一場緊張刺激的單擺計時比賽中。</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 items-center">
                     <div>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">學習目標</h3>
                        <ul class="list-disc list-inside space-y-2 text-stone-700 mb-6">
                            <li><b>單擺週期</b>：理解影響單擺週期的主要因素是擺長。</li>
                            <li><b>不確定度</b>：學習測量不確定度概念與誤差評估。</li>
                            <li><b>實驗比較</b>：比較不同測量物體對週期穩定性的影響。</li>
                        </ul>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">實作挑戰</h3>
                        <p class="text-stone-700">如何精確計時是本實驗最大的挑戰。我們透過測量10次擺動取平均值的方法來減少隨機誤差。分析數據後發現，形狀規整、質量集中的螺帽比手機作為擺錘時的週期更穩定、數據波動更小，這讓我們對理想物理模型與現實情況的差異有了更深刻的認識。</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <div class="chart-container">
                            <canvas id="pendulumChart"></canvas>
                        </div>
                        <div class="mt-4 flex justify-center space-x-2">
                            <button onclick="updatePendulumChart('nut')" class="bg-emerald-200 hover:bg-emerald-300 text-emerald-800 font-bold py-2 px-4 rounded">螺帽數據</button>
                            <button onclick="updatePendulumChart('phone')" class="bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded">手機數據</button>
                        </div>
                         <p class="mt-4 text-center text-stone-600">點擊按鈕切換數據，比較不同擺錘下擺長與週期的關係。可以觀察到螺帽的數據點更貼近理論曲線。</p>
                    </div>
                </div>
            </section>
            
            <section id="project4" class="py-16">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-emerald-800">專案三：利用橡皮筋秤重</h2>
                    <p class="mt-2 text-lg text-stone-600">建立模型與應用彈性定律</p>
                    <p class="max-w-3xl mx-auto mt-4 text-stone-700">這個專案利用常見的橡皮筋來探索虎克定律。我們測量了不同掛重下橡皮筋的伸長量，並學習如何將數據繪製成圖表，更進一步地利用「趨勢線」建立一個數學模型，最後用這個模型來預測未知物體的重量。</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">學習目標</h3>
                        <ul class="list-disc list-inside space-y-2 text-stone-700 mb-6">
                            <li><b>彈性定律</b>：理解串聯與並聯橡皮筋的彈性特性差異。</li>
                            <li><b>數據建模</b>：利用趨-勢線獲得彈力常數，並建立重量估測模型。</li>
                            <li><b>圖表分析</b>：精確繪製科學圖表並解讀其物理意義。</li>
                        </ul>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">實作挑戰</h3>
                        <p class="text-stone-700">實驗的關鍵在於精確測量長度，並將數據點準確地繪製在圖表上。我們學習了如何標準化圖表（座標軸、單位等），並利用試算表工具獲得回歸方程式。最大的挑戰與收穫是，我們成功地將一條數學方程式應用於解決實際問題——秤重，深刻體會到科學模型的預測能力。</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <div class="chart-container">
                            <canvas id="rubberBandChart"></canvas>
                        </div>
                        <div class="mt-4">
                             <label for="weight-slider" class="block text-sm font-medium text-stone-700">拖曳以預測未知重量: <span id="weight-value" class="font-bold text-emerald-700">150</span> gw</label>
                             <input id="weight-slider" type="range" min="50" max="250" value="150" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                             <p class="text-center mt-2">預測總長度: <span id="predicted-length" class="font-bold text-emerald-700"></span> cm</p>
                        </div>
                    </div>
                </div>
            </section>

            <section id="project2" class="py-16">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-emerald-800">專案四：翻滾仔變因探討</h2>
                    <p class="mt-2 text-lg text-stone-600">應用物理原理分析運動現象</p>
                    <p class="max-w-3xl mx-auto mt-4 text-stone-700">在這個專案中，我們親手製作「翻滾仔」裝置，並系統性地改變其結構（如黏土重量），來探究這些變因如何影響它在斜坡上的滾動時間。這個實驗不僅有趣，更讓我們實際應用了課堂上學到的物理攪動量等知識。</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">學習目標</h3>
                        <ul class="list-disc list-inside space-y-2 text-stone-700 mb-6">
                            <li><b>物理應用</b>：運用物理攪動量知識分析裝置運動。</li>
                            <li><b>變因分析</b>：探討裝置結構對轉動時間的影響。</li>
                            <li><b>實驗規劃</b>：學習實驗變因設定及步驟規劃。</li>
                        </ul>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">實作挑戰</h3>
                        <p class="text-stone-700">組裝過程充滿挑戰，例如要確保板子間沒有空隙、轉軸必須穩固。我們透過團隊合作，不斷嘗試與改進，最終加用膠帶成功解決了穩定性問題。實驗中，我們也發現黏土體積對實驗的影響，從而學會了更周全地考慮實驗設計中的潛在問題。</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <div class="chart-container">
                            <canvas id="fanguanzaiChart"></canvas>
                        </div>
                         <p class="mt-4 text-center text-stone-600">圖表顯示，在我們的實驗範圍內，黏土重量的增加並未對轉動時間產生顯著的線性影響，這與初步預測不同，引發了我們對更複雜物理模型的探討。</p>
                    </div>
                </div>
            </section>

            <section id="project1" class="py-16">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-emerald-800">專案五：抹茶顏色變化探究</h2>
                    <p class="mt-2 text-lg text-stone-600">探討變因對物質特性的影響</p>
                    <p class="max-w-3xl mx-auto mt-4 text-stone-700">本專案旨在探討不同環境因素（如酸鹼度與溫度）如何影響抹茶的色澤。我們不僅觀察現象，更學習使用數位工具將顏色變化量化，並分析背後的科學原理。這是一個結合化學、物理與數位分析的跨領域探究。</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 items-center">
                    <div>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">學習目標</h3>
                        <ul class="list-disc list-inside space-y-2 text-stone-700 mb-6">
                            <li><b>變因控制</b>：學習區分操縱變因（酸鹼度、溫度）與控制變因。</li>
                            <li><b>量化分析</b>：學習透過RGB值、亮度和色澤進行顏色量化。</li>
                            <li><b>數據處理</b>：掌握實驗假設設定、數據記錄與圖表製作。</li>
                        </ul>
                        <h3 class="text-xl font-bold mb-2 text-emerald-700">實作挑戰</h3>
                        <p class="text-stone-700">在實作中，我們遇到了粉末測量不易精確、水溫難以恆定等挑戰。透過反覆討論與修正實驗步驟，我們學會了如何系統性地減少實驗誤差，並成功地使用PANTONE Studio程式分析顏色，將數據轉化為有意義的圖表。</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-lg">
                        <h3 class="text-center font-bold text-lg mb-4">抹茶顏色互動模擬</h3>
                        <div id="matcha-display" class="w-full h-48 rounded-lg mb-4 transition-colors duration-500" style="background-color: #789961;"></div>
                        <div class="space-y-4">
                            <div>
                                <label for="temp-slider" class="block text-sm font-medium text-stone-700">溫度: <span id="temp-value">60</span>°C</label>
                                <input id="temp-slider" type="range" min="40" max="80" value="60" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                            </div>
                            <div class="flex space-x-2">
                                <button id="add-acid" class="flex-1 bg-amber-200 hover:bg-amber-300 text-amber-800 font-bold py-2 px-4 rounded">加入檸檬酸</button>
                                <button id="add-base" class="flex-1 bg-indigo-200 hover:bg-indigo-300 text-indigo-800 font-bold py-2 px-4 rounded">加入小蘇打</button>
                                <button id="reset-color" class="flex-1 bg-gray-200 hover:bg-gray-300 text-gray-800 font-bold py-2 px-4 rounded">重置</button>
                            </div>
                        </div>
                        <p id="matcha-result" class="mt-4 text-center text-stone-600 h-10">請選擇一項操作來觀察顏色變化。</p>
                    </div>
                </div>
            </section>
            
            <section id="summary" class="py-16">
                <div class="text-center mb-12">
                    <h2 class="text-3xl font-bold text-emerald-800">總結與學習成果</h2>
                    <p class="mt-2 text-lg text-stone-600">綜合能力的提升</p>
                     <p class="max-w-3xl mx-auto mt-4 text-stone-700">經過一學期的探究與實作，我們不僅累積了科學知識，更重要的是培養了一系列能夠應對未來挑戰的綜合能力。從問題發想到成果發表，我們完整地走過了一遍科學探究的歷程。</p>
                </div>
                 <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <div class="bg-white p-6 rounded-lg shadow-md">
                        <h3 class="font-bold text-lg text-emerald-700 mb-2">🔎 科學探究流程</h3>
                        <p class="text-stone-600">掌握從實驗設計、數據收集到分析與結論的完整方法論。</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md">
                        <h3 class="font-bold text-lg text-emerald-700 mb-2">📈 數據分析能力</h3>
                        <p class="text-stone-600">熟練運用試算表進行數據處理、統計與圖表製作。</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md">
                        <h3 class="font-bold text-lg text-emerald-700 mb-2">💡 問題解決能力</h3>
                        <p class="text-stone-600">面對實驗困難時，學會分析問題並主動尋找解決方案。</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md">
                        <h3 class="font-bold text-lg text-emerald-700 mb-2">👨‍👩‍👧‍👦 團隊合作精神</h3>
                        <p class="text-stone-600">在多個專案中，透過有效的分工與討論，共同完成任務。</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-md">
                        <h3 class="font-bold text-lg text-emerald-700 mb-2">📱 科技應用素養</h3>
                        <p class="text-stone-600">將手機等現代科技工具融入科學實驗，提升探究的效率與深度。</p>
                    </div>
                     <div class="bg-white p-6 rounded-lg shadow-md">
                        <h3 class="font-bold text-lg text-emerald-700 mb-2">🗣️ 成果表達能力</h3>
                        <p class="text-stone-600">學習如何將複雜的實驗過程與結果，清晰地呈現與報告。</p>
                    </div>
                </div>
            </section>
        </div>
    </main>

    <footer class="bg-stone-800 text-white mt-24">
        <div class="max-w-7xl mx-auto py-4 px-4 sm:px-6 lg:px-8 text-center text-sm">
            <p>&copy; 2024 科學探究與實作學習成果報告. All Rights Reserved.</p>
        </div>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            
            const sections = document.querySelectorAll('section');
            const navLinks = document.querySelectorAll('.nav-link');

            const observerOptions = {
                root: null,
                rootMargin: '0px',
                threshold: 0.5
            };

            const observer = new IntersectionObserver((entries, observer) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        navLinks.forEach(link => {
                            link.classList.remove('active');
                            if (link.getAttribute('href').substring(1) === entry.target.id) {
                                link.classList.add('active');
                            }
                        });
                    }
                });
            }, observerOptions);

            sections.forEach(section => {
                observer.observe(section);
            });

            const matchaDisplay = document.getElementById('matcha-display');
            const tempSlider = document.getElementById('temp-slider');
            const tempValue = document.getElementById('temp-value');
            const addAcidBtn = document.getElementById('add-acid');
            const addBaseBtn = document.getElementById('add-base');
            const resetBtn = document.getElementById('reset-color');
            const matchaResult = document.getElementById('matcha-result');
            
            const baseMatchaColor = { r: 120, g: 153, b: 97 };

            function updateMatchaColor() {
                const temp = parseInt(tempSlider.value);
                tempValue.textContent = temp;
                const tempFactor = (temp - 40) / 40; 
                const r = Math.round(baseMatchaColor.r + tempFactor * 20); 
                const g = Math.round(baseMatchaColor.g - tempFactor * 20); 
                const b = Math.round(baseMatchaColor.b);
                matchaDisplay.style.backgroundColor = `rgb(${r}, ${g}, ${b})`;
                matchaResult.textContent = '溫度改變會影響抹茶的色澤。';
            }

            tempSlider.addEventListener('input', updateMatchaColor);
            addAcidBtn.addEventListener('click', () => {
                matchaDisplay.style.backgroundColor = '#B5C48A'; // More yellow-green
                matchaResult.textContent = '加入酸性物質，抹茶顏色變黃綠色。';
            });
            addBaseBtn.addEventListener('click', () => {
                matchaDisplay.style.backgroundColor = '#5E816B'; // Darker, duller green
                matchaResult.textContent = '加入鹼性物質，抹茶顏色變暗綠色。';
            });
            resetBtn.addEventListener('click', () => {
                tempSlider.value = 60;
                tempValue.textContent = '60';
                matchaDisplay.style.backgroundColor = `rgb(${baseMatchaColor.r}, ${baseMatchaColor.g}, ${baseMatchaColor.b})`;
                matchaResult.textContent = '顏色已重置。請選擇操作。';
            });

            var fanguanzaiCtx = document.getElementById('fanguanzaiChart').getContext('2d');
            var fanguanzaiChart = new Chart(fanguanzaiCtx, {
                type: 'bar',
                data: {
                    labels: ['5g', '10g', '15g', '20g'],
                    datasets: [{
                        label: '轉動時間 (s)',
                        data: [5.2, 5.5, 5.3, 5.6],
                        backgroundColor: 'rgba(52, 211, 153, 0.5)',
                        borderColor: 'rgba(5, 150, 105, 1)',
                        borderWidth: 1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: true,
                            title: { display: true, text: '時間 (秒)' }
                        },
                        x: {
                            title: { display: true, text: '黏土重量' }
                        }
                    },
                    plugins: {
                        title: { display: true, text: '黏土重量對翻滾仔轉動時間的影響' },
                        legend: { display: false }
                    }
                }
            });
            
            const pendulumData = {
                nut: {
                    labels: [0.2, 0.4, 0.6, 0.8, 1.0],
                    data: [0.90, 1.27, 1.55, 1.79, 2.01],
                    label: '螺帽平均週期'
                },
                phone: {
                    labels: [0.2, 0.4, 0.6, 0.8, 1.0],
                    data: [0.95, 1.35, 1.60, 1.75, 2.10],
                    label: '手機平均週期'
                }
            };
            var pendulumCtx = document.getElementById('pendulumChart').getContext('2d');
            var pendulumChart = new Chart(pendulumCtx, {
                type: 'line',
                data: {
                    labels: pendulumData.nut.labels,
                    datasets: [{
                        label: pendulumData.nut.label,
                        data: pendulumData.nut.data,
                        borderColor: 'rgba(13, 148, 136, 1)',
                        backgroundColor: 'rgba(13, 148, 136, 0.2)',
                        fill: false,
                        tension: 0.1
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        y: {
                            beginAtZero: false,
                            title: { display: true, text: '週期 (秒)' }
                        },
                        x: {
                            title: { display: true, text: '擺長 (m)' }
                        }
                    },
                    plugins: {
                        title: { display: true, text: '單擺週期與擺長的關係' }
                    }
                }
            });
            
            window.updatePendulumChart = function(type) {
                const { labels, data, label } = pendulumData[type];
                pendulumChart.data.labels = labels;
                pendulumChart.data.datasets[0].data = data;
                pendulumChart.data.datasets[0].label = label;
                pendulumChart.update();
            };

            const rubberBandData = {
                points: [
                    {x: 50.4, y: 22.04}, {x: 70.6, y: 23.6}, {x: 90.8, y: 25.1}, 
                    {x: 111, y: 26.8}, {x: 131.2, y: 28.5}, {x: 151.4, y: 30.2}
                ],
                equation: { m: 0.0773, b: 16.8 } 
            };
            const rubberBandCtx = document.getElementById('rubberBandChart').getContext('2d');
            const rubberBandChart = new Chart(rubberBandCtx, {
                type: 'scatter',
                data: {
                    datasets: [
                        {
                            label: '實驗數據',
                            data: rubberBandData.points,
                            backgroundColor: 'rgba(239, 68, 68, 0.7)',
                        },
                        {
                            label: '趨勢線 (y=0.0773x + 16.8)',
                            data: rubberBandData.points.map(p => ({x: p.x, y: rubberBandData.equation.m * p.x + rubberBandData.equation.b})),
                            type: 'line',
                            fill: false,
                            borderColor: 'rgba(30, 64, 175, 0.7)',
                            tension: 0.1,
                            pointRadius: 0
                        },
                        {
                            label: '預測點',
                            data: [],
                            backgroundColor: 'rgba(16, 185, 129, 1)',
                            pointStyle: 'crossRot',
                            radius: 10,
                            borderWidth: 3
                        }
                    ]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    scales: {
                        x: {
                            type: 'linear',
                            position: 'bottom',
                            title: { display: true, text: '外力 (gw)' }
                        },
                        y: {
                            title: { display: true, text: '總長度 (cm)' }
                        }
                    },
                    plugins: {
                        title: { display: true, text: '橡皮筋外力與總長度關係' },
                        tooltip: {
                             callbacks: {
                                label: function(context) {
                                    let label = context.dataset.label || '';
                                    if (label) {
                                        label += ': ';
                                    }
                                    if (context.parsed.y !== null) {
                                        label += `(${context.parsed.x.toFixed(1)} gw, ${context.parsed.y.toFixed(2)} cm)`;
                                    }
                                    return label;
                                }
                            }
                        }
                    }
                }
            });

            const weightSlider = document.getElementById('weight-slider');
            const weightValue = document.getElementById('weight-value');
            const predictedLength = document.getElementById('predicted-length');
            
            function updatePrediction() {
                const weight = parseFloat(weightSlider.value);
                weightValue.textContent = weight.toFixed(1);
                const length = rubberBandData.equation.m * weight + rubberBandData.equation.b;
                predictedLength.textContent = length.toFixed(2);
                
                rubberBandChart.data.datasets[2].data = [{x: weight, y: length}];
                rubberBandChart.update();
            }
            weightSlider.addEventListener('input', updatePrediction);
            updatePrediction();

            const calculateShmBtn = document.getElementById('calculate-shm');
            const shmResultsDiv = document.getElementById('shm-results');
            calculateShmBtn.addEventListener('click', () => {
                const data = [1.236, 1.219, 1.225, 1.251, 1.236];
                const sum = data.reduce((a, b) => a + b, 0);
                const avg = sum / data.length;
                const variance = data.reduce((acc, val) => acc + Math.pow(val - avg, 2), 0) / (data.length - 1);
                const std = Math.sqrt(variance);
                const uncertainty = std / Math.sqrt(data.length);
                
                document.getElementById('shm-avg').textContent = avg.toFixed(4);
                document.getElementById('shm-std').textContent = std.toFixed(6);
                document.getElementById('shm-uncertainty').textContent = uncertainty.toFixed(6);
                
                shmResultsDiv.classList.remove('hidden');
            });

        });
    </script>
</body>
</html>

