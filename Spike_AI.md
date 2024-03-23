## Spike Findings

Our system should be able to do these

1. Voice recognition and convert speech to text  
   Convert patient voice to text

1. Natural Language Understanding (NLU)  
   Understand context, extract intent and entities about patient.  
   Might need to ask multiple questions
   Pass these entities to BE server

1. Response Generation  
   Provide natural-sounding response to the user  
   This can be based on Pre-defined Responses or a generative language model

### Tools

**Voice recognition and NLU**

- Google Dialogflow
- Microsoft Azure Bot Service
- Rasa
- Custom model using TensorFlow or PyTorch
- Amazon Lex (Natural Language Understanding)

**Voice Recognition**

- Google Cloud Speech-to-Text
- Amazon Transcribe
- Microsoft Azure Speech Services

**Response Generation**

- Pre-defined Responses
- Generative language model

<br/>

### NLU

- subfield of artificial intelligence (AI) and natural language processing (NLP)
- focuses on enabling computers to understand and interpret human language in a way that is meaningful
- NLU aims to comprehend the intent, context, and semantics of the information conveyed in natural language.
- NLU systems strive to understand the context of a conversation. This involves tracking the history of the dialogue and considering previous interactions to provide more accurate and relevant responses.
- NLU can analyze the sentiment expressed in text, whether it's positive, negative, or neutral. This is useful in applications where understanding user sentiment is important, such as customer feedback analysis.

<br/>

### Google Dialogflow

- Dialog flow handles the job of translating natural language into machine readable data using machine learning model trained by our examples
- Upon understanding the context and details it can hand this data to BE
- Dialog flow agent - Collecting what user said, Mapping it to an intent, taking action on it, providing user response
- Understanding
  - Hey google, play music - Hey google is the utterance (trigger)
  - Hey google, talk to smart scheduler - smart scheduler is the invocation name
  - I want to set an appointment - set appointment is the intent
  - Set an appointment for 5pm tomorrow - 5pm and tomorrow are entities
- Dialog flow does intent matching, Matching user phrase to intent, these training intents are provided by us
- Configure Actions and Parameters (define variables to collect and store) (like patient name, number, appointment date)
- Provide static or dynamic response to users based on server response
- Fulfillment is the BE code that we write to respond to a dynamic request (dialog flow has inbuilt integrations with gcf)

<br/>
<br/>

### References

- https://www.youtube.com/watch?v=Ov3CDTxZRQc
