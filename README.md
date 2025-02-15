# Audio_Chatbot
Audio Chatbot as a credit consultant call

# Credit Card EMI Conversion Chatbot

## Overview

This Jupyter Notebook implements a chatbot designed to interact with customers and facilitate the conversion of their outstanding credit card balances into Equated Monthly Installments (EMIs). The chatbot uses speech recognition to understand user input and text-to-speech to provide responses, guiding the user through the EMI conversion process.

## Logic and Flow

The chatbot's logic is structured around a series of functions that handle different aspects of the conversation:

1.  **Initialization**: The chatbot starts by greeting the customer and introducing the EMI conversion offer.
2.  **Intent Recognition**: It listens for the user's response and uses keyword analysis to determine their intent (e.g., expressing interest, asking for more information, declining the offer).
3.  **EMI Tenure Selection**: If the user is interested, the chatbot presents them with a range of EMI tenure options (3, 6, 9, 12, 18, 24, or 36 months).
4.  **Tenure Confirmation**: Once the user selects a tenure, the chatbot calculates the monthly installment amount and confirms the details with the user, including the interest rate and processing fees.
5.  **Final Confirmation**: The chatbot seeks final confirmation from the user before processing the EMI conversion request.
6.  **Handling Objections**: The chatbot is equipped to handle common objections, such as concerns about the interest rate or EMI amount, and offers alternative solutions or additional information.
7.  **Closing**: The chatbot concludes the conversation by thanking the user and providing information on how to contact customer support for further assistance.

### Detailed Function Breakdown:

*   **`speak(text)`**: Takes text as input and uses `pyttsx3` to convert it into speech, which is then spoken to the user.
*   **`listen(timeout=10, phrase_time_limit=20)`**: Uses the `speech_recognition` library to listen to the user's microphone input. It attempts to recognize the speech using Google's Speech Recognition API and returns the recognized text. Includes error handling for unknown input, service unavailability, and timeout.
*   **`confirms_tenure(user_input)`**:
    *   Extracts the number of months spoken by the user from the `user_input` using regular expressions.
    *   Calculates the EMI amount based on the tenure.
    *   Constructs a response confirming the selected tenure, EMI amount, interest rate, and processing fees.
    *   Listens for the user's confirmation.
    *   If the user confirms, it finalizes the EMI conversion request and informs the user that they will receive confirmation via SMS.
    *   Handles scenarios where the user expresses concerns about the interest rate or EMI amount, offering alternative solutions or information.
*   **`yes_interested()`**:
    *   Presents the EMI tenure options to the user.
    *   Listens for the user's preferred tenure.
    *   Calls the `confirms_tenure` function to proceed with the selected tenure.
    *   Handles cases where the user asks to repeat the options or expresses a preference for a lower or higher tenure.
    *   Informs about the interest rate.
*   **`chatbot_logic(user_input)`**:
    *   Main function that orchestrates the chatbot's logic.
    *   It uses `word_tokenize` to break down the user's input into individual words.
    *   Based on the identified keywords, it calls the appropriate function to handle the user's request, such as `yes_interested` or `confirms_tenure`.
    *   Handles scenarios where the user is silent, declines the offer, or asks to be called later.

## Libraries and Tools Used

*   **`speech_recognition`**: For converting speech to text.
*   **`pyttsx3`**: For converting text to speech.
*   **`nltk`**: Natural Language Toolkit for tokenizing and analyzing text.
*   **`regex (re)`**: For pattern matching and extracting information from text using regular expressions.
*   **`time`**: For time-related functionalities (although not explicitly used in the provided code).

### NLTK Downloads

The following NLTK resources are used and need to be downloaded:

*   `punkt`: Sentence tokenizer.
*   `averaged_perceptron_tagger`: Part-of-speech tagger.
*   `maxent_ne_chunker`: Named entity chunker.
*   `words`: Word list.
*   `punkt_tab`: Punkt sentence tokenizer trained on tables.

## Example Conversation Flow

1.  **Chatbot**: "Hi Customer, I’m Vidya from TEST Bank, I have an exciting offer for you! Convert your outstanding Credit Card balance into easy EMIs, say yes to explore the option."
2.  **User**: "Yes, I am interested"
3.  **Chatbot**: "That's a great choice! You can convert your Credit Card outstanding amount of INR 5000 into 3, 6, 9, 12, 18, 24 or 36 equal monthly instalments. Could you please confirm your preferred EMI tenure? If you wish to hear this again, please say repeat."
4.  **User**: "Need lower tenure"
5.  **Chatbot**: "Oh! I understand your requirement, but currently, these are the available tenurity options. So, do you wish to opt for the tenure from 3, 6, 9, 12, 18, 24, 36 months?"
6.  **User**: "24 month"
7.  **Chatbot**: "Nice! You have selected 24 months EMI plan. Your monthly installment will be INR. 208.33 with an interest rate of 10% and processing fees of 1%. Please confirm shall I go ahead with your request?"
8.  **User**: "Need lesser interest"
9.  **Chatbot**: "I got it! but currently this rate of interest is offered for the tenure choosen and this is the best in the market. So do you wish to continue over the request or change your tenurity option?"
10. **User**: "Continue with the request"
11. **Chatbot**: "! As per your confirmation request to convert your outstanding to 24 months EMI plan, with a monthly instalment of INR 208.33 and interest rate of 10% is updated. You shall receive your confirmation shortly via SMS on your registered mobile number. Thank you!"

## Notes

*   The code assumes an outstanding credit card balance of INR 5000. This value can be modified in the `confirms_tenure` function.
*   The interest rate is set at 10%. This value can also be adjusted in the `confirms_tenure` function.
*   The chatbot's responses and logic can be further customized and expanded to handle a wider range of user inputs and scenarios.
*   Ensure all required libraries are installed (`pip install speech_recognition pyttsx3 nltk regex`).
*   The NLTK resources must be downloaded before running the code (`nltk.download('punkt')`, etc.).
