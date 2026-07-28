<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AI 급식 칼로리 도우미</title>
    <!-- Tailwind CSS 적용 (현대적이고 깔끔한 UI) -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* 로딩 스피너 애니메이션 */
        .spinner {
            border: 4px solid rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            border-top: 4px solid #ffffff;
            width: 24px;
            height: 24px;
            animation: spin 1s linear infinite;
            display: inline-block;
            vertical-align: middle;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
    </style>
</head>
<body class="bg-gray-50 text-gray-800 font-sans min-h-screen p-4 sm:p-8 flex justify-center items-start">

    <div class="max-w-md w-full bg-white rounded-2xl shadow-lg p-6 sm:p-8 mt-10">
        <!-- 헤더 영역 -->
        <div class="text-center mb-8">
            <h1 class="text-2xl sm:text-3xl font-bold text-green-600 mb-2">🍱 AI 칼로리 도우미</h1>
            <p class="text-gray-500 text-sm sm:text-base">오늘 먹을 급식이나 음식 사진을 올려주세요!</p>
        </div>

        <!-- 이미지 업로드 영역 -->
        <div class="mb-6">
            <label for="imageInput" class="block w-full border-2 border-dashed border-gray-300 rounded-xl p-6 text-center cursor-pointer hover:bg-gray-50 transition-colors">
                <span class="text-gray-500 font-medium flex flex-col items-center">
                    <svg class="w-10 h-10 mb-2 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 9a2 2 0 012-2h.93a2 2 0 001.664-.89l.812-1.22A2 2 0 0110.07 4h3.86a2 2 0 011.664.89l.812 1.22A2 2 0 0018.07 7H19a2 2 0 012 2v9a2 2 0 01-2 2H5a2 2 0 01-2-2V9z"></path><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 13a3 3 0 11-6 0 3 3 0 016 0z"></path></svg>
                    사진 촬영 또는 앨범 선택
                </span>
                <!-- 모바일에서 카메라 바로 띄우기: capture="environment" -->
                <input type="file" id="imageInput" accept="image/*" capture="environment" class="hidden">
            </label>
        </div>

        <!-- 이미지 미리보기 영역 -->
        <div id="previewContainer" class="hidden mb-6 rounded-xl overflow-hidden shadow-sm border border-gray-100">
            <img id="imagePreview" src="" alt="미리보기" class="w-full h-auto object-cover max-h-64">
        </div>

        <!-- 분석 버튼 -->
        <button id="analyzeBtn" class="w-full bg-green-500 hover:bg-green-600 text-white font-bold py-3 px-4 rounded-xl transition-colors disabled:bg-gray-300 disabled:cursor-not-allowed flex justify-center items-center gap-2" disabled>
            <span>영양소 분석하기</span>
            <div id="loadingSpinner" class="spinner hidden"></div>
        </button>

        <!-- 결과 출력 영역 -->
        <div id="resultContainer" class="hidden mt-8 p-5 bg-green-50 rounded-xl border border-green-100">
            <h3 class="font-bold text-green-800 mb-3 text-lg">💡 분석 결과</h3>
            <div id="resultText" class="text-gray-700 leading-relaxed whitespace-pre-wrap text-sm sm:text-base">
                <!-- 결과 텍스트가 여기에 들어갑니다. -->
            </div>
        </div>
    </div>

    <script>
        const imageInput = document.getElementById('imageInput');
        const imagePreview = document.getElementById('imagePreview');
        const previewContainer = document.getElementById('previewContainer');
        const analyzeBtn = document.getElementById('analyzeBtn');
        const loadingSpinner = document.getElementById('loadingSpinner');
        const resultContainer = document.getElementById('resultContainer');
        const resultText = document.getElementById('resultText');

        let base64Data = null;
        let imageMimeType = null;
        const apiKey = ""; // 실행 환경에서 자동으로 키가 주입됩니다.

        // 1. 이미지 선택 시 미리보기 및 Base64 변환
        imageInput.addEventListener('change', (e) => {
            const file = e.target.files[0];
            if (!file) return;

            imageMimeType = file.type;

            const reader = new FileReader();
            reader.onload = (event) => {
                const dataUrl = event.target.result;
                
                // 미리보기 이미지 업데이트
                imagePreview.src = dataUrl;
                previewContainer.classList.remove('hidden');
                
                // Base64 순수 데이터만 추출 (data:image/jpeg;base64, 이후)
                base64Data = dataUrl.split(',')[1];
                
                // 분석 버튼 활성화
                analyzeBtn.disabled = false;
                
                // 이전 결과 초기화
                resultContainer.classList.add('hidden');
                resultText.textContent = '';
            };
            reader.readAsDataURL(file);
        });

        // 2. 분석 버튼 클릭 시 서버리스 API 호출
        analyzeBtn.addEventListener('click', async () => {
            if (!base64Data) return;

            // UI 상태 변경 (로딩 중)
            analyzeBtn.disabled = true;
            analyzeBtn.querySelector('span').textContent = '분석 중...';
            loadingSpinner.classList.remove('hidden');
            resultContainer.classList.add('hidden');

            try {
                // 미리보기 환경을 위해 HTML 내에서 직접 Gemini API를 호출하도록 수정
                const endpoint = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
                const promptText = `
                이 급식 또는 음식 사진을 분석해주세요.
                1. 사진에 있는 음식들의 종류를 파악해주세요.
                2. 예상되는 총 칼로리를 알려주세요.
                3. 주요 영양소(탄수화물, 단백질, 지방 등)의 비율과 특징을 간단히 설명해주세요.
                4. 학생이나 일반인이 보기 좋게 이모지를 적절히 섞어서 친절하고 격려하는 말투로 작성해주세요.
                `;

                const response = await fetch(endpoint, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify({
                        contents: [{
                            parts: [
                                { text: promptText },
                                {
                                    inline_data: {
                                        mime_type: imageMimeType,
                                        data: base64Data
                                    }
                                }
                            ]
                        }]
                    })
                });

                if (!response.ok) {
                    throw new Error('분석 중 오류가 발생했습니다.');
                }

                const data = await response.json();

                // 결과 표시
                resultText.textContent = data.candidates?.[0]?.content?.parts?.[0]?.text || "분석 결과를 가져올 수 없습니다.";
                resultContainer.classList.remove('hidden');

            } catch (error) {
                console.error(error);
                alert(`오류: ${error.message}`);
            } finally {
                // UI 상태 복구
                analyzeBtn.disabled = false;
                analyzeBtn.querySelector('span').textContent = '영양소 분석하기';
                loadingSpinner.classList.add('hidden');
            }
        });
    </script>
</body>
</html>