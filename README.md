# API Documentation

### Overview

This API provides a suite of Natural Language Processing (NLP) functionalities, including text summarization, generation, classification, completion, keyword extraction, language detection, translation, topic modeling, and question answering. The API is designed to be versatile and user-friendly, offering developers powerful tools to integrate advanced NLP capabilities into their applications.

### Authentication

Authentication is required for all endpoints. Use an API key in the header of your requests:

```
x-key: YOUR_API_KEY
```

Please contact the API provider to obtain your API key.

### Guardrails

While not explicitly mentioned in the schema, it's recommended to implement guardrails to ensure the safe, secure, and ethical use of these NLP functionalities. These guardrails should protect against various types of violations, maintain content quality, prevent malicious usage, and comply with ethical guidelines.

## Available Endpoints

1. [Summarization](#summarization)
2. [Text Generation](#text-generation)
3. [Text Classification](#text-classification)
4. [Text Completion](#text-completion)
5. [Keyword Extraction](#keyword-extraction)
6. [Language Detection](#language-detection)
7. [Language Translation](#language-translation)
8. [Topic Modeling](#topic-modeling)
9. [Question Answering](#question-answering)

## Endpoints:

### Summarization

**Endpoint URL:** `POST /summarize`  
**Description:** Creates a summary of the provided text content.

#### Request Parameters

| Parameter      | Type     | Description                          | Required |
|----------------|----------|--------------------------------------|----------|
| content        | string   | The text to be summarized.           | Yes      |
| length         | integer  | Desired length of the summary.       | No       |
| style          | string   | Style of the summary.                | No       |
| focus          | string   | Specific aspects to focus on.        | No       |
| domain         | string   | Subject area of the content.         | No       |
| include_info   | string   | Additional information to include.   | No       |
| output_format  | string   | Format of the output (PLAIN_TEXT, MARKDOWN, HTML) | No |

#### Request Body Example

```json
{
  "content": "Lorem ipsum dolor sit amet, consectetur adipiscing elit...",
  "length": 100,
  "style": "concise",
  "focus": "main points",
  "domain": "general",
  "output_format": "PLAIN_TEXT"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": "Summarized content goes here..."
}
```

### Text Generation

**Endpoint URL:** `POST /generate`  
**Description:** Generates text based on the provided input and parameters.

#### Request Parameters

| Parameter      | Type     | Description                          | Required |
|----------------|----------|--------------------------------------|----------|
| content        | string   | The input text or prompt.            | Yes      |
| type           | string   | Type of text to generate.            | No       |
| length         | integer  | Desired length of generated text.    | No       |
| tone           | string   | Desired tone of the text.            | No       |
| domain         | string   | Subject area for the text.           | No       |
| focus          | string   | Specific focus for the generation.   | No       |
| output_format  | string   | Format of the output (PLAIN_TEXT, MARKDOWN, HTML) | No |

#### Request Body Example

```json
{
  "content": "Write a short story about a robot learning to paint.",
  "type": "creative",
  "length": 500,
  "tone": "whimsical",
  "domain": "science fiction",
  "output_format": "MARKDOWN"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": "Generated text in Markdown format..."
}
```

### Text Classification

**Endpoint URL:** `POST /text-classification`  
**Description:** Classifies the provided text into predefined or custom categories.

#### Request Parameters

| Parameter            | Type     | Description                          | Required |
|----------------------|----------|--------------------------------------|----------|
| content              | string   | The text to be classified.           | Yes      |
| predefined_categories| array    | List of predefined categories.       | No       |
| domain               | string   | Subject area for classification.     | No       |
| justification        | boolean  | Whether to include justification.    | No       |
| output_format        | string   | Format of the output (JSON)          | No       |

#### Request Body Example

```json
{
  "content": "The new smartphone features a high-resolution camera and 5G capability.",
  "predefined_categories": ["Technology", "Fashion", "Sports"],
  "domain": "consumer electronics",
  "justification": true,
  "output_format": "JSON"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": {
    "category": "Technology",
    "confidence": 0.95,
    "justification": "The text mentions smartphone features like camera and 5G, which are technology-related."
  }
}
```

### Text Completion

**Endpoint URL:** `POST /text-completion`  
**Description:** Completes the provided text based on the given context and parameters.

#### Request Parameters

| Parameter          | Type     | Description                          | Required |
|--------------------|----------|--------------------------------------|----------|
| content            | string   | The text to be completed.            | Yes      |
| domain             | string   | Subject area for completion.         | No       |
| completion_context | string   | Additional context for completion.   | No       |
| style              | string   | Desired style of completion.         | No       |
| length             | integer  | Desired length of completion.        | No       |
| output_format      | string   | Format of the output (PLAIN_TEXT, MARKDOWN, HTML) | No |

#### Request Body Example

```json
{
  "content": "The future of artificial intelligence is",
  "domain": "technology",
  "completion_context": "Focus on positive advancements",
  "style": "academic",
  "length": 200,
  "output_format": "PLAIN_TEXT"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": "Completed text goes here..."
}
```

### Keyword Extraction

**Endpoint URL:** `POST /keyword-extraction`  
**Description:** Extracts keywords from the provided text.

#### Request Parameters

| Parameter         | Type     | Description                          | Required |
|-------------------|----------|--------------------------------------|----------|
| content           | string   | The text to extract keywords from.   | Yes      |
| no_of_keywords    | integer  | Number of keywords to extract.       | No       |
| keywords_to_detect| array    | Specific keywords to look for.       | No       |
| domain            | string   | Subject area for extraction.         | No       |
| output_format     | string   | Format of the output (JSON)          | No       |

#### Request Body Example

```json
{
  "content": "Artificial intelligence and machine learning are revolutionizing various industries, from healthcare to finance.",
  "no_of_keywords": 5,
  "domain": "technology",
  "output_format": "JSON"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": {
    "keywords": ["artificial intelligence", "machine learning", "healthcare", "finance", "industries"]
  }
}
```

### Language Detection

**Endpoint URL:** `POST /language-detection`  
**Description:** Detects the language of the provided text.

#### Request Parameters

| Parameter     | Type     | Description                          | Required |
|---------------|----------|--------------------------------------|----------|
| content       | string   | The text to detect language from.    | Yes      |
| domain        | string   | Subject area of the text.            | No       |
| tone          | string   | Tone of the text.                    | No       |
| justification | boolean  | Whether to include justification.    | No       |
| output_format | string   | Format of the output (MARKDOWN, PLAIN_TEXT) | No |

#### Request Body Example

```json
{
  "content": "Bonjour, comment allez-vous?",
  "justification": true,
  "output_format": "PLAIN_TEXT"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": "Detected language: French\nJustification: The text contains common French greeting phrases."
}
```

### Language Translation

**Endpoint URL:** `POST /language-translation`  
**Description:** Translates text from one language to another.

#### Request Parameters

| Parameter        | Type     | Description                          | Required |
|------------------|----------|--------------------------------------|----------|
| target_language  | string   | The language to translate to.        | Yes      |
| content          | string   | The text to be translated.           | Yes      |
| source_language  | string   | The language of the input text.      | No       |
| domain           | string   | Subject area of the text.            | No       |
| tone             | string   | Desired tone of the translation.     | No       |
| style            | string   | Desired style of the translation.    | No       |
| idiom_and_culture| string   | Cultural context for translation.    | No       |
| output_format    | string   | Format of the output (PLAIN_TEXT, HTML) | No    |

#### Request Body Example

```json
{
  "target_language": "Spanish",
  "content": "Hello, how are you?",
  "source_language": "English",
  "tone": "casual",
  "output_format": "PLAIN_TEXT"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": "¡Hola! ¿Cómo estás?"
}
```

### Topic Modeling

**Endpoint URL:** `POST /topic-modeling`  
**Description:** Identifies main topics in the provided text.

#### Request Parameters

| Parameter                | Type     | Description                          | Required |
|--------------------------|----------|--------------------------------------|----------|
| content                  | string   | The text to model topics from.       | Yes      |
| no_of_topics_to_identify | integer  | Number of topics to identify.        | No       |
| domain                   | string   | Subject area of the text.            | No       |
| justification            | boolean  | Whether to include justification.    | No       |
| output_format            | string   | Format of the output (JSON)          | No       |

#### Request Body Example

```json
{
  "content": "Long text about various subjects...",
  "no_of_topics_to_identify": 3,
  "domain": "general",
  "justification": true,
  "output_format": "JSON"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": {
    "topics": [
      {
        "topic": "Technology",
        "keywords": ["AI", "blockchain", "cybersecurity"],
        "justification": "These terms are frequently mentioned in technology contexts."
      },
      {
        "topic": "Environment",
        "keywords": ["climate change", "sustainability", "renewable energy"],
        "justification": "These concepts are central to environmental discussions."
      },
      {
        "topic": "Healthcare",
        "keywords": ["telemedicine", "vaccines", "mental health"],
        "justification": "These terms are prevalent in modern healthcare discourse."
      }
    ]
  }
}
```

### Question Answering

**Endpoint URL:** `POST /question-answer`  
**Description:** Provides answers to questions based on given context or information.

#### Request Parameters

| Parameter        | Type     | Description                          | Required |
|------------------|----------|--------------------------------------|----------|
| question         | string   | The question to be answered.         | Yes      |
| context          | string   | Context for answering the question.  | No       |
| information      | string   | Additional information for answering.| No       |
| focus            | string   | Specific focus for the answer.       | No       |
| sources_citation | string   | Citation style for sources.          | No       |
| domain           | string   | Subject area of the question.        | No       |
| length           | integer  | Desired length of the answer.        | No       |
| output_format    | string   | Format of the output (MARKDOWN, PLAIN_TEXT, HTML) | No |

#### Request Body Example

```json
{
  "question": "What are the main causes of climate change?",
  "context": "Recent scientific studies on global warming",
  "focus": "human activities",
  "domain": "environmental science",
  "length": 200,
  "output_format": "MARKDOWN"
}
```

#### Response Example

```json
{
  "code": "SUCCESS",
  "message": "Response fetched successfully.",
  "data": "Markdown-formatted answer about the main causes of climate change, focusing on human activities..."
}
```

This documentation provides a comprehensive overview of the API's capabilities and how to use each endpoint. Users can refer to this guide to understand the required parameters, request formats, and expected responses for each NLP functionality offered by the API.
