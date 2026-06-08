# social
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>청소년 MBTI 1000만원 5대 자산 포트폴리오 테스트</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons for visual enhancements -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Noto Sans KR -->
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background: linear-gradient(135deg, #f8fafc 0%, #e2e8f0 100%);
        }
        /* Chart rotation and smooth animation */
        .chart-svg {
            transform: rotate(-90deg);
        }
        .chart-segment {
            transition: stroke-dasharray 1s ease-out, stroke 0.5s, stroke-width 0.3s;
            cursor: pointer;
        }
        .chart-segment:hover {
            stroke-width: 6;
        }
    </style>
</head>
<body class="min-h-screen text-slate-800 antialiased flex flex-col justify-between">

    <!-- Header -->
    <header class="bg-white/90 backdrop-blur-md border-b border-slate-200 sticky top-0 z-50 shadow-sm">
        <div class="max-w-4xl mx-auto px-4 h-16 flex items-center justify-between">
            <div class="flex items-center gap-2 cursor-pointer" onclick="resetTest()">
                <div class="w-10 h-10 bg-gradient-to-tr from-indigo-600 to-violet-600 rounded-xl flex items-center justify-center text-white shadow-md shadow-indigo-100">
                    <i class="fa-solid fa-graduation-cap text-lg">🎓</i>
                </div>
                <span class="font-black text-lg tracking-tight bg-gradient-to-r from-indigo-600 to-violet-600 bg-clip-text text-transparent">교과서 연계 자산관리 멘토</span>
            </div>
            <div class="text-xs bg-indigo-50 text-indigo-700 font-bold px-3 py-1.5 rounded-full border border-indigo-100">
                중3 사회·가정 100% 반영
            </div>
        </div>
    </header>

    <!-- Main Content Area -->
    <main class="flex-grow max-w-2xl w-full mx-auto px-4 py-8 flex flex-col justify-center">
        
        <!-- START PAGE -->
        <div id="start-page" class="bg-white rounded-3xl shadow-xl shadow-slate-200/60 p-6 md:p-10 border border-slate-100 text-center transition-all duration-300">
            <span class="text-xs font-bold text-indigo-600 bg-indigo-50 border border-indigo-100 rounded-full px-3.5 py-1.5 uppercase tracking-wide">
                My Textbook 5-Asset Planner
            </span>
            <h1 class="text-3xl md:text-4xl font-black mt-4 text-slate-900 leading-tight">
                교과서 속 자산관리 <br class="sm:hidden"><span class="text-indigo-600">1,000만 원</span>으로 실전 연습!💰
            </h1>
            <p class="text-sm md:text-base text-slate-500 mt-4 leading-relaxed max-w-md mx-auto">
                중3 일상 상황을 통해 나의 MBTI 성향을 확인하고, 교과서에 등장하는 핵심 5대 금융자산인 <strong>예금·적금·주식·채권·부동산</strong>에 1,000만 원을 배분하여 금융 지혜를 완벽하게 터득해 보세요!
            </p>
            
            <div class="my-8 flex justify-center">
                <div class="relative w-44 h-44 bg-gradient-to-tr from-indigo-50 to-violet-50 rounded-full flex items-center justify-center animate-pulse">
                    <svg class="w-28 h-28" viewBox="0 0 100 100" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <circle cx="50" cy="50" r="45" fill="#EEF2F6"/>
                        <!-- Stack of coins representing 5 assets -->
                        <rect x="35" y="30" width="30" height="8" rx="3" fill="#10B981" />
                        <rect x="35" y="40" width="30" height="8" rx="3" fill="#3B82F6" />
                        <rect x="35" y="50" width="30" height="8" rx="3" fill="#F59E0B" />
                        <rect x="35" y="60" width="30" height="8" rx="3" fill="#EF4444" />
                        <rect x="35" y="70" width="30" height="8" rx="3" fill="#EC4899" />
                    </svg>
                </div>
            </div>

            <button onclick="startTest()" class="w-full sm:w-auto px-10 py-4 bg-gradient-to-r from-indigo-600 to-violet-600 hover:from-indigo-700 hover:to-violet-700 text-white font-bold text-lg rounded-2xl shadow-lg shadow-indigo-200 transition-all transform hover:-translate-y-0.5 active:translate-y-0">
                5대 자산 투자 모의테스트 시작 <i class="fa-solid fa-chevron-right ml-1"></i>
            </button>

            <div class="mt-6 flex justify-center items-center gap-6 text-xs text-slate-400 font-medium">
                <span><i class="fa-regular fa-clock mr-1"></i> 소요시간 약 1분</span>
                <span><i class="fa-solid fa-list-check mr-1"></i> 중3 금융교과 연계 12문항</span>
            </div>
        </div>

        <!-- TEST PAGE (HIDDEN BY DEFAULT) -->
        <div id="test-page" class="hidden bg-white rounded-3xl shadow-xl shadow-slate-200/60 p-6 md:p-10 border border-slate-100 transition-all duration-300">
            <!-- Progress Bar -->
            <div class="mb-8">
                <div class="flex justify-between items-center text-xs text-slate-400 font-bold mb-2">
                    <span id="progress-text" class="text-indigo-600 bg-indigo-50 px-2.5 py-1 rounded">질문 1 / 12</span>
                    <span id="progress-percentage">8%</span>
                </div>
                <div class="w-full bg-slate-100 rounded-full h-2">
                    <div id="progress-bar" class="bg-indigo-600 h-2 rounded-full transition-all duration-300" style="width: 8.3%"></div>
                </div>
            </div>

            <!-- Question Body -->
            <div class="min-h-[110px] mb-8">
                <span class="text-xs font-bold text-indigo-500 tracking-wide uppercase" id="question-category">외향 vs 내향</span>
                <h2 id="question-title" class="text-xl md:text-2xl font-black text-slate-900 mt-2 leading-snug">
                    질문 내용 로딩 중...
                </h2>
            </div>

            <!-- Options Area -->
            <div class="space-y-4" id="options-container">
                <!-- Option Buttons Dynamic Insertion -->
            </div>
        </div>

        <!-- LOADING PAGE (HIDDEN BY DEFAULT) -->
        <div id="loading-page" class="hidden bg-white rounded-3xl shadow-xl shadow-slate-200/60 p-10 border border-slate-100 text-center transition-all duration-300">
            <div class="flex flex-col items-center justify-center py-12">
                <div class="relative w-24 h-24 mb-6 flex items-center justify-center">
                    <div class="absolute inset-0 rounded-full border-4 border-slate-100"></div>
                    <div class="absolute inset-0 rounded-full border-4 border-indigo-600 border-t-transparent animate-spin"></div>
                    <span class="text-2xl animate-bounce">📈</span>
                </div>
                <h3 class="text-xl font-bold text-slate-900">5대 자산 포트폴리오 기획 중</h3>
                <p class="text-slate-400 text-sm mt-2">안전성·수익성·유동성 3대 법칙을 계산하여<br>학생의 MBTI 맞춤형 황금 비율을 연계 중입니다.</p>
            </div>
        </div>

        <!-- RESULT PAGE (HIDDEN BY DEFAULT) -->
        <div id="result-page" class="hidden transition-all duration-300 space-y-6">
            
            <!-- Result Overview Card -->
            <div class="bg-white rounded-3xl shadow-xl shadow-slate-200/60 p-6 md:p-10 border border-slate-100">
                <div class="text-center">
                    <div id="result-badge" class="inline-block px-4 py-1.5 bg-gradient-to-r from-indigo-50 to-violet-50 border border-indigo-100 rounded-full text-sm font-extrabold text-indigo-700 tracking-wider">
                        ESTJ
                    </div>
                    <h2 id="result-title" class="text-2xl md:text-3xl font-black text-slate-900 mt-4 leading-tight">
                        체계적이고 똑부러지는 '꼬마 자산가'
                    </h2>
                    <p id="result-desc" class="text-sm text-slate-500 mt-3 leading-relaxed max-w-md mx-auto">
                        꼼꼼하고 계획적인 당신을 위한 맞춤 금융 진단서입니다.
                    </p>
                </div>

                <hr class="my-6 border-slate-100">

                <!-- Core Investment Characteristics -->
                <div>
                    <h3 class="font-bold text-slate-900 text-base mb-4 flex items-center gap-2">
                        <span>🔍</span> 나의 주니어 금융 행동 요약
                    </h3>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-3" id="character-traits">
                        <!-- Filled in dynamically -->
                    </div>
                </div>
            </div>

            <!-- Visual & Legible Portfolio Ratio Card -->
            <div class="bg-white rounded-3xl shadow-xl shadow-slate-200/60 p-6 md:p-8 border border-slate-100">
                <div class="flex items-center justify-between mb-2">
                    <h3 class="font-black text-slate-900 text-lg flex items-center gap-2">
                        <span>📊</span> 교과서 속 5대 자산 포트폴리오
                    </h3>
                    <span class="text-xs bg-indigo-50 text-indigo-700 font-extrabold px-3 py-1 rounded-full border border-indigo-100">예산: 10,000,000원</span>
                </div>
                <p class="text-slate-500 text-xs leading-relaxed mb-6">
                    예금, 적금, 주식, 채권, 부동산 5대 자산을 활용해 나의 성향에 최적화된 포트폴리오를 설계했습니다. 차트에 마우스나 터치로 각 조각을 확인하면 1,000만 원 중 <strong>배정된 금액</strong>을 실시간으로 확인해 보실 수 있습니다.
                </p>

                <!-- Interactive 5-Asset Donut Chart Area -->
                <div class="flex flex-col md:flex-row items-center justify-center gap-8 mb-8 p-6 bg-slate-50 rounded-3xl border border-slate-100">
                    <!-- SVG Donut Chart container with 5 segment paths -->
                    <div class="relative w-52 h-52 flex items-center justify-center shrink-0 animate-fade-in">
                        <svg class="chart-svg w-full h-full" viewBox="0 0 42 42">
                            <!-- Inner empty area to block line joins and provide contrast -->
                            <circle cx="21" cy="21" r="15.91549430918954" fill="white"></circle>
                            <!-- Segments dynamically drawn by JS (now 5 segments!) -->
                            <circle id="donut-segment-1" class="chart-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#10B981" stroke-width="4"></circle>
                            <circle id="donut-segment-2" class="chart-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#3B82F6" stroke-width="4"></circle>
                            <circle id="donut-segment-3" class="chart-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#EF4444" stroke-width="4"></circle>
                            <circle id="donut-segment-4" class="chart-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#F59E0B" stroke-width="4"></circle>
                            <circle id="donut-segment-5" class="chart-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#EC4899" stroke-width="4"></circle>
                        </svg>
                        
                        <!-- Center Label inside the Donut hole -->
                        <div class="absolute inset-0 flex flex-col items-center justify-center text-center pointer-events-none p-4">
                            <span id="donut-center-label" class="text-xs text-slate-400 font-extrabold tracking-wide">총 투자 금액</span>
                            <span id="donut-center-value" class="text-base font-black text-indigo-600 leading-tight">1,000만 원</span>
                        </div>
                    </div>

                    <!-- Side Color Index with Quick Readability -->
                    <div class="flex-grow space-y-3 w-full">
                        <div class="text-xs text-slate-400 font-bold border-b border-slate-200 pb-2 flex justify-between">
                            <span>5대 자산 분류</span>
                            <span id="risk-badge-text" class="text-indigo-600 font-black">성향 위험등급</span>
                        </div>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-3" id="donut-color-legend">
                            <!-- Dynamic Index legend list -->
                        </div>
                    </div>
                </div>

                <!-- 2. Detailed Breakdown rows with progress bars for perfect readability & Real Money values -->
                <div class="space-y-4" id="portfolio-list">
                    <!-- Dynamic Injection of Cash, Installment Savings, Stocks, Bonds, Real Estate with colorful layout -->
                </div>
            </div>

            <!-- PORTFOLIO ELEMENTARY EXPLANATIONS (STUDENT LEVEL) -->
            <div class="bg-white rounded-3xl shadow-xl shadow-slate-200/60 p-6 md:p-8 border border-slate-100">
                <h3 class="font-bold text-slate-900 text-base mb-4 flex items-center gap-2">
                    📚 중3 교과서 자산관리 핵심 정리 (안전성·수익성·유동성)
                </h3>
                
                <div class="space-y-4 text-xs md:text-sm text-slate-600 leading-relaxed">
                    <!-- Explain 예금 -->
                    <div class="flex gap-3 p-4 bg-emerald-50/50 rounded-2xl border border-emerald-100">
                        <span class="text-2xl mt-0.5 shrink-0">🛡️</span>
                        <div>
                            <p class="font-extrabold text-emerald-800 text-sm">1. 예금: “언제든 꺼내 쓸 수 있는 최고의 유동성!”</p>
                            <p class="mt-1 text-slate-500">목돈을 한 번에 은행에 맡기는 자산입니다. 수시입출금식 예금은 필요할 때 현금으로 바로 출금할 수 있어 **유동성(환금성)**이 극대화된 강력한 보관 장치입니다. (안전성 높음, 수익성 낮음, 유동성 매우 높음)</p>
                        </div>
                    </div>

                    <!-- Explain 적금 -->
                    <div class="flex gap-3 p-4 bg-blue-50/50 rounded-2xl border border-blue-100">
                        <span class="text-2xl mt-0.5 shrink-0">📅</span>
                        <div>
                            <p class="font-extrabold text-blue-800 text-sm">2. 적금: “용돈을 쪼개어 차곡차곡 쌓는 최고의 목돈 파트너!”</p>
                            <p class="mt-1 text-slate-500">매달 정해진 날에 일정한 용돈을 저금하여 만기일에 큰돈으로 돌려받는 예금의 일종입니다. 꾸준한 저축 습관을 들여 큰 비용이 필요할 때를 대비하는 대표 자산입니다. (안전성 매우 높음, 수익성 낮음, 유동성 보통)</p>
                        </div>
                    </div>

                    <!-- Explain 채권 -->
                    <div class="flex gap-3 p-4 bg-red-50/50 rounded-2xl border border-red-100">
                        <span class="text-2xl mt-0.5 shrink-0">🤝</span>
                        <div>
                            <p class="font-extrabold text-red-800 text-sm">3. 채권: “국가나 대기업에 차용증을 쓰고 받아오는 이자 기계!”</p>
                            <p class="mt-1 text-slate-500">정부나 공공기관, 대기업이 대규모 자금을 조달하기 위해 돈을 빌리고 이자를 약속하는 '채무 증서'입니다. 은행 예금보다는 수익성이 좋고 우량주식보다는 안전한 중간급 자산입니다. (안전성 보통, 수익성 보통, 유동성 보통)</p>
                        </div>
                    </div>

                    <!-- Explain 주식 -->
                    <div class="flex gap-3 p-4 bg-amber-50/50 rounded-2xl border border-amber-100">
                        <span class="text-2xl mt-0.5 shrink-0">🚀</span>
                        <div>
                            <p class="font-extrabold text-amber-800 text-sm">4. 주식: “기업의 일원이 되어 가치를 공유하는 대박 마차!”</p>
                            <p class="mt-1 text-slate-500">주식회사의 지분을 소유하는 증서입니다. 회사가 번창하면 주가가 오르고 배당금을 받아 아주 높은 **수익성**을 올리지만, 반대로 원금을 완전히 잃을 수 있는 위험성도 따릅니다. (안전성 낮음, 수익성 매우 높음, 유동성 높음)</p>
                        </div>
                    </div>

                    <!-- Explain 부동산 -->
                    <div class="flex gap-3 p-4 bg-pink-50/50 rounded-2xl border border-pink-100">
                        <span class="text-2xl mt-0.5 shrink-0">🏢</span>
                        <div>
                            <p class="font-extrabold text-pink-800 text-sm">5. 부동산: “실물 자산의 가치와 매월 들어오는 조용한 임대 거위!”</p>
                            <p class="mt-1 text-slate-500">토지와 건물처럼 고정된 실물 자산입니다. 종이돈의 가치가 폭락하는 물가 상승(인플레이션) 시기에 실물 가치를 철저히 방어할 수 있어 장기적으로 우수한 투자 수단입니다. (안전성 높음, 수익성 보통, 유동성 매우 낮음)</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Expert's Feedback / Opinion Card (PRO ADVICE) -->
            <div class="bg-gradient-to-br from-indigo-950 to-slate-900 text-white rounded-3xl shadow-xl p-6 md:p-10 relative overflow-hidden">
                <div class="absolute -top-10 -right-10 w-48 h-48 bg-indigo-700/20 rounded-full blur-3xl"></div>
                <div class="absolute -bottom-10 -left-10 w-48 h-48 bg-violet-700/20 rounded-full blur-3xl"></div>
                
                <div class="relative z-10">
                    <div class="flex items-center gap-3 mb-4">
                        <div class="w-12 h-12 rounded-full bg-indigo-500/20 border border-indigo-400/40 flex items-center justify-center text-xl shadow-lg">
                            🎓
                        </div>
                        <div>
                            <span class="text-[11px] font-bold uppercase tracking-wider text-indigo-300">PROFESSIONAL PORTFOLIO ADVICE</span>
                            <h4 class="text-base md:text-lg font-black text-white">투자자산운용가 멘토의 1,000만 원 5대 자산 관리 조언</h4>
                        </div>
                    </div>

                    <div class="bg-indigo-900/40 border border-indigo-800/60 rounded-2xl p-5 md:p-6 text-sm text-indigo-100 leading-relaxed space-y-4">
                        <div id="expert-opinion">
                            <!-- Dynamically loaded professional investment reasoning -->
                        </div>
                    </div>

                    <!-- Teenager Safeguard Rules -->
                    <div class="mt-6 pt-6 border-t border-indigo-800/60 flex items-start gap-2 text-xs text-indigo-300">
                        <span class="text-amber-400 font-bold"><i class="fa-solid fa-circle-exclamation"></i> 주의:</span>
                        <p>본 포트폴리오는 경제 자산관리 원리와 MBTI 성격을 융합해 설계된 교육 모의 모델입니다. 1,000만 원이라는 한정된 예산을 똑 부러지게 5대 자산으로 쪼개서 저축하고 지키는 습관을 키우는 용도로 활용해 주세요.</p>
                    </div>
                </div>
            </div>

            <!-- Action Buttons -->
            <div class="flex flex-col sm:flex-row gap-4">
                <button onclick="resetTest()" class="flex-1 py-4 bg-slate-200 hover:bg-slate-300 text-slate-700 font-bold rounded-2xl transition-all">
                    테스트 다시하기 <i class="fa-solid fa-rotate-left ml-1"></i>
                </button>
                <button onclick="copyShareLink()" class="flex-1 py-4 bg-gradient-to-r from-indigo-600 to-violet-600 hover:from-indigo-700 hover:to-violet-700 text-white font-bold rounded-2xl shadow-lg shadow-indigo-100 transition-all">
                    내 성향 친구들과 비교하기 <i class="fa-solid fa-share-nodes ml-1"></i>
                </button>
            </div>
            
            <div id="copy-toast" class="hidden text-center text-xs text-indigo-600 font-semibold mt-2">
                링크가 안전하게 복사되었습니다! 친구들에게 공유해보세요.
            </div>
        </div>

    </main>

    <!-- Footer -->
    <footer class="bg-slate-900 text-slate-400 py-6 mt-12 text-center text-xs border-t border-slate-800">
        <div class="max-w-4xl mx-auto px-4">
            <p class="font-semibold text-slate-300 mb-1">© 2026 주니어 금융투자 아카데미</p>
            <p>본 서비스는 중학교 경제 단원에 연계하여 제작된 청소년 교육용 포트폴리오 저작물입니다.</p>
        </div>
    </footer>

    <!-- MBTI Logic Script -->
    <script>
        // 12 Questions tailored for Middle School Grade 3 (16 years old)
        // Testing E/I, S/N, T/F, J/P dimensions (3 questions for each dimension)
        const questions = [
            // E vs I (Extraversion vs Introversion)
            {
                id: 1,
                category: "E vs I (외향성 vs 내향성)",
                title: "새학기 첫날 쉬는 시간, 마음에 드는 친구를 봤을 때 나의 행동은?",
                options: [
                    { text: "“안녕! 나 3반이었던 OOO인데!” 먼저 다가가 말을 붙이며 번호를 교환한다.", score: { E: 1, I: 0 } },
                    { text: "어떻게 말을 걸까 속으로 고민만 하다가 쉬는 시간이 가버려 다음을 기약한다.", score: { E: 0, I: 1 } }
                ]
            },
            {
                id: 2,
                category: "E vs I (외향성 vs 내향성)",
                title: "이번 설에 받은 두둑한 세뱃돈 중 일부를 친구와 쓸 예정이라면?",
                options: [
                    { text: "시끄럽고 사람이 붐비는 핫플 마라탕 가게나 코인노래방으로 친구들을 모은다.", score: { E: 1, I: 0 } },
                    { text: "단짝 단 한 명만 불러서 조용한 만화카페나 동네 분식점에서 수다를 떤다.", score: { E: 0, I: 1 } }
                ]
            },
            {
                id: 3,
                category: "E vs I (외향성 vs 내향성)",
                title: "금융 모둠 수행평가 시간에 역할을 나눌 때 더 끌리는 쪽은?",
                options: [
                    { text: "마이크를 잡고 앞에 나가 모둠 발표를 리드하는 '대표 연사'형", score: { E: 1, I: 0 } },
                    { text: "화면 뒤에서 조용히 대본을 작성하고 자료를 조사하는 '백스테이지 전략가'형", score: { E: 0, I: 1 } }
                ]
            },
            // S vs N (Sensing vs Intuition)
            {
                id: 4,
                category: "S vs N (감각성 vs 직관성)",
                title: "용돈 지출 관리를 위해 잔액 조회를 할 때 나의 모습은?",
                options: [
                    { text: "통장 잔액이나 현금 파우치에 있는 원화 단위를 한 자리 숫자까지 정확하게 센다.", score: { S: 1, N: 0 } },
                    { text: "“아마 한 3만 원 정도 대충 남아있겠지?” 눈대중으로 계산하고 깊이 신경 쓰지 않는다.", score: { S: 0, N: 1 } }
                ]
            },
            {
                id: 5,
                category: "S vs N (감각성 vs 직관성)",
                title: "선생님이 가르쳐주신 미래 ‘가상현실/메타버스’ 기업 뉴스를 보고 든 생각은?",
                options: [
                    { text: "“그 회사 작년 매출은 얼마지? 현실적으로 서비스 가격은 합리적인가?”에 호기심이 생긴다.", score: { S: 1, N: 0 } },
                    { text: "“가상세계 상점에서 건물주가 되면 현실처럼 월세를 받을 수 있을까?” 상상의 나래를 편다.", score: { S: 0, N: 1 } }
                ]
            },
            {
                id: 6,
                category: "S vs N (감각성 vs 직관성)",
                title: "목표를 정해 저금통에 돈을 모을 때 나의 기준은?",
                options: [
                    { text: "다음 달 콘서트 티켓 값, 혹은 새로 나올 패딩 등 실질적이고 구체적인 목표가 우선이다.", score: { S: 1, N: 0 } },
                    { text: "나중에 대학생이 되거나 어른이 되었을 때 쓸 원대한 ‘시드머니(종잣돈)’라는 개념이 우선이다.", score: { S: 0, N: 1 } }
                ]
            },
            // T vs F (사고형 vs 감정형)
            {
                id: 7,
                category: "T vs F (사고형 vs 감정형)",
                title: "친한 단짝이 투자 공부를 하겠다며 주식을 샀다가 용돈의 절반을 잃었다며 울상일 때 나는?",
                options: [
                    { text: "“어떤 기업 주식을 샀는데 그래? 재무 보고서나 실적 확인은 제대로 해보고 들어갔어?” 분석을 돕는다.", score: { T: 1, F: 0 } },
                    { text: "“헐... 어떡해... 진짜 속상하겠다. 떡볶이라도 먹으면서 일단 기분부터 풀자.” 마음을 공감해준다.", score: { T: 0, F: 1 } }
                ]
            },
            {
                id: 8,
                category: "T vs F (사고형 vs 감정형)",
                title: "세계적으로 환경 오염을 극복하기 위해 노력하는 ‘ESG 착한 기업’ 기사를 읽었다면?",
                options: [
                    { text: "취지는 좋아도 결국 수익률과 안정성이 떨어지는 기업이면 투자 메리트가 없다고 냉정히 본다.", score: { T: 1, F: 0 } },
                    { text: "지구를 구하는 착한 기업들의 지분을 아주 조금이라도 사주며 주주로서 동참해야 한다고 믿는다.", score: { T: 0, F: 1 } }
                ]
            },
            {
                id: 9,
                category: "T vs F (사고형 vs 감정형)",
                title: "학교 경제동아리 팀원을 뽑는 자리에서 더 동반하고 싶은 동료는?",
                options: [
                    { text: "평소 무뚝뚝하지만 컴퓨터나 엑셀 수치를 능숙하게 다루어 성과를 보장해줄 사람", score: { T: 1, F: 0 } },
                    { text: "서툴더라도 매 회의마다 긍정적인 파이팅을 불어넣고 소통이 잘 통하는 리액션 리더", score: { T: 0, F: 1 } }
                ]
            },
            // J vs P (판단형 vs 인식형)
            {
                id: 10,
                category: "J vs P (판단형 vs 인식형)",
                title: "매달 부모님께 고정적으로 용돈을 받는 시기, 나는 어떻게 자금을 관리할까?",
                options: [
                    { text: "받자마자 ‘식비 40%, 예금 30%, 잡화 30%’ 처럼 구체적인 예산부터 쪼개서 분배한다.", score: { J: 1, P: 0 } },
                    { text: "별도 계획 없이 필요한 상황이 올 때마다 유동적으로 꺼내 쓰고 잔액에 몸을 맡긴다.", score: { J: 0, P: 1 } }
                ]
            },
            {
                id: 11,
                category: "J vs P (판단형 vs 인식형)",
                title: "중요한 시험기간, 목표를 위한 나의 공부 스타일은?",
                options: [
                    { text: "주차별, 요일별로 쪼갠 학습 계획표를 미리 정교하게 수립하고 이를 최대한 클리어한다.", score: { J: 1, P: 0 } },
                    { text: "그날그날 유난히 집중이 잘 되는 과목 위주로 임기응변식의 벼락치기를 주도한다.", score: { J: 0, P: 1 } }
                ]
            },
            {
                id: 12,
                category: "J vs P (판단형 vs 인식형)",
                title: "가상 자산 거래소 모의 투자 앱을 처음 설치했을 때 나의 대응은?",
                options: [
                    { text: "앱 이용 가이드와 자산별 거래 규칙을 하나하나 완벽하게 독파한 뒤 첫 거래를 체결한다.", score: { J: 1, P: 0 } },
                    { text: "일단 현재 시세 화면에 가장 눈에 띄게 차트가 오르내리는 핫한 자산부터 바로 구매하며 체득한다.", score: { J: 0, P: 1 } }
                ]
            }
        ];

        // 16 MBTI Results with 5-Asset Allocation: 예금, 적금, 채권, 주식, 부동산
        // Ratios match MBTI personality profile while maintaining high pedagogical value.
        const mbtiOutcomes = {
            "ISTJ": {
                title: "철벽 수비형 ‘자산 방패 대장’",
                desc: "원칙을 목숨처럼 지키는 초강력 안정 투자자입니다. 잃지 않는 투자를 최우선으로 선호합니다.",
                traits: ["#손실방지_최우선", "#확정금리_바라기", "#꼼꼼한_자산정리", "#원칙주의자"],
                riskLabel: "매우 안정적 (안전제일)",
                portfolio: [
                    { name: "예금", value: 30, color: "#10B981", productName: "수시 입출금식 통장 (유동성 확보)", detail: "언제든지 필요한 공부용품이나 용돈이 필요할 때 은행 수수료 없이 즉각 출금할 수 있는 총알 예금입니다." },
                    { name: "적금", value: 40, color: "#3B82F6", productName: "청소년 정기적금 (확정 금리형)", detail: "매달 정해진 용돈 날에 일정 금액을 강제 저축해 만기 시점에 고정 보장 이율과 완벽한 목돈을 만듭니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "대한민국 AAA급 우량 장기 국채", detail: "국가가 무너지지 않는 한 이자를 약속대로 꼬박꼬박 내어주는 튼튼한 국고채 펀드에 일부 자금을 넣습니다." },
                    { name: "주식", value: 10, color: "#F59E0B", productName: "글로벌 시장 대표 지수 ETF", detail: "가장 거래 규율이 선명한 상위 500대 기업 세트에 분산 투자하여 최소한의 시장 성장을 탑승합니다." },
                    { name: "부동산", value: 5, color: "#EC4899", productName: "안정적 공공 물류센터 리츠 주식", detail: "안정적 택배와 유통이 끊임없이 발생하는 국가 인증 대형 유통단지 지분에 아주 적은 비율로 참여합니다." }
                ],
                expertAdvice: "<strong>ISTJ 1,000만 원 운용 과외:</strong><br>당신은 자산이 감소할 때의 불안감을 철저하게 회피하는 모범적인 관리자입니다. 그래서 <b>1,000만 원 중 무려 700만 원(예금 300만 원 + 적금 400만 원)을 은행 저축</b>에 전격적으로 꽁꽁 묶어두는 수비를 설계했습니다. 투자 영역인 주식(100만 원)과 채권(150만 원)은 변동성이 가장 통제된 안정적인 국채와 지수 위주입니다. 교과서에 나오는 '유동성'과 '안전성'을 완벽히 이룩한 수비 축적 모델입니다."
            },
            "ISFJ": {
                title: "다정한 일상 방어막 ‘든든 수호자’",
                desc: "차분하고 다정하며, 매달 또박또박 눈앞에 들어오는 정기 이자와 월세의 따뜻한 보너스를 좋아합니다.",
                traits: ["#정기적_배당수익", "#내집마련_청약", "#안전주의자", "#계획형_저축"],
                riskLabel: "안정형 (낮은 리스크)",
                portfolio: [
                    { name: "예금", value: 25, color: "#10B981", productName: "우량 은행 수시입출금 통장", detail: "비상 용돈 및 소소한 선물용 일시 지출을 바로 감당할 수 있도록 마련해 두는 유동성 예치금입니다." },
                    { name: "적금", value: 40, color: "#3B82F6", productName: "청년 주택청약 종합저축 + 매월 정기적금", detail: "정부 지원 혜택을 챙기고 이자 우대와 미래 내집 주거 자격을 선점하는 똑부러지는 목돈 자산입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "글로벌 공공기관 우량 환경 채권 ETF", detail: "기후 기금 마련 등을 위해 공익적으로 발행된 국가 신용의 채권으로 안정성을 보장받습니다." },
                    { name: "주식", value: 10, color: "#F59E0B", productName: "안정 배당 우량주 패키지 (고배당)", detail: "매 분기 주주들에게 정기적 정성 담긴 보너스 배당 용돈을 뿌려주는 최고 신뢰의 국내외 대기업 주식입니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "수도권 도심 상업지구 인프라 리츠", detail: "랜드마크 오피스 빌딩에서 얻는 월세 분배 수입을 정기 이자처럼 꼬박꼬박 가져오는 소형 부동산 권리입니다." }
                ],
                expertAdvice: "<strong>ISFJ 1,000만 원 운용 과외:</strong><br>성실한 저축의 대명사인 당신을 위해, 1,000만 원 자산의 65%인 <b>650만 원을 예적금(예금 250만 원 + 적금 400만 원)</b>에 칼같이 배치하여 안전 기둥을 구축했습니다. 투자 영역인 주식(100만 원)과 부동산(100만 원)은 매 분기 '정기 보너스(배당금)'가 정기 입금되는 가치주 위주로 설계하여, 통장 명세서의 숫자가 따스하게 늘어나는 즐거움을 안전하게 선물해 줍니다."
            },
            "INFJ": {
                title: "세상을 바꾸는 미래의 ‘착한 수호인’",
                desc: "돈을 단순히 소유하는 기쁨보다, 세상을 치유하고 쾌적하게 하는 친환경적 이념에 표를 던집니다.",
                traits: ["#지구수호_착한돈", "#신념의_동반자", "#조용한_거장", "#ESG_투자"],
                riskLabel: "안정 추구형 (낮은 위험)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "착한 공익 은행 우량 예금", detail: "은행 이율을 그대로 지키면서, 동시에 사회 소외계층 무상 대출을 지원하는 공익 전용 예금입니다." },
                    { name: "적금", value: 35, color: "#3B82F6", productName: "환경 보존 매칭 펀딩 정기적금", detail: "매월 적금을 모으면 가입액 일부를 기부해 숲을 조성해 주는 지구사랑 정기 적금 상품입니다." },
                    { name: "채권", value: 20, color: "#EF4444", productName: "글로벌 상생 그린 채권 (Green Bond)", detail: "탄소 중립 및 청정에너지 발전 설비 건설에 안전하게 쓰여서 이자와 이념을 다 잡는 채권입니다." },
                    { name: "주식", value: 15, color: "#F59E0B", productName: "글로벌 ESG 리딩 우량 테크 기업주", detail: "친환경 신소재 개발, 공정 노동 환경을 모범적으로 지키는 최고의 착한 하이테크 기업 지분을 응원합니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "제로에너지 스마트 주택 보급 리츠", detail: "냉난방 에너지를 태양광으로 자급자족하는 복지 스마트 주택 단지를 건설하는 리츠 지분입니다." }
                ],
                expertAdvice: "<strong>INFJ 1,000만 원 운용 과외:</strong><br>당신은 물질적인 가치 위에 공익적 정체성이 서있을 때 가장 마음 편한 투자가 가능합니다. 1,000만 원 자산 중 무려 <b>450만 원(채권 200만 원 + 주식 150만 원 + 부동산 100만 원)을 ESG 상생형 공공 자산</b>에 전격적으로 뿌려 두었습니다. 돈을 잃으면 정서적으로 타격을 많이 받는 성격이므로, 든든한 예적금 안전장치 550만 원(예금 200만 원 + 적금 350만 원)은 절대로 깨지 않도록 마음의 자물쇠를 꼭 채워 놓으세요."
            },
            "INTJ": {
                title: "치밀한 마스터마인드 ‘꼬마 버핏’",
                desc: "남들의 수다나 뇌피셜 소문은 배제하고, 독보적인 계량 데이터와 미래 성장 추세만 조준해 전략적 타격을 수행합니다.",
                traits: ["#뇌피셜_거부", "#글로벌_독점기업", "#위기는_매수찬스", "#체계적_데이터"],
                riskLabel: "성장 지향형 (보통 위험)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "수시 즉각 입출금 통장 (파킹형)", detail: "평소 고금리를 따먹다가, 시장이 갑자기 공포로 고꾸라졌을 때 헐값에 주식을 줍기 위한 사냥용 비축 현금입니다." },
                    { name: "적금", value: 20, color: "#3B82F6", productName: "목표 만기 자동이체 정기적금", detail: "자산운용 계획의 기본 규칙을 준수하기 위해 칼날같이 납입하여 확실히 모아두는 200만 원 저축입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "미국 장기 국채 ETF (헤지 자산)", detail: "전 지구 주가가 흔들릴 때 홀로 달러 가치가 상승해 자산 포트폴리오의 밸런스를 철저히 잡아주는 장치입니다." },
                    { name: "주식", value: 35, color: "#F59E0B", productName: "글로벌 인공지능(AI) 지배 대장주", detail: "경쟁자가 결코 넘볼 수 없는 철옹성 기술 생태계를 구축해 전 세계 지식 산업을 독점 지배하는 기업에 묻어둡니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "글로벌 하이테크 데이터센터 리츠", detail: "전 지구적 디지털 클라우드 데이터 트래픽이 모이는 튼튼한 인공지능 서버 전용 빌딩 부동산입니다." }
                ],
                expertAdvice: "<strong>INTJ 1,000만 원 운용 과외:</strong><br>당신은 투자 판단 시 감정적 소모가 극도로 적고 시장 폭락장 속에서도 침착하게 대응하는 퀀트형 인재입니다. 1,000만 원 중 무려 <b>350만 원을 미래의 AI 지배자(주식)</b>에 분산하여 과감한 지분을 가져가고, 부동산 자산도 100만 원 상당의 최신 '데이터센터'로 설계했습니다. 200만 원의 파킹예금은 무의미한 지출을 위한 돈이 아니라, '시장의 대폭락 시기'에 저가 매수를 감행할 무서운 전략적 대기 총알입니다."
            },
            "ISTP": {
                title: "팩트 기계적 ‘트렌드 냉철가’",
                desc: "감정이 섞이지 않는 논리적인 판단과 참신한 과학적 검증을 즐기는 완벽한 기계적 기술 투자가입니다.",
                traits: ["#기계적_자산배분", "#실용적_테크니션", "#차트의_진실", "#침착한_마인드"],
                riskLabel: "중립형 (보통 위험)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "수수료 전면 제로 하루 파킹 예금", detail: "단돈 하루를 넣어두어도 정직하게 일 단위 이자가 정산되어 들어오는 합리적 유동성 자산입니다." },
                    { name: "적금", value: 25, color: "#3B82F6", productName: "이율 연동 자유 적립식 정기적금", detail: "용돈이 들어오는 간격을 분석하여 유연하게 최적의 적금 불입 이율을 뽑아내는 전략 저축입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "정밀 이격 보정 대기업 회사채 ETF", detail: "대기업 우량 채권들을 모아두어 시장 변동에 정교한 수학 수식처럼 가격 흐름을 연동하는 자산입니다." },
                    { name: "주식", value: 30, color: "#F59E0B", productName: "글로벌 핵심 시스템 반도체 공정주", detail: "인류 제조업 최고의 도구인 나노 반도체 핵심 생산라인과 위탁 가공 글로벌 지배 기업을 조준합니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "무인 자동 스마트 물류 단지 리츠", detail: "택배와 물류가 컨베이어 벨트와 무인 AI 로봇에 의해 자동으로 관리 분배되는 첨단 물류창고 빌딩 지분입니다." }
                ],
                expertAdvice: "<strong>ISTP 1,000만 원 운용 과외:</strong><br>당신은 복잡한 시장 예측 대신 논리적인 '자산 시스템 설계'를 편안해합니다. 1,000만 원을 예금 200만 원, 적금 250만 원, 채권 150만 원, 주식 300만 원, 부동산 100만 원의 황금 비율로 오차 없이 나누었습니다. 감정이 투자를 침범해 망치는 시나리오를 막기 위해, 매년 비율이 깨졌을 때 자동으로 비율을 다시 복원하는 '자산 리밸런싱 기법'을 손수 익히시길 적극 권해드립니다."
            },
            "ISFP": {
                title: "예술적 직관의 ‘안식형 디자이너’",
                desc: "시끄러운 차트 싸움을 싫어하며, 평화로운 내 일상을 방패처럼 사수하면서 좋아하는 유행 가치에 소소히 동참합니다.",
                traits: ["#힐링소비_일치", "#싸움은_싫어", "#내최애브랜드_수집", "#평화형_주주"],
                riskLabel: "안정 추구형 (낮은 위험)",
                portfolio: [
                    { name: "예금", value: 25, color: "#10B981", productName: "공공 안전 최고 우체국 예금", detail: "가장 마음 편하게 일상의 비상금을 보관할 수 있으며 변동 리스크가 전혀 없는 안심 금고입니다." },
                    { name: "적금", value: 35, color: "#3B82F6", productName: "우량 시중은행 자동 이체 정기적금", detail: "용돈 날마다 수동 이체 스트레스 없이 기계적으로 알아서 자금을 모아 큰 목돈으로 돌려주는 적금입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "글로벌 상위 자산배분 안정형 본드 펀드", detail: "지루한 분석 대신 펀드매니저들이 가장 튼튼하고 평화로운 국채들로만 모아서 굴려주는 상품입니다." },
                    { name: "주식", value: 15, color: "#F59E0B", productName: "내가 아끼는 글로벌 명품 소비재 브랜드주", detail: "내가 주말에 사 신고 가보며 가슴이 설렜던 전 세계가 극찬하는 최고의 유행 신발, 미디어 제작사 주식입니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "유명 쇼핑 문화 아울렛 복합 리츠", detail: "대중들이 가장 붐비는 힙한 도심 복합 상업 단지의 부동산 월세를 나도 나누어 받을 수 있는 리츠입니다." }
                ],
                expertAdvice: "<strong>ISFP 1,000만 원 운용 과외:</strong><br>당신에게 금융이란 마음의 상처를 입어가면서까지 해야 하는 전투가 아닙니다. 그래서 1,000만 원 중 무려 <b>600만 원을 예적금(예금 250만 원 + 적금 350만 원)</b>에 배치하여 평화 존을 확보했습니다. 나머지 투자 400만 원(주식 150만 원 + 부동산 100만 원 + 채권 150만 원) 영역도 어려운 계산기 분석 대신 '내가 실생활에서 예쁘고 긍정적으로 경험한 우수 명품 브랜드'로 세팅하여 정서적 동반 투자 모델을 이뤄냈습니다."
            },
            "INFP": {
                title: "자유로운 가치의 ‘어린 숲속 주주’",
                desc: "탐욕과 질투로 점철된 전쟁터 같은 자본 논리 대신, 인류의 건강한 행복과 아름다운 스토리에 가치를 던지는 낭만적 주주입니다.",
                traits: ["#친환경에너지", "#마음이_가는곳에_돈", "#장기_혁신형", "#몽상가의_지갑"],
                riskLabel: "보통 성향 (중립 위험)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "상생 협력 우수 공공 파킹예금", detail: "자산 가치를 조용하게 보관하며, 급작스럽게 상상이 번질 때 유동적으로 쓸 수 있게 거치해 둔 현금입니다." },
                    { name: "적금", value: 30, color: "#3B82F6", productName: "친환경 온실가스 감축 우대 우정 적금", detail: "착한 탄소중립 실천 서약서에 동참하면 금융 우대 이율을 함께 타내는 착한 적금통장입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "국제연합 아동 복지 보조 친환경 채권", detail: "전 지구 오지마을에 깨끗한 친환경 에너지를 전파하기 위해 발행된 평화적 목적의 안전한 국제 채권입니다." },
                    { name: "주식", value: 25, color: "#F59E0B", productName: "차세대 생명 의학 글로벌 연구소 주식", detail: "소외받는 희귀 바이러스나 희귀 질병을 치료하기 위해 분투하는 전 지구적 다국적 헬스케어 테크주입니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "에코 제로에너지 미래 주거 단지 리츠", detail: "콘크리트 회색 아파트가 아닌 미래 청정 흙과 태양열 패널이 설치된 자연친화 빌딩 건설 주식에 동참합니다." }
                ],
                expertAdvice: "<strong>INFP 1,000만 원 운용 과외:</strong><br>당신은 투자할 때 '스토리와 사랑'이라는 영감이 닿아있어야 마음의 불씨가 당겨지는 아름다운 영혼을 지녔습니다. 그래서 당신의 1,000만 원 설계안은 <b>글로벌 헬스케어(250만 원)와 친환경 스마트 빌딩(100만 원), 공익 채권(150만 원)</b>에 걸쳐 50%나 할당했습니다. 멘탈이 섬세해 돈이 깨지면 큰 충격을 받으므로, 예적금 평화구역 500만 원(예금 200만 원 + 적금 300만 원)의 수비라인은 절대로 깨지지 않도록 비상용으로 봉인해 두세요."
            },
            "INTP": {
                title: "끝없는 지적 탐구의 ‘알고리즘 퀀트’",
                desc: "논리적 인과관계, 물리학, 컴퓨터 나노 구조 등 고도의 수학 설계가 녹아든 가치 인프라에 지적 희열을 느끼는 뇌섹 투자가입니다.",
                traits: ["#기초과학_우선", "#알고리즘_매매", "#숫자_지배자", "#논리적인_투자"],
                riskLabel: "성장 지향형 (보통 위험)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "계단형 금리 회전 단기 예치금", detail: "시장 관측 주기 주말에 맞추어 가장 완벽한 연간 가치를 회전시킬 수 있도록 전략 설계된 예금 자산입니다." },
                    { name: "적금", value: 20, color: "#3B82F6", productName: "수학적 규칙 불입 자동적금", detail: "스스로 정의한 주니어 자산 증식 공식에 입각하여 칼날같이 적립해 나가는 계획 저축입니다." },
                    { name: "채권", value: 20, color: "#EF4444", productName: "글로벌 매크로 물가 변동 연동 채권 ETF", detail: "환율과 물가 지수의 연동 변수 공식을 대입하여 리스크를 기계적으로 차단해 주는 국채 자산입니다." },
                    { name: "주식", value: 30, color: "#F59E0B", productName: "글로벌 1위 미세 공정 반도체 파운드리주", detail: "나노 크기의 빛 반사 기술로 차세대 인공지능 그래픽 연산 카드를 정밀 제조해 내는 1등 기업입니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "5G 무선 중계소 탑 랜드마크 리츠", detail: "전 세계 디지털 데이터 흐름의 안테나 역할을 해주는 하이테크 하드웨어 통신 부동산 지분입니다." }
                ],
                expertAdvice: "<strong>INTP 1,000만 원 운용 과외:</strong><br>당신은 감정이나 허황된 유행보단 정밀한 과학적 가치를 수식으로 풀어냈을 때 비로소 투자에 발을 들이는 논리주의자입니다. 1,000만 원 자산 중 <b>300만 원을 초미세 반도체 기업(주식)</b>에 이성적으로 투입하였고, 200만 원의 미국 국채를 대입해 포트폴리오를 완벽하게 보강했습니다. 충동적 투기로 슬퍼지지 않게, 예적금 완충 장치 400만 원(예금 200만 원 + 적금 200만 원)을 정량 할당해 철저히 방패를 세웠습니다."
            },
            "ESTP": {
                title: "파도를 지배하는 ‘스피드 승부사’",
                desc: "급등락하는 변동성의 파도를 찬스로 여기며 대담하고 영리한 액션을 보여주는 고수익 고위험 파이터입니다.",
                traits: ["#모멘텀_투자", "#두려움은_사치", "#하이리스크_하이리턴", "#기회포착_달인"],
                riskLabel: "공격형 (높은 위험 수준)",
                portfolio: [
                    { name: "예금", value: 15, color: "#10B981", productName: "단기 수시입출금 통장 (총알 대기)", detail: "기회가 보이는 고속 성장 주식이 떴을 때 망설임 없이 기동성 있는 매수로 진입할 준비를 하는 파킹 예금입니다." },
                    { name: "적금", value: 20, color: "#3B82F6", productName: "강제 잠금 정기 적금 (생명줄 묶음)", detail: "당신의 과감함이 한순간 폭망의 시나리오를 맞아 1,000만 원을 날렸을 때 최후의 용돈을 보장하는 안심 자물쇠입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "준우량 하이일드 고금리 대기업 회사채", detail: "안정적인 국가 채권보다 두 배가량 화끈한 이율을 약속해 주는 흥미진진한 모험형 회사 보증서입니다." },
                    { name: "주식", value: 40, color: "#F59E0B", productName: "글로벌 최고 거래량 신성장 전기자율주행주", detail: "현재 시장 거래 대금 압도적 1위이자 매 순간 역동적으로 요동치는 기술 기업의 핵심 지분 400만 원어치입니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "글로벌 메가시티 카지노 리조트 특수 리츠", detail: "전 지구 복합 테마파크와 최고급 엔터 호텔들의 임대 수익을 거둬들이는 짜릿한 테마 부동산입니다." }
                ],
                expertAdvice: "<strong>ESTP 1,000만 원 운용 과외:</strong><br>당신은 투자 시 스릴과 수익을 무섭게 낚아채지만, <b>'한순간에 시드가 전액 소멸되어 버리는 극단적 파멸'</b>을 경계해야 합니다. 이를 위해 1,000만 원 중 <b>400만 원을 최고 인기 급등주(주식)</b>에 분배해 에너지를 보존했습니다. 다만 명심해 주세요. 200만 원의 강제 잠금 적금과 150만 원의 파킹용 대기 예금이 뒤받쳐주지 않으면, 시장 급변 시 바로 구걸 통장으로 전락합니다. 이 안전지대 35%는 당신의 우주복이자 마지막 안전벨트입니다."
            },
            "ESFP": {
                title: "트렌드 최전선의 ‘컬처 인사이더’",
                desc: "지금 유행하는 의류, 명품 패션, K-POP, 소셜 미디어 플랫폼 등 대중이 붐비는 힙한 길목에 영리하게 동반 탑승하는 문화스타입니다.",
                traits: ["#트렌드세터", "#힙한브랜드만_조준", "#스타기업_응원", "#소비자적_통찰"],
                riskLabel: "성장 지향형 (보통 위험)",
                portfolio: [
                    { name: "예금", value: 15, color: "#10B981", productName: "우량 시중은행 수시 입출금 예금", detail: "가장 힙한 제품의 급작스러운 신상품 런칭이 떴을 때 지체 없이 지출할 수 있는 유동 현금 자산입니다." },
                    { name: "적금", value: 25, color: "#3B82F6", productName: "충동구매 방어 목적 강제 자동적금", detail: "눈만 뜨면 멋진 옷과 물건들을 사고 싶어 하는 욕망의 지출을 차단하는 자금 강제 묶기 통장입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "글로벌 하이 럭셔리 패션 명품 회사채", detail: "절대 쉽게 망하지 않는 프랑스, 이탈리아 최고급 하이엔드 가방 제조사가 보증하는 이자 채권입니다." },
                    { name: "주식", value: 35, color: "#F59E0B", productName: "전 지구 1등 엔터테인먼트 스타 기획사주", detail: "세계 최고 인기의 케이팝 스타들과 콘텐츠 제작사 등 내가 매일 유행처럼 소비하는 문화를 만드는 주식입니다." },
                    { name: "부동산", value: 10, color: "#EC4899", productName: "글로벌 대표 프리미엄 복합 쇼핑타운 리츠", detail: "매 주말 수많은 트렌드 인사이더들이 몰려 쇼핑하고 소비하는 최고 요지의 도심 빌딩 부동산 지분입니다." }
                ],
                expertAdvice: "<strong>ESFP 1,000만 원 운용 과외:</strong><br>당신은 유행의 냄새를 맡고 소비의 흐름을 짚는 천성적인 강점이 있습니다. 이 장점을 고스란히 살려 1,000만 원 중 <b>350만 원을 메가 트렌드 K-컬처 엔터주(주식)</b>에 묵직하게 넣었고 100만 원은 명문 오피스 빌딩(부동산)에 분산했습니다. 다만 평소 지출 유혹이 매우 강한 스타일이므로, 250만 원의 강제 적금과 150만 원의 예금을 철저히 자동 이체 걸어두어야 비로소 '통장 잔고가 마르지 않는 멋쟁이 자산가'로 우뚝 섭니다."
            },
            "ENFP": {
                title: "호기심 가득한 ‘아이디어 모험가’",
                desc: "새롭고 번뜩이는 모험 정신으로 미래의 미개척 신영역에 기꺼이 상상력을 불어넣는 긍정의 투자가입니다.",
                traits: ["#메타버스_우주선", "#끝없는_아이디어", "#충동구매_차단필요", "#긍정의_에너지"],
                riskLabel: "중립형 (보통 위험)",
                portfolio: [
                    { name: "예금", value: 15, color: "#10B981", productName: "충동 제어용 단기 파킹 통장", detail: "새로운 가상자산이나 신흥 펀딩 유행이 떴을 때 바로 쓸 수 있는 여유 유동성 총알 예금입니다." },
                    { name: "적금", value: 25, color: "#3B82F6", productName: "카더라 유혹 퇴치 정기 예적금", detail: "주변 친구들의 '이거 곧 대박난대!' 하는 귀 얇은 소문에 한순간 돈을 날리지 못하게 묶어둔 든든한 금고입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "미국 장기 국가 보장 국채 ETF", detail: "변동성이 심하고 즉흥적인 당신의 자산이 요동칠 때 우량한 이율로 뒤를 든든하게 받쳐주는 채권입니다." },
                    { name: "주식", value: 30, color: "#F59E0B", productName: "차세대 공중 차량 및 미래형 가상현실 플랫폼", detail: "하늘을 나는 택시, 디지털 공간 내에 독창적인 자아를 만들어 내는 차세대 3D 소프트웨어 주식입니다." },
                    { name: "부동산", value: 15, color: "#EC4899", productName: "글로벌 상징적 아트 갤러리 빌딩 리츠", detail: "뉴욕이나 파리 중심가에서 화려한 현대 미술 전시회가 펼쳐지는 도심형 복합 문화 리츠 부동산입니다." }
                ],
                expertAdvice: "<strong>ENFP 1,000만 원 운용 과외:</strong><br>당신은 상상력과 긍정이 넘치지만 그만큼 <b>'남의 카더라 유행이나 소문에 전 지구에서 귀가 가장 얇은 성격'</b>이기도 합니다. 이에 흔들려 전 재산을 날리는 시나리오를 막기 위해, 예적금 비율 400만 원(예금 150만 원 + 적금 250만 원)을 강력하게 잠가 두어야 합니다. 주식 300만 원 영역은 당신의 영감 가치를 지지하는 우량 하이테크 미래주이며, 150만 원의 문화 리츠 부동산으로 완벽한 분산 가치를 융합시켰습니다."
            },
            "ENTP": {
                title: "패러다임 브레이커 ‘천재 개척가’",
                desc: "남들이 말도 안 된다고 무시하는 기막힌 발명 기술, 차세대 인프라 등 미개척 전방 도전자들에게 온몸으로 응원을 던집니다.",
                traits: ["#지적모험_풀충전", "#기존질서_해체", "#미개척_영역수색", "#도전적인_지갑"],
                riskLabel: "공격형 (높은 위험 수준)",
                portfolio: [
                    { name: "예금", value: 15, color: "#10B981", productName: "즉각 매수 투입 파킹 통장 (유동성 최상)", detail: "번뜩이는 주가 분석 타점이 보이거나 하락 시 즉시 주식을 낚아챌 수 있도록 세워둔 수시 입출금 예금입니다." },
                    { name: "적금", value: 20, color: "#3B82F6", productName: "장기 자산 기반 마련용 고이율 적금", detail: "기존의 지루한 이율 수준을 극복하기 위해 가장 우대이율 혜택이 탄탄한 곳으로 선별해 강제하는 저축입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "글로벌 테크 기업 자금 조달 특수 채권", detail: "지루한 국채 대신 하이테크 메이커들이 발행하는 금리가 좀 더 가치 있는 채권 펀드를 가입합니다." },
                    { name: "주식", value: 35, color: "#F59E0B", productName: "저궤도 인공 우주 위성 통신 대장주", detail: "전 지구 상공에 위성 통신망을 뿌려 데이터 독과점을 완성해 나가는 미래 외연 우주 확장 선도 기업입니다." },
                    { name: "부동산", value: 15, color: "#EC4899", productName: "무인 자동 스마트 물류 시스템 거점 리츠", detail: "인공지능 로봇과 자율주행 택배차량이 상호작용하는 대형 첨단 유통 허브 기지 부동산입니다." }
                ],
                expertAdvice: "<strong>ENTP 1,000만 원 운용 과외:</strong><br>당신은 똑같이 반복되는 시중은행 예금 적금을 보면 몸이 근질거리는 본능적 개혁가입니다. 그래서 세상을 바꿀 <b>우주위성 테크 대장주(주식 350만 원)와 첨단 무인 로봇 물류 빌딩(부동산 150만 원)</b>에 과감히 비중을 조준했습니다. 단, 본인의 기묘한 지식만 믿고 매크로 경제 리스크를 얕보다 무너지기 쉬우므로, 350만 원의 예적금 완충 장치(예금 150만 원 + 적금 200만 원)는 절대 건드리지 않고 만기일까지 묻어두어야 생존합니다."
            },
            "ESTJ": {
                title: "체계적인 지배인 ‘완벽 지갑 관리인’",
                desc: "철저한 예산표 정량 분할, 고정된 기일의 만기 회수, 투명한 보고 규칙을 최고의 신용으로 모시는 자산 관리의 정석입니다.",
                traits: ["#철저한_예산관리", "#통장쪼개기_대장", "#질서와_효율", "#계획형_대장주"],
                riskLabel: "중립형 (합리적 보수성)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "주간 지출 예산 수립용 우량 예금", detail: "매월 지출 계획에 따른 고정 예산을 1원의 차이도 없이 정확히 인출해 사용하는 유동성 예치금입니다." },
                    { name: "적금", value: 30, color: "#3B82F6", productName: "정량 복리 우대 금리 만기 보장 적금", detail: "계획표 마이 플래너에 따라 매 정기일 칼날같이 납입하여 만기에 이자를 정확하게 타내는 강제 저축입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "정부 신용 보증 무위험 공공 공채", detail: "원금 손실 확률이 절대적으로 제로(0)에 완벽 수렴하여 튼튼한 이율 흐름을 공급해 주는 국공채 펀드입니다." },
                    { name: "주식", value: 20, color: "#F59E0B", productName: "글로벌 상위 10대 우량주 종합 지수 ETF", detail: "거래 규율이 선명하게 공개되어 있고 재무 수치가 검증된 전 세계 최고 우량 지수 펀드에 분산 투자합니다." },
                    { name: "부동산", value: 15, color: "#EC4899", productName: "대한민국 최고 중심상업지구 코어 오피스 리츠", detail: "매달 확실한 정기 주주 실적 보고서를 고지하며 월세를 똑바르게 수급해 주는 오피스 빌딩 부동산 지분입니다." }
                ],
                expertAdvice: "<strong>ESTJ 1,000만 원 운용 과외:</strong><br>당신은 주니어 금융 클래스 중 가장 교과서적이고 안정적인 자산 분산 통제력을 구현할 수 있습니다. 1,000만 원 예산을 <b>예금 200만 원, 적금 300만 원, 채권 150만 원, 주식 200만 원, 부동산 150만 원</b>의 완벽한 5대 자산 포토형으로 분할했습니다. 계획적인 성격답게 이 밸런스를 평온히 사수해 가면서, 주식(200만 원)과 채권(150만 원)의 교과서 속 수익성 원리가 실제로 복리 성장하는 마법을 정량 수치로 직접 차트에 기록하며 공부하기 좋은 모델입니다."
            },
            "ESFJ": {
                title: "협동과 행복의 ‘다정다감 이웃 기부자’",
                desc: "나의 자산을 철저히 보호하는 동시에 사회의 평온한 상생, 영세민 일자리 창출에 표를 더하는 착한 주주입니다.",
                traits: ["#상생금융_실천", "#주택청약_선점", "#따뜻한_이웃사랑", "#안정형_선구자"],
                riskLabel: "안정 추구형 (낮은 위험)",
                portfolio: [
                    { name: "예금", value: 20, color: "#10B981", productName: "청년 청약 우대 수시 예금 통장", detail: "비상 상황 대처를 든든하게 하면서, 미래 내 집 마련 비전의 씨앗 주택 청약 혜택을 선점하는 자산입니다." },
                    { name: "적금", value: 35, color: "#3B82F6", productName: "상생 협력 기금 마련 매칭 적금", detail: "내가 저축하면 영세 전통시장 활성화 기금으로 매칭 후원되어 이웃 사랑을 실천하는 정기 적금입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "지하철 및 신축 공공 정수 인프라 국공채", detail: "모든 시민들의 쾌적한 출퇴근과 맑은 물 공급을 위해 발행된 확실히 보장되는 안전한 국가 채권입니다." },
                    { name: "주식", value: 15, color: "#F59E0B", productName: "일자리 우수 대기업 및 동반성장 우량주", detail: "협력 소상공인과의 동반성장 평판이 가장 훌륭하여 국민들에게 고신뢰를 얻는 대표 국민 대장주 지분입니다." },
                    { name: "부동산", value: 15, color: "#EC4899", productName: "서민 안심 복지 주택 보급 공공 인프라 리츠", detail: "소외받는 서민들의 든든한 주거 임대 공간을 건설하여 세상을 따뜻하게 이롭게 만드는 공공 부동산 리츠입니다." }
                ],
                expertAdvice: "<strong>ESFJ 1,000만 원 운용 과외:</strong><br>당신에게 투자란 소외된 자 없이 함께 잘 살아가는 신용 사회를 만드는 악수입니다. 1,000만 원 자금 중 무려 <b>550만 원을 예적금(예금 200만 원 + 적금 350만 원)</b>에 칼같이 잠가두고 150만 원 상당의 국가 보장 채권으로 튼튼한 장갑차 수비를 만들었습니다. 나머지 주식과 부동산 300만 원 영역도 사회와 상생하는 우수 1등 브랜드로 안착시켜, 금리 사기 위험이 일절 없는 가장 정석적이고 다정한 청소년 자산 배분 모델입니다."
            },
            "ENFJ": {
                title: "모두를 이끄는 ‘공익형 따스한 캡틴’",
                desc: "탁월한 리더십과 지혜로 전 세계 교육 에듀테크 플랫폼, 바이오 의료 혁신 인프라를 지탱하는 비전가입니다.",
                traits: ["#교육기술_혁신", "#인류애의_자산배분", "#리더의_용돈철학", "#비전제시가"],
                riskLabel: "보통 성향 (중립 위험)",
                portfolio: [
                    { name: "예금", value: 15, color: "#10B981", productName: "학습 포럼 참가비 전용 유동성 예금", detail: "나의 리더십 개발 및 각종 학습 모임 참가비를 필요 시 언제든 바로 뽑아 쓸 수 있게 거치해 둔 유동 자금입니다." },
                    { name: "적금", value: 30, color: "#3B82F6", productName: "청소년 꿈나무 미래 적립 정기적금", detail: "만기일에 확실한 목돈 자금을 받아 대학 입학 자금 및 멋진 배움 활동에 투입하기 위한 정기 적금입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "아동 구호 복지 조달 국제기구 채권", detail: "세계 영유아 보건 안전과 초등학교 건설을 위해 UNICEF 연계 국제연합이 발행하는 최우량 공익 채권입니다." },
                    { name: "주식", value: 25, color: "#F59E0B", productName: "원격 교육 에듀테크 선도 기업주", detail: "전 지구 오지의 청소년들도 우수한 온라인 교육을 차별 없이 수급받도록 돕는 멋진 글로벌 테크 기업 주식입니다." },
                    { name: "부동산", value: 15, color: "#EC4899", productName: "친환경 신재생 복합 빌딩 단지 리츠", detail: "우리 후손들이 쾌적하게 숨 쉴 수 있도록 태양광 청정 에너지 발전소를 설치하는 복합 스마트 부동산 빌딩입니다." }
                ],
                expertAdvice: "<strong>ENFJ 1,000만 원 운용 과외:</strong><br>당신은 다른 사람의 비전을 도울 때 큰 성취를 체감하는 따스한 캡틴입니다. 1,000만 원의 설계안 중 <b>에듀테크(주식 250만 원)와 친환경 에코 빌딩(부동산 150만 원)</b>에 40%를 과감히 배치하여 멋진 도전을 후원합니다. 주변 사람들의 가여운 부탁이나 사적 소문에 마음이 약해져 돈을 흘리기 쉬우니, 300만 원의 정기 적금 통장은 만기일까지 절대로 깨지 못하도록 기일을 엄수해 관리하시길 조언합니다."
            },
            "ENTJ": {
                title: "시장을 뒤흔들 ‘거물급 주식 CEO’",
                desc: "글로벌 독점 패권을 완벽 장악하여 세상을 송두리째 리드하는 최고의 거함 브랜드들을 강력히 지지하는 야망가입니다.",
                traits: ["#왕좌는_단하나", "#1등기업_몰빵_대신_배분", "#엄청난_지배력", "#주총_목소리"],
                riskLabel: "공격형 (성장 중심형)",
                portfolio: [
                    { name: "예금", value: 15, color: "#10B981", productName: "파킹형 기회 대기 예금 (유동성 중점)", detail: "자본주의 시장에 갑자기 닥치는 글로벌 하락 찬스에서 최고의 주식을 저가에 일격 매수하기 위한 실탄용 현금입니다." },
                    { name: "적금", value: 15, color: "#3B82F6", productName: "경영 시드머니 마련 목적 고금리 적금", detail: "야망의 비즈니스 종잣돈을 만기일에 차곡차곡 받아내기 위해 강제 분배하는 정기 저축 자금입니다." },
                    { name: "채권", value: 15, color: "#EF4444", productName: "기축통화 달러 연동 우량 미국 국고채", detail: "글로벌 하락장 위험에서 포트폴리오의 심리적 붕괴를 강력히 차단해 이겨내게 하는 안전 벨트 자산입니다." },
                    { name: "주식", value: 35, color: "#F59E0B", productName: "글로벌 최고 성능 데이터 지배 1위주", detail: "스마트 기기 운영체제를 완벽히 장악해 인류의 일상을 정량 데이터화해 지배하는 전 지구 1등 플랫폼 회사 주식입니다." },
                    { name: "부동산", value: 20, color: "#EC4899", productName: "뉴욕 맨해튼 비즈니스 핵심 빌딩 리츠", detail: "전 지구 경제 금융 허브인 월스트리트 노른자위에 솟아있는 글로벌 마천루 오피스 건물의 임대 분배인 지분입니다." }
                ],
                expertAdvice: "<strong>ENTJ 1,000만 원 운용 과외:</strong><br>당신은 비즈니스 구조를 조망하고 패권을 탐색하는 천부적인 감각이 흐릅니다. 그래서 1,000만 원 중 <b>350만 원을 우량 독점 플랫폼(주식)</b>에 묵직하게 거치하고, 맨해튼 오피스(부동산 200만 원)에 분배했습니다. 다만 야심 찬 도전은 튼튼한 수비 예적금 300만 원(예금 150만 원 + 적금 150만 원)이 방패가 되어주지 않으면 일시적 등락 시 이겨내지 못하고 한순간 무너질 수 있습니다. 이 안전지대는 당신의 강력한 방어 요새입니다."
            }
        };

        let currentQuestionIndex = 0;
        let userScores = { E: 0, I: 0, S: 0, N: 0, T: 0, F: 0, J: 0, P: 0 };
        let activePortfolioData = null;

        function startTest() {
            document.getElementById('start-page').classList.add('hidden');
            document.getElementById('test-page').classList.remove('hidden');
            currentQuestionIndex = 0;
            userScores = { E: 0, I: 0, S: 0, N: 0, T: 0, F: 0, J: 0, P: 0 };
            showQuestion();
        }

        function showQuestion() {
            const q = questions[currentQuestionIndex];
            
            // Progress Bar Update
            const progressNum = currentQuestionIndex + 1;
            const progressPercent = Math.round((progressNum / questions.length) * 100);
            document.getElementById('progress-text').innerText = `질문 ${progressNum} / ${questions.length}`;
            document.getElementById('progress-percentage').innerText = `${progressPercent}%`;
            document.getElementById('progress-bar').style.width = `${progressPercent}%`;

            // Question Categories
            document.getElementById('question-category').innerText = q.category;
            document.getElementById('question-title').innerText = q.title;

            // Generate Options Dynamically
            const optionsContainer = document.getElementById('options-container');
            optionsContainer.innerHTML = '';

            q.options.forEach((opt, idx) => {
                const btn = document.createElement('button');
                btn.className = "w-full text-left p-4 md:p-5 bg-slate-50 hover:bg-indigo-50 border border-slate-200 hover:border-indigo-300 rounded-2xl font-medium transition-all duration-200 transform active:scale-[0.99] flex items-start gap-3 shadow-sm hover:shadow-indigo-50/50";
                
                // Option Bullet Icon
                const numIcon = document.createElement('span');
                numIcon.className = "w-7 h-7 rounded-full bg-white border border-slate-300 flex items-center justify-center text-xs font-bold shrink-0 mt-0.5 text-slate-500";
                numIcon.innerText = String.fromCharCode(65 + idx); // A, B
                
                const textNode = document.createElement('span');
                textNode.className = "text-sm md:text-base text-slate-700 font-bold leading-relaxed";
                textNode.innerText = opt.text;

                btn.appendChild(numIcon);
                btn.appendChild(textNode);
                
                btn.onclick = () => selectOption(opt.score);
                optionsContainer.appendChild(btn);
            });
        }

        function selectOption(score) {
            // Record Scores
            for (let key in score) {
                userScores[key] += score[key];
            }

            // Next Question
            currentQuestionIndex++;
            if (currentQuestionIndex < questions.length) {
                showQuestion();
            } else {
                showLoading();
            }
        }

        function showLoading() {
            document.getElementById('test-page').classList.add('hidden');
            document.getElementById('loading-page').classList.remove('hidden');

            setTimeout(() => {
                calculateResult();
            }, 1800); // 1.8 seconds processing mimicry
        }

        // Helper to format money (e.g., 5000000 -> 500만 원)
        function formatKoreanMoney(amountInKRW) {
            const tenThousand = 10000;
            const hundredMillion = 100000000;
            
            if (amountInKRW >= hundredMillion) {
                return `${Math.floor(amountInKRW / hundredMillion)}억 ${Math.floor((amountInKRW % hundredMillion) / tenThousand)}만 원`;
            }
            return `${Math.floor(amountInKRW / tenThousand)}만 원`;
        }

        function calculateResult() {
            // Find dominant letter for each dimension
            const mbti = [
                userScores.E >= userScores.I ? 'E' : 'I',
                userScores.S >= userScores.N ? 'S' : 'N',
                userScores.T >= userScores.F ? 'T' : 'F',
                userScores.J >= userScores.P ? 'J' : 'P'
            ].join('');

            const data = mbtiOutcomes[mbti];
            activePortfolioData = data;

            // Render Results page elements
            document.getElementById('result-badge').innerText = mbti;
            document.getElementById('result-title').innerText = data.title;
            document.getElementById('result-desc').innerText = data.desc;

            // Render Traits
            const traitsContainer = document.getElementById('character-traits');
            traitsContainer.innerHTML = '';
            data.traits.forEach(trait => {
                const badge = document.createElement('span');
                badge.className = "bg-slate-50 border border-slate-200 rounded-xl px-3 py-2 text-xs font-bold text-slate-600 flex items-center gap-1.5";
                badge.innerHTML = `<i class="fa-solid fa-check text-indigo-500"></i> ${trait.replace('#', '')}`;
                traitsContainer.appendChild(badge);
            });

            // Set Center Default text of Donut
            const centerLabel = document.getElementById('donut-center-label');
            const centerValue = document.getElementById('donut-center-value');
            centerLabel.innerText = "총 투자자산";
            centerValue.innerText = "1,000만 원";
            centerValue.style.color = "#4F46E5";

            // Risk Assessment badge
            document.getElementById('risk-badge-text').innerText = `성향 위험도: ${data.riskLabel}`;

            // Create SVG Donut Chart dynamically with 5 slices
            let accumulatedPercent = 0;
            data.portfolio.forEach((item, index) => {
                const segment = document.getElementById(`donut-segment-${index + 1}`);
                if (segment) {
                    const realAmount = (item.value / 100) * 10000000;
                    const formattedAmountText = formatKoreanMoney(realAmount);

                    // Stroke-dasharray format: "dash_length gap_length"
                    segment.style.strokeDasharray = `${item.value} 100`;
                    segment.style.strokeDashoffset = `-${accumulatedPercent}`;
                    segment.style.stroke = item.color;
                    segment.setAttribute("stroke-width", "4");

                    // Interactive Event listeners for segments (Now showing real money amounts!)
                    segment.onmouseover = () => {
                        segment.setAttribute("stroke-width", "5.5");
                        centerLabel.innerText = `${item.name} 금액`;
                        centerValue.innerText = formattedAmountText;
                        centerValue.style.color = item.color;
                    };
                    segment.onmouseout = () => {
                        segment.setAttribute("stroke-width", "4");
                        centerLabel.innerText = "총 투자자산";
                        centerValue.innerText = "1,000만 원";
                        centerValue.style.color = "#4F46E5";
                    };

                    accumulatedPercent += item.value;
                }
            });

            // Create Side Color Index Dynamic Legend with Real KRW values (5 items)
            const legendContainer = document.getElementById('donut-color-legend');
            legendContainer.innerHTML = '';
            data.portfolio.forEach((item, index) => {
                const realAmount = (item.value / 100) * 10000000;
                const formattedAmountText = formatKoreanMoney(realAmount);

                const leg = document.createElement('div');
                leg.className = "flex items-center gap-2 p-1.5 rounded-lg hover:bg-slate-100/70 transition-all duration-150 cursor-help";
                leg.innerHTML = `
                    <span class="w-3.5 h-3.5 rounded-md shrink-0" style="background-color: ${item.color}"></span>
                    <div class="text-[11px] leading-tight text-slate-700">
                        <p class="font-extrabold text-slate-900">${item.name}</p>
                        <p class="text-indigo-600 font-extrabold">${formattedAmountText} (${item.value}%)</p>
                    </div>
                `;
                // Linking hover on legend to donut center too!
                leg.onmouseover = () => {
                    centerLabel.innerText = `${item.name} 금액`;
                    centerValue.innerText = formattedAmountText;
                    centerValue.style.color = item.color;
                };
                leg.onmouseout = () => {
                    centerLabel.innerText = "총 투자자산";
                    centerValue.innerText = "1,000만 원";
                    centerValue.style.color = "#4F46E5";
                };
                legendContainer.appendChild(leg);
            });

            // Create Detailed Breakdown list with product recommendations & real money
            const portfolioList = document.getElementById('portfolio-list');
            portfolioList.innerHTML = '';

            data.portfolio.forEach(item => {
                const realAmount = (item.value / 100) * 10000000;
                const formattedAmountText = formatKoreanMoney(realAmount);

                const itemRow = document.createElement('div');
                itemRow.className = "p-4 rounded-2xl bg-slate-50 border border-slate-100 flex flex-col gap-2.5";
                
                itemRow.innerHTML = `
                    <div class="flex items-center justify-between">
                        <div class="flex items-center gap-2">
                            <span class="w-3.5 h-3.5 rounded-full animate-pulse" style="background-color: ${item.color}"></span>
                            <span class="font-black text-sm text-slate-800">${item.name} - <span class="text-slate-400 font-semibold text-xs">${item.productName}</span></span>
                        </div>
                        <span class="text-xs font-black text-indigo-600 bg-indigo-50 border border-indigo-100 px-2.5 py-0.5 rounded-full">${formattedAmountText} (${item.value}%)</span>
                    </div>
                    
                    <!-- Progress Bar representing the portion -->
                    <div class="w-full bg-slate-200/60 rounded-full h-1.5">
                        <div class="h-1.5 rounded-full transition-all duration-1000" style="width: ${item.value}%; background-color: ${item.color}"></div>
                    </div>
                    
                    <p class="text-xs text-slate-500 leading-relaxed">${item.detail}</p>
                `;
                portfolioList.appendChild(itemRow);
            });

            // Load expert advice
            document.getElementById('expert-opinion').innerHTML = data.expertAdvice;

            // Transition page
            document.getElementById('loading-page').classList.add('hidden');
            document.getElementById('result-page').classList.remove('hidden');
        }

        function resetTest() {
            document.getElementById('result-page').classList.add('hidden');
            document.getElementById('test-page').classList.add('hidden');
            document.getElementById('loading-page').classList.add('hidden');
            document.getElementById('start-page').classList.remove('hidden');
            window.scrollTo({ top: 0, behavior: 'smooth' });
        }

        function copyShareLink() {
            // Simulated Clipboard copy with reliable API
            const dummy = document.createElement('input');
            const text = window.location.href;
            document.body.appendChild(dummy);
            dummy.value = text;
            dummy.select();
            document.execCommand('copy');
            document.body.removeChild(dummy);

            const toast = document.getElementById('copy-toast');
            toast.classList.remove('hidden');
            setTimeout(() => {
                toast.classList.add('hidden');
            }, 3000);
        }
    </script>
</body>
</html>
