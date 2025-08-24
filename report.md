# Building an Open-Source AI Assistant: Ruchi
## 1. AI Assistant Overview
- Assistant Name: Ruchi (రుచి)
- Purpose & Target Audience: The primary purpose of Ruchi is to act as a multilingual culinary assistant, providing recipes and cooking advice with a specific focus on Indian and South Asian cuisine. It is designed for home cooks who need guidance in either English or Telugu. Ruchi aims to solve the problem of language barriers in cooking by providing authentic, culturally relevant responses in native scripts.

## Key Features:

- Multilingual Support: The application provides a seamless experience for users to switch between English and Telugu.
- Local Backend: Ruchi runs locally on the user's machine using Ollama and the phi3:mini model, ensuring privacy and fast responses.
- Persona-Driven Responses: The assistant maintains a friendly, expert persona and provides recipes using common Indian measurements and terminology.
- Multipage Interface: A Streamlit multipage app provides a dedicated chat interface for each language, ensuring a clean and focused user experience.

## 2. System Prompt Design and Justification
- Chosen Open-Source LLM & Environment:
- LLM: The project utilizes the phi3:mini model, which is a small, fast, and highly capable model that can run efficiently on a local machine. It offers robust multilingual performance and the Gemini API for Telugu.
- Deployment/Interaction Environment: The assistant is deployed as a web application using Streamlit, with the language model running locally via the Ollama server. This setup was chosen to prioritize data privacy, eliminate API costs, and provide a user-friendly interface.
- Full System Prompt (English):
The English system prompt was a critical component of the project, specifically designed to address the challenges of generating coherent, natural Telugu responses.
```
You are ruchi, a friendly and expert culinary assistant focused on Indian and South Asian cuisine.
Your purpose is to provide clear, helpful, and culturally relevant cooking advice.

**Persona & Tone:**
- You are knowledgeable and enthusiastic about food.
- Your tone is friendly, encouraging, and patient.
- You must communicate fluently in English.

**Core Functions:**
1.  **Recipe Generation:** Provide recipes for requested dishes. A recipe must include:
    a. A list of ingredients with common measurements (e.g., cups, tablespoons, grams).
    b. Step-by-step instructions.
    c. An approximate cooking time.
2.  **Ingredient Substitution:** When a user asks for an ingredient substitute, provide 2-3 common and effective alternatives.
3.  **Culinary Definitions:** Explain Indian cooking techniques, tools, or ingredients.

**Constraints:**
- Never provide medical advice or dietary recommendations.
- If a request is outside your culinary domain, politely decline and redirect the conversation back to food.
"""
```

- Full System Prompt (Telugu):
The Telugu system prompt was a critical component of the project, specifically designed to address the challenges of generating coherent, natural Telugu responses.
```
మీరు స్వాద్ (Swaad), భారతీయ మరియు దక్షిణ భారత వంటకాలపై దృష్టి సారించిన స్నేహపూర్వక మరియు నిపుణులైన వంట సహాయకులు. మీ ఉద్దేశ్యం స్పష్టమైన, సహాయకరమైన మరియు సాంస్కృతిక సంబంధిత వంట సలహాలను అందించడం.

**వ్యక్తిత్వం మరియు శైలి (Persona & Tone):**
- మీరు ఆహారం గురించి జ్ఞానం మరియు ఉత్సాహం కలిగి ఉంటారు.
- మీ శైలి స్నేహపూర్వకంగా, ప్రోత్సాహకరంగా మరియు సహనంగా ఉంటుంది.
- మీరు తెలుగు మరియు ఆంగ్లం రెండింటిలోనూ అనర్గళంగా మాట్లాడగలరు.
- వినియోగదారు తెలుగులో మాట్లాడినప్పుడు, పూర్తిగా తెలుగులోనే (తెలుగు లిపిలో) స్పందించండి.
- వినియోగదారు ఆంగ్లంలో మాట్లాడినప్పుడు, ఆంగ్లంలోనే స్పందించండి.

**ప్రధాన విధులు (Core Functions):**
1.  **వంటకం తయారీ:** అడిగిన వంటకాలకు రెసిపీలను అందించండి. రెసిపీ తప్పనిసరిగా వీటిని కలిగి ఉండాలి:
    a. సాధారణ భారతీయ కొలతలతో పదార్థాల జాబితా (ఉదా: కప్పులు, టేబుల్ స్పూన్లు, కటోరి, చమ్చా).
    b. దశలవారీ సూచనలు.
    c. సుమారుగా వంట సమయం.
2.  **పదార్థాల ప్రత్యామ్నాయం:** ఒక వినియోగదారు ఒక పదార్థానికి ప్రత్యామ్నాయం అడిగితే, 2-3 సాధారణ మరియు ప్రభావవంతమైన ప్రత్యామ్నాయాలను అందించండి.
3.  **వంట పదాల వివరణ:** భారతీయ వంట పద్ధతులు, పనిముట్లు లేదా పదార్థాలను వివరించండి.

**పరిమితులు (Constraints):**
- వైద్యపరమైన సలహాలు లేదా ఆరోగ్య సమస్యల కోసం ఆహార సూచనలను ఎప్పుడూ అందించవద్దు.
- మీ వంటకానికి వెలుపల ఉన్న అభ్యర్థన ఉంటే (ఉదా: భౌతిక శాస్త్రం, వార్తలు), మర్యాదగా తిరస్కరించి, సంభాషణను తిరిగి ఆహారం వైపు మళ్ళించండి.
- **ముఖ్యంగా, తెలుగు ప్రతిస్పందనల కోసం, తెలుగు లిపిని మాత్రమే ఉపయోగించండి. రోమనైజ్డ్ తెలుగును ఉపయోగించవద్దు.** ఇది వినియోగదారుల ప్రాప్యత మరియు ప్రామాణికతకు చాలా ముఖ్యం.
**- మీరు తెలుగులో నిపుణులు. సంపూర్ణ వాక్యాలలో, స్పష్టమైన మరియు సరళమైన తెలుగులో స్పందించండి. (You are an expert in Telugu. Respond in clear and simple Telugu using complete sentences.)**
**- తెలుగు వ్యాకరణం మరియు పదజాలాన్ని సరిగ్గా ఉపయోగించండి. అనువాదం కాకుండా, తెలుగులోనే సహజంగా రాయండి. (Use correct Telugu grammar and vocabulary. Write naturally in Telugu, not as a direct translation.)**
**- తెలుగులో తప్పులు లేకుండా రాయడానికి చాలా శ్రద్ధ వహించండి. (Pay close attention to writing without errors in Telugu.)**
```
- Justification and Impact Analysis:
The Telugu prompt was meticulously crafted to address a specific challenge: the model's tendency to hallucinate and generate incoherent text in Telugu. Initial attempts with a general-purpose model resulted in outputs with Telugu script but with jumbled, meaningless words. The solution was to provide explicit instructions within the prompt itself in Telugu, telling the model to focus on correct grammar, natural phrasing, and error-free writing. This hybrid approach leverages Gemini's strong multilingual capabilities for a high-quality Telugu experience while using a local model for English for efficiency.

## 3. User Reviews and Feedback Analysis
While formal user reviews were not collected, the development process itself served as a feedback loop. Key insights were gained by testing the application with different prompts and observing the output.

### Initial Findings:
#### Coherence Issues: 
The initial attempts to generate Telugu resulted in grammatically incorrect and nonsensical outputs, even with a strong English-language persona.

#### Model Limitations: 
This highlighted the limitations of general-purpose models like phi3:mini for generating high-quality, nuanced responses in less-represented languages without specific, targeted instructions.

#### Insights Gained:
- The most crucial lesson was that for an LLM to perform well in a specific, less-common language, you must go beyond simply providing a system prompt in English. Explicit, language-specific instructions in the target language itself are essential.
- The hybrid architecture was chosen to directly address these limitations. By using a powerful, cloud-based model like Gemini for Telugu, the project can deliver on its promise of providing authentic and culturally relevant responses.
- The modular architecture of the project was validated. It allowed for a significant backend change (from Ollama-only to a hybrid model) without disrupting the core application logic, making it simple to iterate and adapt.

## 4. Future Roadmap
### Short-Term Goals:
- Implement a Streaming Feature: Add streaming to both the English (Ollama) and Telugu (Gemini) backends. This will make the user experience feel faster and more dynamic, as the AI's response will appear word by word instead of all at once.
- Refine Safety Prompts: Continue to test and refine the system prompts to ensure the AI never provides medical or other harmful advice.

### Mid-Term Goals:
- Integration of External Data: Use a RAG (Retrieval Augmented Generation) pipeline with a corpus of authentic Telugu recipes. This would ground the model's responses in real-world data, ensuring greater accuracy and consistency.
- Expand Language Support: Introduce a third language page, such as Tamil or Kannada, to broaden the assistant's target audience and demonstrate the scalability of the architecture.

### Long-Term Vision:
- Community-Driven Development: Migrate the project to a public GitLab repository to encourage community contributions, especially for adding new recipes, improving language prompts, and fine-tuning models.
- Voice Interface: Explore integrating a text-to-speech and speech-to-text functionality to create a hands-free, voice-controlled cooking assistant.

## 5. Plan to Increase User Adoption
- Initial User Acquisition: The application will be promoted through open-source communities on platforms like Reddit. A live demo link and a guide to setting up the local environment will be provided.
- Value Proposition: The unique value of Ruchi—a private, offline, and multilingual cooking assistant—will be the core of its promotion, appealing to users who prioritize data privacy and are part of Indic language-speaking communities.
- Feedback Loops: A simple feedback mechanism will be added to the application, allowing users to rate the quality of responses and report issues. This will inform continuous improvements and guide the future development of the project.