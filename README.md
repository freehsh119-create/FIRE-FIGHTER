<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="AI 에이전트 시대에 자녀를 어떻게 키워야 할까요? 30문항으로 부모님의 준비도를 평가합니다.">
    <title>AI 에이전트 시대 부모 준비도 평가 - 30문항 자가 진단</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', sans-serif;
            background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
            padding: 20px;
            color: #2c3e50;
            min-height: 100vh;
        }
        
        .container {
            max-width: 900px;
            margin: 0 auto;
            background: white;
            border-radius: 16px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 40px 20px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 32px;
            font-weight: 700;
            margin-bottom: 12px;
        }
        
        .header p {
            font-size: 16px;
            opacity: 0.9;
            margin-bottom: 8px;
        }
        
        .header .subtitle {
            font-size: 14px;
            opacity: 0.8;
        }
        
        .content {
            padding: 40px;
        }
        
        .intro-section {
            margin-bottom: 32px;
            display: none;
        }
        
        .intro-section.show {
            display: block;
        }
        
        .intro-section h2 {
            font-size: 20px;
            margin-bottom: 16px;
            color: #667eea;
        }
        
        .intro-section p {
            line-height: 1.8;
            margin-bottom: 12px;
            color: #555;
            font-size: 15px;
        }
        
        .intro-section ul {
            margin: 16px 0 16px 20px;
            line-height: 2;
            font-size: 15px;
            color: #555;
        }
        
        .start-button {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 14px 40px;
            border: none;
            border-radius: 8px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-top: 24px;
            transition: transform 0.2s;
        }
        
        .start-button:hover {
            transform: translateY(-2px);
        }
        
        .progress-bar {
            width: 100%;
            height: 6px;
            background: #e0e0e0;
            border-radius: 3px;
            margin-bottom: 32px;
            overflow: hidden;
            display: none;
        }
        
        .progress-bar.show {
            display: block;
        }
        
        .progress-fill {
            height: 100%;
            background: linear-gradient(90deg, #667eea, #764ba2);
            width: 0%;
            transition: width 0.3s ease;
        }
        
        .quiz-container {
            display: none;
        }
        
        .quiz-container.show {
            display: block;
        }
        
        .question-card {
            background: #f9f9f9;
            border: 2px solid #e0e0e0;
            border-radius: 12px;
            padding: 24px;
            margin-bottom: 24px;
            display: none;
        }
        
        .question-card.active {
            display: block;
            border-color: #667eea;
        }
        
        .question-number {
            font-size: 12px;
            color: #667eea;
            font-weight: 600;
            margin-bottom: 8px;
            text-transform: uppercase;
        }
        
        .question-text {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 20px;
            line-height: 1.6;
            color: #2c3e50;
        }
        
        .options {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        
        .option {
            display: flex;
            align-items: flex-start;
            gap: 12px;
            padding: 14px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            background: white;
        }
        
        .option:hover {
            background: #f5f5f5;
            border-color: #667eea;
        }
        
        .option input[type="radio"] {
            margin-top: 4px;
            cursor: pointer;
            width: 20px;
            height: 20px;
        }
        
        .option label {
            cursor: pointer;
            flex: 1;
            font-size: 15px;
            line-height: 1.5;
        }
        
        .button-group {
            display: flex;
            gap: 12px;
            justify-content: space-between;
            align-items: center;
            margin-top: 32px;
        }
        
        .nav-buttons {
            display: flex;
            gap: 12px;
        }
        
        button {
            padding: 10px 20px;
            border: 2px solid #e0e0e0;
            background: white;
            color: #2c3e50;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            font-weight: 600;
            transition: all 0.2s;
        }
        
        button:hover:not(:disabled) {
            background: #f5f5f5;
            border-color: #667eea;
        }
        
        button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
        }
        
        .submit-button {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            padding: 12px 28px;
            font-size: 15px;
        }
        
        .submit-button:hover {
            opacity: 0.9;
        }
        
        .progress-info {
            font-size: 14px;
            color: #666;
            font-weight: 500;
        }
        
        .results-container {
            display: none;
        }
        
        .results-container.show {
            display: block;
        }
        
        .score-section {
            text-align: center;
            margin-bottom: 40px;
        }
        
        .score-circle {
            width: 180px;
            height: 180px;
            margin: 0 auto 24px;
            border-radius: 50%;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
            color: white;
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.3);
        }
        
        .score-number {
            font-size: 64px;
            font-weight: 700;
        }
        
        .score-label {
            font-size: 14px;
            opacity: 0.9;
            text-transform: uppercase;
        }
        
        .score-description {
            font-size: 20px;
            font-weight: 600;
            margin: 16px 0;
            color: #2c3e50;
        }
        
        .score-intro {
            font-size: 15px;
            color: #666;
            margin-bottom: 32px;
        }
        
        .feedback-section {
            margin-top: 40px;
            border-top: 2px solid #e0e0e0;
            padding-top: 32px;
        }
        
        .feedback-title {
            font-size: 20px;
            font-weight: 700;
            margin-bottom: 24px;
            color: #2c3e50;
        }
        
        .feedback-category {
            margin-bottom: 24px;
            background: #f9f9f9;
            padding: 20px;
            border-radius: 12px;
            border-left: 4px solid #667eea;
        }
        
        .feedback-category h3 {
            font-size: 16px;
            font-weight: 700;
            margin-bottom: 8px;
            color: #667eea;
        }
        
        .category-score {
            display: inline-block;
            background: #667eea;
            color: white;
            padding: 4px 10px;
            border-radius: 4px;
            font-size: 12px;
            font-weight: 600;
            margin-right: 8px;
            margin-bottom: 8px;
        }
        
        .feedback-text {
            font-size: 14px;
            line-height: 1.7;
            color: #555;
            margin-bottom: 12px;
        }
        
        .suggestions {
            font-size: 13px;
            line-height: 1.8;
            color: #666;
            white-space: pre-wrap;
            background: white;
            padding: 12px;
            border-radius: 6px;
            margin-top: 8px;
        }
        
        .action-buttons {
            margin-top: 32px;
            display: flex;
            gap: 12px;
            justify-content: center;
            flex-wrap: wrap;
        }
        
        .action-button {
            padding: 12px 24px;
            border-radius: 8px;
            border: none;
            font-size: 14px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.2s;
        }
        
        .print-button {
            background: #667eea;
            color: white;
        }
        
        .print-button:hover {
            opacity: 0.9;
        }
        
        .retry-button {
            background: white;
            color: #667eea;
            border: 2px solid #667eea;
        }
        
        .retry-button:hover {
            background: #f5f5f5;
        }
        
        @media print {
            body {
                background: white;
            }
            
            .button-group, .action-buttons {
                display: none;
            }
        }
        
        @media (max-width: 768px) {
            .header h1 {
                font-size: 24px;
            }
            
            .content {
                padding: 20px;
            }
            
            .score-circle {
                width: 140px;
                height: 140px;
            }
            
            .score-number {
                font-size: 48px;
            }
            
            .button-group {
                flex-direction: column;
            }
            
            .nav-buttons {
                width: 100%;
            }
            
            button {
                flex: 1;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>🎯 AI 에이전트 시대 부모 준비도 평가</h1>
            <p>초등학생·중학생 자녀를 둔 부모님을 위한 30문항 자가 진단</p>
            <p class="subtitle">약 10-15분 소요 | 무료 평가</p>
        </div>
        
        <div class="content">
            <!-- 소개 섹션 -->
            <div class="intro-section show" id="introSection">
                <h2>💡 이 평가가 무엇인가요?</h2>
                <p>AI 에이전트 시대가 도래했습니다. ChatGPT, Claude와 같은 지능형 AI가 일상과 직업을 빠르게 변화시키고 있습니다.</p>
                <p><strong>부모님은 자녀를 이 새로운 세상에 제대로 준비시키고 계신가요?</strong></p>
                
                <h2 style="margin-top: 24px;">📊 평가 항목</h2>
                <p>이 평가는 다음의 16가지 영역에서 부모님의 준비도를 진단합니다:</p>
                <ul>
                    <li><strong>AI 리터러시:</strong> AI 기술에 대한 이해와 활용 능력</li>
                    <li><strong>비판적 사고력:</strong> 정보를 판단하고 분석하는 능력</li>
                    <li><strong>창의성 양성:</strong> 새로운 아이디어를 표현하도록 격려</li>
                    <li><strong>디지털 윤리:</strong> 개인정보 보호, 보안, 책임감 있는 행동</li>
                    <li><strong>성장 마인드셋:</strong> 실패를 배움의 기회로 보기</li>
                    <li><strong>감정 지능:</strong> 자신과 타인의 감정 이해</li>
                    <li><strong>자기주도 학습:</strong> 스스로 배우고 성장하기</li>
                    <li><strong>협업 능력:</strong> 함께 일하고 배우기</li>
                    <li><strong>그 외 8가지 중요한 미래 역량</strong></li>
                </ul>
                
                <h2 style="margin-top: 24px;">🎯 평가 후 얻을 수 있는 것</h2>
                <ul>
                    <li>✅ 100점 만점 기준의 부모 준비도 점수</li>
                    <li>✅ 16개 영역별 상세 분석 결과</li>
                    <li>✅ 부족한 영역에 대한 구체적인 개선 방안</li>
                    <li>✅ AI 시대 자녀 교육을 위한 실질적 조언</li>
                </ul>
                
                <button class="start-button" onclick="startQuiz()">평가 시작하기 →</button>
            </div>
            
            <!-- 퀴즈 섹션 -->
            <div class="quiz-container" id="quizContainer">
                <div class="progress-bar" id="progressBar">
                    <div class="progress-fill" id="progress"></div>
                </div>
                
                <div id="questions-wrapper"></div>
                
                <div class="button-group">
                    <div class="nav-buttons">
                        <button id="prevBtn" onclick="previousQuestion()" style="display: none;">← 이전</button>
                        <button id="nextBtn" onclick="nextQuestion()">다음 →</button>
                    </div>
                    <div class="progress-info">
                        <span id="currentQuestion">1</span> / <span id="totalQuestions">30</span>
                    </div>
                </div>
            </div>
            
            <!-- 결과 섹션 -->
            <div class="results-container" id="resultsContainer">
                <div class="score-section">
                    <div class="score-circle">
                        <div class="score-number" id="scoreNumber">0</div>
                        <div class="score-label">점수</div>
                    </div>
                    <div class="score-description" id="scoreDescription"></div>
                    <p class="score-intro">AI 에이전트 시대에 자녀를 준비시키기 위한 영역별 상세 피드백입니다.</p>
                </div>
                
                <div class="feedback-section">
                    <h3 class="feedback-title">📊 영역별 분석</h3>
                    <div id="feedbackContent"></div>
                </div>
                
                <div class="action-buttons">
                    <button class="action-button print-button" onclick="window.print()">📄 인쇄하기</button>
                    <button class="action-button retry-button" onclick="retakeQuiz()">🔄 다시 평가하기</button>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        const questions = [
            {
                q: "자녀가 ChatGPT나 Claude 같은 AI 도구를 사용할 때, 어떤 태도를 보이시나요?",
                category: "AI 리터러시",
                options: [
                    { text: "위험하니까 절대 사용하지 말라고 금지한다", score: 0 },
                    { text: "사용은 하지만 그 한계와 윤리에 대해 별로 이야기하지 않는다", score: 30 },
                    { text: "함께 사용하면서 AI의 장단점을 자주 이야기한다", score: 70 },
                    { text: "자녀가 AI를 비판적으로 활용하도록 격려하고 원리를 설명해준다", score: 100 }
                ]
            },
            {
                q: "자녀가 틀린 문제를 푼 후, 부모의 반응은?",
                category: "성장 마인드셋",
                options: [
                    { text: "점수가 떨어졌다고 혼낸다", score: 0 },
                    { text: "무조건 정답을 알려주려 한다", score: 30 },
                    { text: "어디서 실수했는지 찾아보도록 한다", score: 70 },
                    { text: "실수를 통해 무엇을 배웠는지 깊이 있게 대화한다", score: 100 }
                ]
            },
            {
                q: "자녀가 학교 공부 외에 프로그래밍, 데이터, 창의 프로젝트에 관심을 보일 때?",
                category: "디지털 기술 이해",
                options: [
                    { text: "공부에 방해가 된다며 중단시킨다", score: 0 },
                    { text: "하는 대로 놔둔다", score: 30 },
                    { text: "좋다고 격려하지만 자세히 모른다", score: 70 },
                    { text: "함께 배우고 자녀의 프로젝트를 적극 지원한다", score: 100 }
                ]
            },
            {
                q: "일상에서 데이터와 자동화에 대해 자녀와 대화하나요?",
                category: "AI 리터러시",
                options: [
                    { text: "거의 하지 않는다", score: 0 },
                    { text: "가끔 AI 뉴스를 보여주긴 한다", score: 40 },
                    { text: "유튜브나 기사를 함께 보며 대화한다", score: 70 },
                    { text: "실생활 사례를 찾아 규칙적으로 토론한다", score: 100 }
                ]
            },
            {
                q: "자녀가 온라인에서 개인정보를 보호하는 것의 중요성을 알고 있나요?",
                category: "디지털 윤리",
                options: [
                    { text: "잘 모른다", score: 0 },
                    { text: "막연히 조심하라고는 한다", score: 30 },
                    { text: "구체적으로 설명해준 적이 있다", score: 70 },
                    { text: "정기적으로 개인정보 보호, 사이버 보안에 대해 토론한다", score: 100 }
                ]
            },
            {
                q: "AI 시대에는 어떤 능력이 가장 중요하다고 생각하시나요?",
                category: "미래 역량 인식",
                options: [
                    { text: "좋은 성적과 유명 대학 입학", score: 0 },
                    { text: "컴퓨터 기술이나 프로그래밍 능력", score: 30 },
                    { text: "창의성, 비판적 사고, 협업 능력", score: 80 },
                    { text: "위 세 가지 모두를 균형있게 발달시키는 것", score: 100 }
                ]
            },
            {
                q: "자녀가 새로운 분야에 도전할 때 부모의 반응은?",
                category: "성장 마인드셋",
                options: [
                    { text: "성공이 보장되지 않으면 하지 말라고 한다", score: 0 },
                    { text: "해볼 수 있지만 실패하면 책임은 자신의 것이라고 말한다", score: 40 },
                    { text: "도전을 지지하고 실패를 배움의 기회로 본다", score: 80 },
                    { text: "함께 실패를 분석하고 다음 시도를 계획한다", score: 100 }
                ]
            },
            {
                q: "자녀가 의문을 제기하거나 부모의 생각에 다를 때?",
                category: "비판적 사고력",
                options: [
                    { text: "어른 말을 따르라고 한다", score: 0 },
                    { text: "일단 듣긴 한다", score: 40 },
                    { text: "왜 그렇게 생각하는지 함께 살펴본다", score: 70 },
                    { text: "자녀의 근거와 논리를 존중하며 건설적으로 토론한다", score: 100 }
                ]
            },
            {
                q: "디지털 중독(SNS, 게임 등)에 대해 자녀와 얼마나 자주 대화하나요?",
                category: "디지털 윤리",
                options: [
                    { text: "별로 대화하지 않는다", score: 0 },
                    { text: "시간을 줄이라고만 말한다", score: 30 },
                    { text: "기술의 중독성 원리와 자기조절 방법에 대해 설명한다", score: 70 },
                    { text: "자녀가 의도적으로 건강한 디지털 습관을 만들도록 함께 한다", score: 100 }
                ]
            },
            {
                q: "자녀의 미래 진로에 대해 몇 가지 가능성을 열어두고 있나요?",
                category: "미래 역량 인식",
                options: [
                    { text: "의사, 변호사, 공무원 같은 전통적인 직업만 원한다", score: 0 },
                    { text: "IT 직업도 괜찮다고 생각한다", score: 30 },
                    { text: "다양한 신직업 가능성을 함께 탐색한다", score: 70 },
                    { text: "자녀의 흥미와 사회 변화에 맞춰 함께 커리어를 설계한다", score: 100 }
                ]
            },
            {
                q: "인공지능이 창출하는 새로운 일자리에 대해 알고 계신가요?",
                category: "AI 리터러시",
                options: [
                    { text: "거의 없을 거라 생각한다", score: 0 },
                    { text: "대충 들어본 정도다", score: 40 },
                    { text: "몇 가지 새로운 직업 분야를 알고 있다", score: 70 },
                    { text: "정기적으로 학습하고 자녀에게 소개한다", score: 100 }
                ]
            },
            {
                q: "자녀가 실패했을 때, 자신감을 잃으면 어떻게 하나요?",
                category: "감정 지능",
                options: [
                    { text: "그럴 수도 있다고 위로만 한다", score: 30 },
                    { text: "잘못한 부분을 지적해서 다시 하라고 한다", score: 0 },
                    { text: "감정을 인정하고 함께 대응책을 생각한다", score: 70 },
                    { text: "자녀의 감정을 깊이 있게 경청하고 회복력을 키워준다", score: 100 }
                ]
            },
            {
                q: "자녀와 함께 온라인 보안(암호, 피싱, 사기)에 대해 배운 적 있나요?",
                category: "디지털 윤리",
                options: [
                    { text: "없다", score: 0 },
                    { text: "정도는 알려줬다", score: 40 },
                    { text: "구체적인 사례를 들어 설명해줬다", score: 70 },
                    { text: "정기적으로 함께 보안 습관을 점검하고 업데이트한다", score: 100 }
                ]
            },
            {
                q: "자녀가 혼자 공부하고 배우는 능력을 어느 정도 격려하나요?",
                category: "자기주도 학습",
                options: [
                    { text: "부모가 계획을 세우고 관리해야 한다고 생각한다", score: 0 },
                    { text: "자율성은 중요하지만 방치하는 경향이 있다", score: 40 },
                    { text: "자녀가 주도적으로 계획하도록 점진적으로 격려한다", score: 70 },
                    { text: "자녀의 자기주도 학습을 체계적으로 코칭한다", score: 100 }
                ]
            },
            {
                q: "온라인과 오프라인의 건강한 균형에 대해 함께 대화하나요?",
                category: "디지털 웰빙",
                options: [
                    { text: "온라인을 피하라고만 말한다", score: 0 },
                    { text: "시간을 정해주고 강제한다", score: 30 },
                    { text: "온라인의 장점과 위험을 함께 이야기한다", score: 70 },
                    { text: "자녀 스스로 균형을 유지하는 능력을 기른다", score: 100 }
                ]
            },
            {
                q: "창의적인 아이디어나 새로운 시도에 자녀가 얼마나 자유로운가요?",
                category: "창의성 양성",
                options: [
                    { text: "정해진 길을 따르는 것이 안전하다고 생각한다", score: 0 },
                    { text: "괜찮지만 실용성 있는 것만 지지한다", score: 40 },
                    { text: "창의적인 표현을 격려한다", score: 70 },
                    { text: "자녀의 창의력 개발을 위해 환경을 적극 지원한다", score: 100 }
                ]
            },
            {
                q: "자녀와 다른 문화, 관점에 대해 대화하나요?",
                category: "글로벌 마인드셋",
                options: [
                    { text: "한국 방식이 최고라고 생각한다", score: 0 },
                    { text: "다른 문화도 있다는 정도만 말한다", score: 30 },
                    { text: "다양한 관점과 문화를 소개하고 이해한다", score: 70 },
                    { text: "글로벌 이슈를 함께 분석하고 다양한 해석을 존중한다", score: 100 }
                ]
            },
            {
                q: "자녀가 도움이 필요할 때 먼저 스스로 해결책을 찾도록 유도하나요?",
                category: "자기주도 학습",
                options: [
                    { text: "바로 답을 알려준다", score: 0 },
                    { text: "가끔 스스로 생각해보라고 한다", score: 40 },
                    { text: "자주 질문을 통해 스스로 생각하게 한다", score: 70 },
                    { text: "자녀의 문제해결 능력을 체계적으로 코칭한다", score: 100 }
                ]
            },
            {
                q: "자녀와 인공지능의 윤리적 문제(편향, 투명성, 책임)에 대해 이야기한 적 있나요?",
                category: "AI 윤리 의식",
                options: [
                    { text: "없다", score: 0 },
                    { text: "AI가 때때로 편향될 수 있다는 정도만 알고 있다", score: 40 },
                    { text: "구체적인 사례를 들어 설명해주었다", score: 70 },
                    { text: "정기적으로 AI 윤리에 대해 비판적으로 토론한다", score: 100 }
                ]
            },
            {
                q: "자녀가 정보의 출처를 확인하고 가짜뉴스를 판별하는 능력이 있나요?",
                category: "비판적 사고력",
                options: [
                    { text: "아직 배운 적 없다", score: 0 },
                    { text: "대충 조심하라고만 말했다", score: 30 },
                    { text: "구체적으로 방법을 가르쳤다", score: 70 },
                    { text: "정기적으로 함께 팩트체크를 하고 검증한다", score: 100 }
                ]
            },
            {
                q: "자녀가 팀 프로젝트나 협력할 때 부모의 역할은?",
                category: "협업 능력",
                options: [
                    { text: "개인 성과만 신경 쓴다", score: 0 },
                    { text: "협력하되 주도적으로 하도록 한다", score: 40 },
                    { text: "팀원과의 소통과 협력을 격려한다", score: 70 },
                    { text: "팀 협력의 중요성을 코칭하고 갈등 해결을 지원한다", score: 100 }
                ]
            },
            {
                q: "자녀의 온라인 활동을 어느 정도 모니터링하나요?",
                category: "디지털 윤리",
                options: [
                    { text: "전혀 관심이 없다", score: 0 },
                    { text: "가끔 확인한다", score: 40 },
                    { text: "정기적으로 확인하고 함께 대화한다", score: 70 },
                    { text: "신뢰와 감시 사이의 균형을 유지하며 관계를 맺는다", score: 100 }
                ]
            },
            {
                q: "자녀의 디지털 발자국(온라인 기록)의 중요성을 알고 있나요?",
                category: "디지털 시민의식",
                options: [
                    { text: "몰랐다", score: 0 },
                    { text: "대충 들어본 정도다", score: 30 },
                    { text: "왜 중요한지 이해하고 있다", score: 70 },
                    { text: "함께 책임감 있는 온라인 행동의 중요성을 배우고 있다", score: 100 }
                ]
            },
            {
                q: "자녀가 스트레스를 받을 때 감정 표현과 대처 방법을 배우고 있나요?",
                category: "감정 지능",
                options: [
                    { text: "그냥 넘어가라고 한다", score: 0 },
                    { text: "문제가 생기면 해결 방법을 제시한다", score: 40 },
                    { text: "감정을 표현하고 함께 대처 방법을 찾는다", score: 70 },
                    { text: "감정 지능과 회복력을 키우는 것을 의도적으로 코칭한다", score: 100 }
                ]
            },
            {
                q: "부모 스스로 기술 변화에 대해 배우고 적응하려고 노력하나요?",
                category: "부모의 AI 학습",
                options: [
                    { text: "기술은 자녀에게 맡긴다", score: 0 },
                    { text: "필요할 때만 배운다", score: 30 },
                    { text: "가끔 새로운 기술을 배우려고 한다", score: 70 },
                    { text: "지속적으로 배우고 자녀와 함께 학습한다", score: 100 }
                ]
            },
            {
                q: "인공지능이 없어질 직업과 생길 직업에 대해 자녀와 이야기했나요?",
                category: "미래 역량 인식",
                options: [
                    { text: "아직 아니다", score: 0 },
                    { text: "간단히 언급한 적 있다", score: 40 },
                    { text: "구체적으로 탐색해본 적 있다", score: 70 },
                    { text: "정기적으로 미래 진로 가능성을 함께 탐색한다", score: 100 }
                ]
            },
            {
                q: "자녀가 실수에서 배우는 것의 중요성을 얼마나 강조하나요?",
                category: "성장 마인드셋",
                options: [
                    { text: "실수는 피해야 한다고 강조한다", score: 0 },
                    { text: "실수도 괜찮다고 말하지만 깊이 있게 배우지는 못한다", score: 40 },
                    { text: "실수에서 배운 점을 함께 찾는다", score: 70 },
                    { text: "성장 마인드셋(성장할 수 있다는 믿음)을 의도적으로 전한다", score: 100 }
                ]
            },
            {
                q: "자녀가 새로운 정보를 어디서 얻고 판단하는지 관심이 있나요?",
                category: "미디어 리터러시",
                options: [
                    { text: "관심이 없다", score: 0 },
                    { text: "대충 어떤 앱을 쓰는지는 안다", score: 30 },
                    { text: "정보 출처를 함께 확인한다", score: 70 },
                    { text: "신뢰도 있는 정보 취득 능력을 함께 개발한다", score: 100 }
                ]
            },
            {
                q: "자녀가 타인의 의견을 존중하면서도 자신의 주장을 표현하는 능력이 있나요?",
                category: "협업 능력",
                options: [
                    { text: "자신의 주장만 고집한다", score: 0 },
                    { text: "다른 의견도 있다는 것을 안다", score: 40 },
                    { text: "의견을 존중하면서 자신의 주장을 표현한다", score: 70 },
                    { text: "건설적인 대화와 타협 능력이 뛰어나다", score: 100 }
                ]
            },
            {
                q: "AI, 데이터, 기술에 대한 개인적인 지식 수준은 어떻게 되나요?",
                category: "부모의 AI 학습",
                options: [
                    { text: "거의 모르는 편이다", score: 0 },
                    { text: "기본적인 개념만 안다", score: 40 },
                    { text: "일반적인 수준으로 이해한다", score: 70 },
                    { text: "꾸준히 배우고 최신 발전을 따라간다", score: 100 }
                ]
            },
            {
                q: "자녀가 다양한 관점에서 문제를 해결하도록 격려하나요?",
                category: "비판적 사고력",
                options: [
                    { text: "정답이 하나라고 가르친다", score: 0 },
                    { text: "여러 방법이 있다고는 말한다", score: 40 },
                    { text: "다양한 접근 방식을 탐색하도록 격려한다", score: 70 },
                    { text: "창의적이고 다각도의 문제 해결을 코칭한다", score: 100 }
                ]
            }
        ];
        
        const feedbackData = {
            "AI 리터러시": {
                feedback: "AI의 기초 개념과 활용법에 대한 이해입니다. 자녀가 AI를 도구로 이해하고 비판적으로 활용하는 능력을 키워주세요.",
                suggestions: "• ChatGPT, Claude 등을 함께 사용해보기\n• AI의 정확성과 한계에 대해 함께 탐색하기\n• 주간 뉴스나 AI 기술 트렌드를 함께 읽기\n• AI 관련 유튜브 채널(3Blue1Brown, CGP Grey 등) 함께 보기"
            },
            "디지털 기술 이해": {
                feedback: "코딩, 데이터, 소프트웨어 등 기술에 대한 실무적 이해입니다. 자녀의 기술 활동을 지원하는 것이 중요합니다.",
                suggestions: "• 자녀가 하고 싶은 프로젝트 함께 계획하기\n• Scratch, Python 같은 프로그래밍 기초 배워보기\n• Tech 유튜브나 블로그로 함께 배우기\n• 교육용 AI 도구(Teachable Machine, ML Kit) 체험하기"
            },
            "디지털 윤리": {
                feedback: "개인정보, 보안, 사이버 안전, 온라인 행동 규범에 대한 이해입니다. 자녀의 디지털 시민의식을 키워주세요.",
                suggestions: "• 개인정보 보호의 구체적 사례 함께 학습하기\n• 사이버 보안(암호, 피싱) 워크숍 함께 하기\n• 온라인 괴롭힘, 사생활 침해에 대해 대화하기\n• 신뢰할 수 있는 온라인 친구관계에 대해 논의하기"
            },
            "성장 마인드셋": {
                feedback: "실패를 배움의 기회로 보고 도전을 격려하는 태도입니다. 자녀의 회복력과 끊임없는 학습 능력이 핵심입니다.",
                suggestions: "• 자녀의 실패를 함께 분석하기(\"어디서 배웠나?\")\n• 성공한 사람들의 실패 사례 함께 읽기\n• 어려운 것에 도전할 때 \"아직\"이라는 표현 사용하기\n• 노력의 과정을 칭찬하기 (결과가 아닌)"
            },
            "비판적 사고력": {
                feedback: "증거를 바탕으로 판단하고 다양한 관점을 이해하는 능력입니다. AI 시대에 가장 중요한 능력 중 하나입니다.",
                suggestions: "• 의견이 다를 때 \"왜 그렇게 생각하니?\" 질문하기\n• 가짜뉴스 판별 방법 함께 배우기\n• 사설과 뉴스의 차이 이해하기\n• 여러 출처의 정보를 비교하는 습관 들이기"
            },
            "창의성 양성": {
                feedback: "자유롭게 새로운 아이디어를 표현하고 시도하는 능력입니다. AI가 할 수 없는 인간만의 강점입니다.",
                suggestions: "• 자녀의 아이디어를 먼저 비판하지 않기\n• \"만약 ~라면?\" 같은 가정적 질문하기\n• 창의적인 프로젝트(미술, 음악, 글쓰기) 지원하기\n• 실패해도 괜찮다는 안전한 환경 만들기"
            },
            "감정 지능": {
                feedback: "자신의 감정을 이해하고 표현하며 타인의 감정을 공감하는 능력입니다. 관계형성의 기초이자 AI 시대의 필수 능력입니다.",
                suggestions: "• 자녀의 감정을 먼저 경청하기(\"기분이 어때?\")\n• 감정 표현을 위한 안전한 공간 만들기\n• 자신의 감정 관리 방법을 함께 찾기\n• 타인 배려와 공감 능력 의도적으로 키우기"
            },
            "자기주도 학습": {
                feedback: "스스로 목표를 세우고 계획하며 배우는 능력입니다. AI 시대에 끊임없는 업스킬링을 위해 매우 중요합니다.",
                suggestions: "• 자녀에게 \"너는 뭘 배우고 싶어?\" 물어보기\n• 함께 학습 계획 세우고 진행도 추적하기\n• 온라인 강좌(Khan Academy, Coursera 등) 활용하기\n• 자녀의 주도권을 점진적으로 늘리기(손 놔주기)"
            },
            "협업 능력": {
                feedback: "팀에서 자신의 역할을 하고 타인을 존중하며 함께 목표를 이루는 능력입니다. AI와 인간의 협업이 미래입니다.",
                suggestions: "• 팀 프로젝트의 과정을 함께 들어주기\n• 팀원 간의 갈등 해결 방법을 코칭하기\n• 다양한 관점을 존중하는 토론 문화 만들기\n• 함께 일하는 기술을 의도적으로 가르치기"
            },
            "미래 역량 인식": {
                feedback: "AI 시대에 무엇이 중요한지, 자녀가 어떤 미래를 준비해야 하는지에 대한 부모님의 이해도입니다.",
                suggestions: "• 미래 일자리 변화에 대해 정기적으로 배우기\n• 자녀와 \"10년 뒤 세상\"에 대해 대화하기\n• 새로운 직업 분야를 함께 탐색해보기\n• 자녀의 강점과 관심사로 가능한 미래 경로 그려보기"
            },
            "디지털 웰빙": {
                feedback: "온라인과 오프라인의 건강한 균형을 유지하는 능력입니다. 신체 및 정신 건강의 바탕이 됩니다.",
                suggestions: "• 온라인 시간과 오프라인 활동의 균형 함께 계획하기\n• 스크린 시간이 미치는 영향 함께 논의하기\n• 규칙이 아닌 \"이해와 동의\" 기반의 약속 만들기\n• 부모 스스로 모범을 보이기(스마트폰 사용 줄이기)"
            },
            "글로벌 마인드셋": {
                feedback: "다양한 문화와 관점을 이해하고 존중하는 능력입니다. 국경 없는 AI 시대에 필수적입니다.",
                suggestions: "• 다양한 국가의 뉴스와 문화 함께 접하기\n• 국제 이슈에 대해 다양한 관점으로 토론하기\n• 온라인 펜팔이나 화상 교류 활동해보기\n• 다른 문화를 존중하는 태도를 의도적으로 전하기"
            },
            "AI 윤리 의식": {
                feedback: "AI 기술의 편향, 투명성, 책임에 대한 이해입니다. 기술의 올바른 사용을 위해 중요합니다.",
                suggestions: "• AI의 윤리적 문제(편향, 투명성)에 대해 읽기\n• \"AI는 누가 만들고 누구를 위한가?\" 질문하기\n• 구체적인 AI 윤리 사례(채용 알고리즘, 안면인식 등) 함께 분석하기\n• 책임 있는 AI 사용에 대한 자녀의 의견 듣기"
            },
            "미디어 리터러시": {
                feedback: "정보의 출처를 판단하고 신뢰도를 평가하는 능력입니다. AI 시대의 가짜뉴스 극복의 핵심입니다.",
                suggestions: "• 기사를 읽을 때 출처와 저자 확인하기\n• 가짜뉴스 판별 사이트 함께 보기\n• \"이 정보는 어디서 왔을까?\" 습관 들이기\n• 신뢰할 수 있는 뉴스 매체 함께 찾기"
            },
            "디지털 시민의식": {
                feedback: "온라인에서의 책임감 있는 행동과 장기적 영향을 이해하는 능력입니다.",
                suggestions: "• 온라인 발자국의 영구성 설명하기\n• 과거 게시물의 영향을 함께 생각해보기\n• 디지털 명성(Digital Reputation) 관리 방법 배우기\n• 책임감 있는 온라인 활동을 함께 실천하기"
            },
            "부모의 AI 학습": {
                feedback: "부모님 스스로 기술 변화를 이해하고 배우려는 노력입니다. 자녀의 최고의 멘토가 되기 위해 필수적입니다.",
                suggestions: "• 주간 AI/기술 관련 팟캐스트 듣기\n• \"부모를 위한\" 기술 입문 책이나 강좌 활용하기\n• 자녀와 함께 새로운 기술 배우기\n• 부모 커뮤니티에서 다른 부모들과 경험 나누기"
            }
        };
        
        let currentQuestion = 0;
        let answers = new Array(questions.length).fill(null);
        let quizStarted = false;
        
        function startQuiz() {
            document.getElementById('introSection').classList.remove('show');
            document.getElementById('quizContainer').classList.add('show');
            document.getElementById('progressBar').classList.add('show');
            quizStarted = true;
            initQuiz();
        }
        
        function initQuiz() {
            const wrapper = document.getElementById('questions-wrapper');
            wrapper.innerHTML = '';
            questions.forEach((q, index) => {
                const card = document.createElement('div');
                card.className = 'question-card' + (index === 0 ? ' active' : '');
                card.innerHTML = `
                    <div class="question-number">${q.category} - 문제 ${index + 1}</div>
                    <div class="question-text">${q.q}</div>
                    <div class="options">
                        ${q.options.map((opt, optIndex) => `
                            <label class="option">
                                <input type="radio" name="q${index}" value="${optIndex}" onchange="selectAnswer(${index}, ${optIndex}, ${opt.score})">
                                <label>${opt.text}</label>
                            </label>
                        `).join('')}
                    </div>
                `;
                wrapper.appendChild(card);
            });
            updateNavigation();
        }
        
        function selectAnswer(qIndex, optIndex, score) {
            answers[qIndex] = score;
            updateProgress();
        }
        
        function nextQuestion() {
            if (currentQuestion < questions.length - 1) {
                document.querySelector('.question-card.active').classList.remove('active');
                currentQuestion++;
                document.querySelectorAll('.question-card')[currentQuestion].classList.add('active');
                updateNavigation();
                window.scrollTo(0, 0);
            } else {
                showResults();
            }
        }
        
        function previousQuestion() {
            if (currentQuestion > 0) {
                document.querySelector('.question-card.active').classList.remove('active');
                currentQuestion--;
                document.querySelectorAll('.question-card')[currentQuestion].classList.add('active');
                updateNavigation();
                window.scrollTo(0, 0);
            }
        }
        
        function updateNavigation() {
            document.getElementById('prevBtn').style.display = currentQuestion === 0 ? 'none' : 'block';
            document.getElementById('nextBtn').textContent = currentQuestion === questions.length - 1 ? '채점하기 →' : '다음 →';
            document.getElementById('currentQuestion').textContent = currentQuestion + 1;
        }
        
        function updateProgress() {
            const answered = answers.filter(a => a !== null).length;
            document.getElementById('progress').style.width = (answered / questions.length) * 100 + '%';
        }
        
        function showResults() {
            const totalScore = answers.reduce((a, b) => a + b, 0);
            const normalizedScore = Math.round(totalScore / 30);
            
            const categoryScores = {};
            questions.forEach((q, index) => {
                if (!categoryScores[q.category]) {
                    categoryScores[q.category] = { total: 0, count: 0 };
                }
                categoryScores[q.category].total += answers[index] || 0;
                categoryScores[q.category].count++;
            });
            
            let description = '';
            if (normalizedScore >= 80) {
                description = '🌟 훌륭합니다! 자녀를 AI 시대에 잘 준비시키고 계십니다. 현재의 방향을 유지하면서 부족한 부분을 보완하세요.';
            } else if (normalizedScore >= 60) {
                description = '👍 좋은 기반이 있습니다! 부족한 영역을 보충하면 더욱 완성된 교육이 될 것입니다.';
            } else if (normalizedScore >= 40) {
                description = '📚 개선의 여지가 있습니다. 작은 변화부터 시작해보세요. 모든 영역에서 성장 가능합니다.';
            } else {
                description = '🚀 지금부터 시작하세요! 조금씩 변화를 만들면 큰 차이가 납니다. 함께 배워나가세요.';
            }
            
            let feedbackHTML = '';
            const categoryOrder = Object.keys(categoryScores).sort();
            categoryOrder.forEach(category => {
                const data = categoryScores[category];
                const categoryScore = Math.round((data.total / (data.count * 100)) * 100);
                feedbackHTML += `
                    <div class="feedback-category">
                        <div>
                            <span class="category-score">${categoryScore}점</span>
                            <h3>${category}</h3>
                        </div>
                        <p class="feedback-text">${feedbackData[category]?.feedback || ''}</p>
                        <div class="suggestions">${feedbackData[category]?.suggestions || ''}</div>
                    </div>
                `;
            });
            
            document.getElementById('quizContainer').classList.remove('show');
            document.getElementById('resultsContainer').classList.add('show');
            document.getElementById('scoreNumber').textContent = normalizedScore;
            document.getElementById('scoreDescription').textContent = description;
            document.getElementById('feedbackContent').innerHTML = feedbackHTML;
            window.scrollTo(0, 0);
        }
        
        function retakeQuiz() {
            currentQuestion = 0;
            answers = new Array(questions.length).fill(null);
            document.getElementById('resultsContainer').classList.remove('show');
            document.getElementById('quizContainer').classList.add('show');
            document.getElementById('progressBar').classList.add('show');
            document.getElementById('progress').style.width = '0%';
            
            document.querySelectorAll('.question-card').forEach((card, index) => {
                card.classList.toggle('active', index === 0);
                const inputs = card.querySelectorAll('input[type="radio"]');
                inputs.forEach(input => input.checked = false);
            });
            
            updateNavigation();
            window.scrollTo(0, 0);
        }
    </script>
</body>
</html>
