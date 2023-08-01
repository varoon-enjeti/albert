# Mixed-Language Interpreting Speech-to-Text API

### This Project is a Work-In-Progress

### Use Case:
Heritage & Intermediate Language Learners

### Problem:
The existing landscape of speech-to-text APIs provides valuable functionality for converting spoken language into written text. However, these APIs are primarily designed to handle single-language inputs, resulting in limitations when dealing with mixed-language scenarios.
<br>  
More specifically, the absence of a reliable Mixed-Language Interpreting Speech-to-Text API poses a significant challenge for various applications, especially for language learning platforms with speaking components. Currently, users who speak multiple languages, especially at the intermediate or heritage level, face difficulties in accurately transcribing their speech when they switch between languages within a single sentence or paragraph. This limitation hampers the effectiveness and usability of speech-to-text technology for linguistic analysis.
<br>  
Consider the scenario where a learner has intermediate or heritage level proficiency in Korean and native proficiency in English, utilizing a language learning application that can listen to their voice and provide linguistic analysis feedback. These speakers often encounter limitations in their vocabulary and may find it challenging to fully express themselves in the learning language. As a result, they resort to incorporating words or phrases from their native language within their speech. Existing speech-to-text APIs struggle to accurately interpret and transcribe these mixed-language inputs, leading to incomplete or inaccurate transcriptions. This deficiency in handling mixed-language scenarios poses a significant obstacle for language learning analysis.

### Approach:
**Example Scenario:**
- **Language A:** English (Native Language)
- **Language B:** Korean (Intermediate/Heritage Language)

The core idea behind our approach is to simultaneously run two calls of the Deepgram API for both English and Korean languages on the user's voice audio. Deepgram's API provides confidence values for each word in the form of a JSON output (which can be converted in Python), enabling us to analyze and compare the translations in each language.
<br>  
When processing a mixed-language input, we focus on the Korean translation and identify words with low confidence values. These low confidence values indicate a potential difficulty in accurately recognizing and transcribing the word. To improve the accuracy, we compare the corresponding English translation for the same segment and check if the word was spoken in the other language.
<br>  
By analyzing the confidence values and cross-referencing the translations, we can identify the words that are more likely to be from the Language B and concatenate them together, forming a coherent transcription in Language A. This approach allows us to capture and retain the nuanced meaning of mixed-language speech, providing users with a reliable and fluent transcript that can then be used for linguistic analysis and feedback.

### Tools & Technologies:
- Python
  - [Deepgram API](https://deepgram.com)
  - Pandas
<br>   
