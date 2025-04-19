<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>NYTimes Styled News with AI Summary (Placeholder)</title>
    <style>
        /* Placeholder fonts - replace with actual NYT fonts if available via CDN */
        @font-face {
            font-family: 'nyt-cheltenham';
            src: local('Times New Roman'), serif; /* A common fallback serif */
            font-style: normal;
            font-weight: 400;
        }
        @font-face {
            font-family: 'nyt-franklin';
            src: local('Arial'), sans-serif; /* A common fallback sans-serif */
            font-style: normal;
            font-weight: 700;
        }

        body {
            font-family: 'nyt-cheltenham', serif;
            background-color: #f0f0f0;
            margin: 0;
            padding: 20px;
            color: #333;
            line-height: 1.6;
        }
        h1 {
            font-family: 'nyt-franklin', sans-serif;
            text-align: center;
            margin-bottom: 2rem;
            font-size: 2.5rem;
            color: #222;
            letter-spacing: -0.02em;
        }
        .container {
            max-width: 960px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }
        .article {
            background: white;
            padding: 20px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            border-radius: 4px;
            border: 1px solid #ddd;
            display: flex;
            flex-direction: column;
        }
        .article h2 {
            font-family: 'nyt-cheltenham', serif;
            margin-top: 0;
            margin-bottom: 0.75rem;
            font-size: 1.5rem;
            color: #222;
            line-height: 1.3;
        }
        .article p.snippet {
            color: #555;
            margin-bottom: 1rem;
            font-size: 0.95rem;
            line-height: 1.4;
        }
        .summary-container {
            margin-top: 1rem;
            padding: 10px;
            background-color: #f9f9f9;
            border: 1px solid #eee;
            border-radius: 4px;
            font-size: 0.9rem;
            color: #666;
        }
        .summary-container.hidden {
            display: none;
        }
        .summary-title {
            font-weight: bold;
            margin-bottom: 0.5rem;
            color: #444;
        }
        button.summarize-button {
            background-color: #007bff;
            color: white;
            border: none;
            padding: 0.6rem 1rem;
            border-radius: 4px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: background-color 0.2s ease;
            margin-top: auto; /* Push button to the bottom */
        }
        button.summarize-button:hover {
            background-color: #0056b3;
        }
        .loading-indicator {
            display: none;
            font-size: 0.8rem;
            color: #777;
            margin-top: 0.5rem;
        }
        .error-message {
            display: none;
            font-size: 0.8rem;
            color: red;
            margin-top: 0.5rem;
        }
        .divider {
            border-top: 1px solid #eee;
            margin-top: 15px;
            padding-top: 15px;
        }
    </style>
</head>
<body>
    <h1>NYTimes Style - AI Summarized Articles</h1>

    <div class="container">
        <div class="article">
            <h2>Article 1: The Rise of Renewable Energy</h2>
            <p class="snippet">Solar, wind, and other renewable energy sources are becoming increasingly cost-effective and are playing a larger role in the global energy mix. Recent policy changes and technological advancements have further accelerated this trend, leading to significant investments in the sector...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article1-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article1">Loading summary...</div>
            <div class="error-message" id="error-article1">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article1">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 2: Global Markets React to Inflation Data</h2>
            <p class="snippet">New inflation figures released today have caused significant volatility in stock markets worldwide, with investors reacting to concerns about potential interest rate hikes by central banks. The energy and technology sectors have been particularly affected...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article2-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article2">Loading summary...</div>
            <div class="error-message" id="error-article2">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article2">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 3: Breakthrough in Cancer Research</h2>
            <p class="snippet">Scientists at a leading research institution have announced a promising new immunotherapy treatment that shows significant results in treating a specific type of aggressive lung cancer. Early trials indicate a higher survival rate and fewer side effects compared to traditional chemotherapy...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article3-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article3">Loading summary...</div>
            <div class="error-message" id="error-article3">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article3">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 4: New Legislation Targets Tech Giants</h2>
            <p class="snippet">Lawmakers in the European Union have unveiled a new set of digital regulations aimed at curbing the power and anti-competitive practices of major technology companies. The proposed legislation includes measures on data privacy, market dominance, and content moderation...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article4-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article4">Loading summary...</div>
            <div class="error-message" id="error-article4">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article4">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 5: AI and the Future of Work</h2>
            <p class="snippet">A comprehensive new report by the World Economic Forum explores the potential impact of artificial intelligence and automation on various industries and the future of the job market. The findings suggest a significant shift in required skills and potential job displacement in certain sectors...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article5-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article5">Loading summary...</div>
            <div class="error-message" id="error-article5">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article5">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 6: Climate Change and Coastal Cities</h2>
            <p class="snippet">Rising sea levels and the increasing frequency of extreme weather events pose significant and growing challenges for coastal urban areas around the world. Experts are calling for urgent action on mitigation and adaptation strategies to protect vulnerable populations and infrastructure...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article6-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article6">Loading summary...</div>
            <div class="error-message" id="error-article6">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article6">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 7: SpaceX Launches New Rocket</h2>
            <p class="snippet">SpaceX successfully launched its latest generation Falcon Heavy rocket earlier today, carrying a payload of advanced communication satellites for global internet access. The launch marks another milestone in the company's ambitious space exploration and commercialization efforts...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article7-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article7">Loading summary...</div>
            <div class="error-message" id="error-article7">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article7">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 8: Education Trends in the Digital Age</h2>
            <p class="snippet">The COVID-19 pandemic has significantly accelerated the adoption of digital tools and online platforms in education, leading to new trends and challenges for students, educators, and institutions. The long-term impact on learning outcomes and pedagogical approaches is still being assessed...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article8-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article8">Loading summary...</div>
            <div class="error-message" id="error-article8">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article8">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 9: Sports Analytics and Performance</h2>
            <p class="snippet">Advanced statistical analysis and data-driven insights are increasingly being used in professional sports to gain a competitive edge, optimize player performance, and inform strategic decisions both on and off the field. This trend is transforming how teams are managed and games are played...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article9-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article9">Loading summary...</div>
            <div class="error-message" id="error-article9">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article9">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
        <div class="article">
            <h2>Article 10: Mental Health Awareness Rises</h2>
            <p class="snippet">There is a growing public awareness and open discussion surrounding mental health issues, leading to increased support services, reduced stigma, and a greater emphasis on well-being in communities and workplaces. However, significant challenges in access and resources still remain...</p>
            <button class="summarize-button" onclick="summarizeArticle(this, 'article10-content')">AI Summary</button>
            <div class="loading-indicator" id="loading-article10">Loading summary...</div>
            <div class="error-message" id="error-article10">Failed to load summary.</div>
            <div class="summary-container hidden" id="summary-article10">
                <div class="summary-title">AI Summary:</div>
                <p class="summary-text"></p>
            </div>
        </div>
    </div>

    <script>
        // Placeholder function for AI summarization
        async function getAiSummary(articleContentId) {
            // In a real application, this function would:
            // 1. Get the article content (either from a hidden element or by fetching via URL).
            // 2. Send the content to a backend API endpoint for AI summarization.
            // 3. Handle the response (including potential errors).
            // 4. Return the generated summary.

            // Simulate an API call with a Promise
            return new Promise((resolve, reject) => {
                setTimeout(() => {
                    const articleContent = document.getElementById(articleContentId)?.textContent;
                    if (articleContent) {
                        const placeholderSummaries = {
                            'article1-content': 'AI Summary: Renewable energy is growing due to policy and tech advancements.',
                            'article2-content': 'AI Summary: Inflation data caused global market volatility and rate hike concerns.',
                            'article3-content': 'AI Summary: New immunotherapy shows promise for aggressive lung cancer.',
                            'article4-content': 'AI Summary: EU proposes new digital regulations targeting tech giants.',
                            'article5-content': 'AI Summary: Report explores AI\'s impact on the future of work and skills.',
                            'article6-content': 'AI Summary: Coastal cities face increasing challenges from climate change and sea levels.',
                            'article7-content': 'AI Summary: SpaceX launched a Falcon Heavy rocket for global internet satellites.',
                            'article8-content': 'AI Summary: Pandemic accelerated digital trends in education with lasting impacts.',
                            'article9-content': 'AI Summary: Sports analytics are transforming team management and performance strategies.',
                            'article10-content': 'AI Summary: Mental health awareness is rising, but access to resources remains a challenge.'
                        };
                        resolve(placeholderSummaries[articleContentId] || 'AI Summary: Summary unavailable.');
                    } else {
                        reject('Could not retrieve article content.');
                    }
                }, 1500); // Simulate network delay
            });
        }

        function summarizeArticle(buttonElement, articleContentId) {
            const articleDiv = buttonElement.closest('.article');
            const summaryContainer = articleDiv.querySelector('.summary-container');
            const summaryTextElement = summaryContainer.querySelector('.summary-text');
            const loadingIndicator = articleDiv.querySelector('.loading-indicator');
            const errorMessage = articleDiv.querySelector('.error-message');

            // Show loading indicator, hide summary and error
            loadingIndicator.style.display = 'block';
            summaryContainer.classList.add('hidden');
            errorMessage.style.display = 'none';
            summaryTextElement.textContent = '';

            getAiSummary(articleContentId)
                .then(summary => {
                    summaryTextElement.textContent = summary;
                    summaryContainer.classList.remove('hidden');
                    loadingIndicator.style.display = 'none';
                })
                .catch(error => {
                    console.error("Error fetching summary:", error);
                    errorMessage.style.display = 'block';
                    loadingIndicator.style.display = 'none';
                });
        }
    </script>

    <div style="display: none;">
        <p id="article1-content">Solar, wind, and other renewable energy sources are becoming increasingly cost-effective and are playing a larger role in the global energy mix. Recent policy changes and technological advancements have further accelerated this trend, leading to significant investments in the sector...</p>
        <p id="article2-content">New inflation figures released today have caused significant volatility in stock markets worldwide, with investors reacting to concerns about potential interest rate hikes by central banks. The energy and technology sectors have been particularly affected...</p>
        <p id="article3-content">Scientists at a leading research institution have announced a promising new immunotherapy treatment that shows significant results in treating a specific type of aggressive lung cancer. Early trials indicate a higher survival rate and fewer side effects compared to traditional chemotherapy...</p>
        <p id="article4-content">Lawmakers in the European Union have unveiled a new set of digital regulations aimed at curbing the power and anti-competitive practices of major technology companies. The proposed legislation includes measures on data privacy, market dominance, and content moderation...</p>
        <p id="article5-content">A comprehensive new report by the World Economic Forum explores the potential impact of artificial intelligence and automation on various industries
