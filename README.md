<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>4번째 계절 - Re:Life Tune Up 스타일</title>
    <style>
        /* 기본 리셋 및 폰트 설정 */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Noto Sans KR', sans-serif;
            color: #333;
            background-color: #ffffff;
            line-height: 1.6;
        }
        a {
            text-decoration: none;
            color: inherit;
        }

        /* 중앙 정렬 컨테이너 */
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* --- 상단 헤더 --- */
        header {
            border-bottom: 1px solid #eee;
            padding: 40px 0 0 0;
        }
        .header-top {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }
        .logo h1 {
            font-size: 28px;
            font-weight: 700;
            color: #222;
            font-family: 'Georgia', serif; /* 예시 화면의 진중한 느낌을 위한 세리프체 */
        }
        .header-util {
            display: flex;
            gap: 15px;
            align-items: center;
        }
        .search-icon {
            cursor: pointer;
            font-size: 18px;
        }

        /* --- 상단 내비게이션 --- */
        nav ul {
            display: flex;
            list-style: none;
            gap: 30px;
            padding-bottom: 15px;
        }
        nav ul li a {
            font-size: 14px;
            color: #666;
            font-weight: 500;
            transition: color 0.2s;
        }
        nav ul li a:hover, nav ul li.active a {
            color: #000;
            border-bottom: 2px solid #000;
            padding-bottom: 13px;
        }

        /* --- 메인 콘텐츠 레이아웃 (좌측 본문 / 우측 사이드바) --- */
        .main-wrapper {
            display: flex;
            gap: 50px;
            margin-top: 40px;
            padding-bottom: 60px;
        }

        /* 좌측 포스트 영역 (전체 너비의 약 75%) */
        .content-area {
            flex: 3;
        }
        .section-title {
            font-size: 16px;
            font-weight: bold;
            margin-bottom: 25px;
            color: #222;
        }
        .section-title span {
            color: #00b4d8; /* 예시의 파란색 숫자 강조 */
            margin-left: 5px;
        }

        /* 3열 카드 그리드 */
        .post-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 30px 20px;
        }
        .post-card {
            display: flex;
            flex-direction: column;
        }
        .post-thumbnail {
            width: 100%;
            height: 160px;
            background-color: #f5f5f5;
            border-radius: 4px;
            overflow: hidden;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #aaa;
            font-size: 14px;
            border: 1px solid #eaeaea;
        }
        /* 임시 이미지 대용 플레이스홀더 스타일 */
        .post-thumbnail.img-demo {
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            color: white;
            padding: 20px;
            text-align: center;
            font-weight: bold;
        }
        .post-title {
            font-size: 15px;
            font-weight: 600;
            line-height: 1.4;
            margin-bottom: 8px;
            color: #222;
            word-break: keep-all;
        }
        .post-desc {
            font-size: 13px;
            color: #777;
            line-height: 1.5;
            margin-bottom: 12px;
            display: -webkit-box;
            -webkit-line-clamp: 3; /* 3줄 넘어가면 말줄임 */
            -webkit-box-orient: vertical;
            overflow: hidden;
        }
        .post-date {
            font-size: 11px;
            color: #aaa;
            margin-top: auto;
        }

        /* --- 우측 사이드바 영역 (전체 너비의 약 25%) --- */
        .sidebar-area {
            flex: 1;
            border-left: 1px solid #eee;
            padding-left: 30px;
        }
        .widget {
            margin-bottom: 40px;
        }
        /* 사이드바 검색창 */
        .search-box {
            display: flex;
            border: 1px solid #ddd;
            padding: 5px 10px;
            border-radius: 4px;
        }
        .search-box input {
            border: none;
            outline: none;
            width: 100%;
            font-size: 13px;
        }
        .search-box button {
            background: #2a5298;
            color: white;
            border: none;
            padding: 3px 10px;
            border-radius: 3px;
            cursor: pointer;
            font-size: 12px;
        }

        /* 사이드바 카테고리 메뉴 */
        .widget-title {
            font-size: 14px;
            font-weight: 700;
            margin-bottom: 15px;
            color: #333;
        }
        .category-list {
            list-style: none;
        }
        .category-list li {
            margin-bottom: 12px;
            font-size: 13px;
            color: #555;
        }
        .category-list li a:hover {
            color: #2a5298;
            text-decoration: underline;
        }

        /* --- 하단 페이지네이션 --- */
        .pagination {
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 15px;
            margin-top: 50px;
            font-size: 14px;
            color: #777;
        }
        .pagination a {
            padding: 5px 10px;
        }
        .pagination a.active {
            color: #222;
            font-weight: bold;
        }

        /* 반응형 모바일 대응 */
        @media (max-width: 991px) {
            .main-wrapper {
                flex-direction: column;
            }
            .sidebar-area {
                border-left: none;
                padding-left: 0;
                border-top: 1px solid #eee;
                padding-top: 30px;
            }
            .post-grid {
                grid-template-columns: repeat(2, 1fr);
            }
        }
        @media (max-width: 600px) {
            .post-grid {
                grid-template-columns: 1fr;
            }
            nav ul {
                overflow-x: auto;
                white-space: nowrap;
            }
        }
    </style>
</head>
<body>

    <!-- 상단 헤더 영역 -->
    <header>
        <div class="container">
            <div class="header-top">
                <div class="logo">
                    <h1><a href="#">4번째 계절 – Re:Life Tune Up</a></h1>
                </div>
                <div class="header-util">
                    <span class="search-icon">🔍</span>
                </div>
            </div>
            <!-- 네비게이션 메뉴 -->
            <nav>
                <ul>
                    <li class="active"><a href="#">홈</a></li>
                    <li><a href="#">Re:Life Tune up</a></li>
                    <li><a href="#">3개의 문</a></li>
                    <li><a href="#">6 Re:Lenz</a></li>
                    <li><a href="#">Note</a></li>
                    <li><a href="#">HAVE+</a></li>
                    <li><a href="#">Re:Hub</a></li>
                    <li><a href="#">방명록</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- 메인 콘텐츠 레이아웃 컨테이너 -->
    <div class="container">
        <div class="main-wrapper">
            
            <!-- 좌측 포스트 그리드 영역 -->
            <main class="content-area">
                <div class="section-title">전체 글 <span>15</span></div>
                
                <div class="post-grid">
                    <!-- 포스트 카드 1 -->
                    <article class="post-card">
                        <div class="post-thumbnail img-demo">[Re:View]<br>감정 문해사전</div>
                        <h2 class="post-title"><a href="#">[Re:View] 감정 문해사전 가나다순 목차 - 감정 글 한눈에 보기</a></h2>
                        <p class="post-desc">걱정, 서운함, 상실감, 후회, 불안, 수용 등 감정 글을 안내문과 함께 찾아볼 수 있는 감정 문해사전 목차입니다.</p>
                        <span class="post-date">2026. 06. 28.</span>
                    </article>

                    <!-- 포스트 카드 2 -->
                    <article class="post-card">
                        <div class="post-thumbnail img-demo" style="background: linear-gradient(135deg, #8e44ad 0%, #c0392b 100%);">[Re:View]<br>파생 감정 지도</div>
                        <h2 class="post-title"><a href="#">[Re:View] 대표 감정별 파생 감정 지도 - 감정 흐름 목차</a></h2>
                        <p class="post-desc">마음은 가나다순으로 움직이지 않습니다. 서운함은 실망감으로 번지고, 상처받음은 원망이나 분노로 깊어집니다.</p>
                        <span class="post-date">2026. 06. 28.</span>
                    </article>

                    <!-- 포스트 카드 3 -->
                    <article class="post-card">
                        <div class="post-thumbnail img-demo" style="background: linear-gradient(135deg, #2c3e50 0%, #3498db 100%);">NOTE<br>연결허브</div>
                        <h2 class="post-title"><a href="#">Note 연결허브 안내지도 - 문해력 공방에서 독서까지</a></h2>
                        <p class="post-desc">이 글은 디지털 국어 도서관의 Note 계열 안내글을 한곳에서 찾아볼 수 있도록 묶은 통합 연결 지도입니다.</p>
                        <span class="post-date">2026. 06. 28.</span>
                    </article>

                    <!-- 포스트 카드 4 -->
                    <article class="post-card">
                        <div class="post-thumbnail img-demo" style="background: linear-gradient(135deg, #16a085 0%, #f4d03f 100%);">6 Re:Lenz<br>안내 지도</div>
                        <h2 class="post-title"><a href="#">6 Re:Lenz 안내 지도 - 세상을 읽는 여섯 개의 렌즈</a></h2>
                        <p class="post-desc">현대사회, 고전, 상징, 철학, 언어, 경제를 각각 다른 방향에서 바라보며 복잡한 삶을 조금 더 분명하게 이해합니다.</p>
                        <span class="post-date">2026. 06. 16.</span>
                    </article>

                    <!-- 포스트 카드 5 -->
                    <article class="post-card">
                        <div class="post-thumbnail img-demo" style="background: linear-gradient(135deg, #e67e22 0%, #e74c3c 100%);">[Re:Hub]<br>권력과 침묵</div>
                        <h2 class="post-title"><a href="#">[Re:Hub] 권력보다 더 무서운 침묵 ― 사랑의 반대는 왜 무관심인가</a></h2>
                        <p class="post-desc">침묵과 무관심, 중립과 외면, 방관과 여론조작이 어떻게 연결되는지 관계와 사회의 관점에서 읽습니다.</p>
                        <span class="post-date">2026. 05. 31.</span>
                    </article>

                    <!-- 포스트 카드 6 -->
                    <article class="post-card">
                        <div class="post-thumbnail img-demo" style="background: linear-gradient(135deg, #4a148c 0%, #880e4f 100%);">[Re:Hub]<br>쉬어도 불안한 이유</div>
                        <h2 class="post-title"><a href="#">[Re:Hub] 왜 현대인은 쉬어도 불안할까? - 멈추는 감각의 상실</a></h2>
                        <p class="post-desc">몸은 멈췄지만 마음은 멈추지 않습니다. 현대인의 휴식 불안, 미래불안, 번아웃을 통해 마음을 읽어봅니다.</p>
                        <span class="post-date">2026. 05. 26.</span>
                    </article>
                </div>

                <!-- 하단 페이지네이션 -->
                <div class="pagination">
                    <a href="#">&lt;</a>
                    <a href="#" class="active">1</a>
                    <a href="#">2</a>
                    <a href="#">3</a>
                    <a href="#">&gt;</a>
                </div>
            </main>

            <!-- 우측 사이드바 영역 -->
            <aside class="sidebar-area">
                <!-- 검색 위젯 -->
                <div class="widget">
                    <div class="search-box">
                        <input type="text" placeholder="검색어를 입력하세요.">
                        <button>검색</button>
                    </div>
                </div>

                <!-- 카테고리 위젯 -->
                <div class="widget">
                    <h3 class="widget-title">분류 전체보기</h3>
                    <ul class="category-list">
                        <li><a href="#">Re:Life Tune Up (전체 세계관)</a></li>
                        <li><a href="#">블로그 단위의 통로(3개의 문) 안내 지도</a></li>
                        <li><a href="#">6 Re:Lenz (세상을 읽는 눈)</a></li>
                        <li><a href="#">Note (세상을 이해하는 도구)</a></li>
                        <li><a href="#">HAVE+ (삶을 새로 배우고 설계한다)</a></li>
                        <li><a href="#">Re:Hub (세상을 바라보는 연결망)</a></li>
                    </ul>
                </div>
            </aside>

        </div>
    </div>

</body>
</html>
