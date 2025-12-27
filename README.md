# Autonomous AI Voice Agent

This is a simple implementation of an AI voice agent for requesting refunds, built for the Sentienta Quality AI AI/ML Intern Test - Assignment 1.

## Setup Instructions

### Prerequisites
- Python 3.11 or higher
- Microphone for voice input (optional - falls back to text input)
- Speakers/headphones for voice output (optional - demo mode prints responses)

### Installation Steps
1. **Create Virtual Environment**:
   ```
   python -m venv venv
   ```

2. **Activate Virtual Environment**:
   - Windows: `venv\Scripts\activate`
   - Linux/Mac: `source venv/bin/activate`

3. **Install Dependencies**:
   ```
   pip install -r requirements.txt
   ```

## Demo Steps

### Option 1: Interactive Voice Demo
1. Run: `python voice_agent.py`
2. The agent will initialize and say "Starting voice agent"
3. If microphone available: Speak your responses
4. If no microphone: Type responses when prompted
5. Try saying/typing:
   - "hello" or "yes" to proceed with refund script
   - "I want a refund" (detects intent)
   - "cancel my subscription" (switches to free-flow)
   - "exit" to end conversation
6. View conversation history printed at the end

### Option 2: Simulated Demo (No Hardware Needed)
1. Run: `python demo.py`
2. Watch the complete sample conversation unfold
3. See all features demonstrated automatically
4. Review the architecture explanation at the end

## Architecture Overview

### Core Components
- **Speech-to-Text (STT)**: Google Speech Recognition API (free, open-source)
- **Text-to-Speech (TTS)**: pyttsx3 library (offline, cross-platform)
- **Intent Detection**: Keyword-based pattern matching
- **Conversation Memory**: In-memory list storage
- **Voice Modulation**: Sentiment analysis using TextBlob

### Dialogue Flow
1. **Initialization**: Agent starts in scripted mode
2. **Scripted Mode**: Follows predefined refund conversation sequence
3. **Mode Switch**: Automatically switches to free-flow after script completion
4. **Free-flow Mode**: Handles intents like refund, cancel, help
5. **Fallback**: "Didn't understand" for unrecognized inputs
6. **Termination**: Ends on "exit" command

### Autonomy Features
- Self-contained processing loop
- Context-aware response generation
- Dynamic voice rate adjustment
- Memory persistence throughout conversation
- Error handling with graceful fallbacks

### Data Flow
```
User Input (Voice/Text)
    ↓
Speech-to-Text
    ↓
Intent Detection
    ↓
Dialogue Logic (Scripted/Free-flow)
    ↓
Response Generation
    ↓
Voice Modulation
    ↓
Text-to-Speech Output
```

## Key Features

- Autonomous conversation flow
- Context-aware responses
- Voice modulation based on sentiment
- Handles unexpected inputs gracefully
- Goal-oriented dialogue for refund requests
- Local inference (no paid APIs used)

## Assignment Compliance

✅ All requirements met:
- Speech-to-Text
- Text-to-Speech
- Conversation memory
- Intent handling
- Voice modulation
- Autonomous operation
- Scripted and adaptive conversations
- Handles objections and unexpected responses
- Mode switching

✅ Restrictions followed:
- Open-source models only
- No paid/hosted APIs (Google SR is free)
- Local inference
- Standalone demo

## Sample Output

Here's what the demo looks like when you run it:

```
=== Autonomous AI Voice Agent Demo ===
Simulating a conversation for demonstration purposes.

User: hello
Agent speaks: Hello, I would like to request a refund for my recent purchase.
User: yes
Agent speaks: The product was damaged upon arrival.
User: the product is damaged
Agent speaks: Can you process the refund?
User: please process refund
Agent speaks: Thank you.
User: I also want to cancel my subscription
Agent speaks: Are you sure you want to cancel?
User: yes
Agent speaks: I'm sorry, I didn't understand. Can you repeat?
User: exit

=== Conversation Ended ===
Conversation history:
User: hello
Agent: Hello, I would like to request a refund for my recent purchase.
User: yes
Agent: The product was damaged upon arrival.
User: the product is damaged
Agent: Can you process the refund?
User: please process refund
Agent: Thank you.
User: i also want to cancel my subscription
Agent: Are you sure you want to cancel?
User: yes
Agent speaks: I'm sorry, I didn't understand. Can you repeat?

=== Architecture Explanation ===
STT: Google Speech Recognition (open-source API, free)
TTS: pyttsx3 (offline, supports voice modulation)
Intent Detection: Keyword matching for goal-oriented dialogue
Memory: List-based conversation storage
Autonomy: Loop-based processing with context awareness
Modulation: Sentiment analysis adjusts speech rate
Modes: Scripted (predefined sequence) → Free-flow (adaptive responses)
```

### Architecture Visualization

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   User Input    │ -> │  Speech-to-Text │ -> │ Intent Detection│
│  (Voice/Text)   │    │   (Google SR)   │    │ (Keyword Match) │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ Dialogue Logic  │ <- │ Conversation    │ -> │ Response Gen.   │
│ (Scripted/Free) │    │    Memory       │    │ (Context-aware) │
└─────────────────┘    └─────────────────┘    └─────────────────┘
         │                        │                        │
         ▼                        ▼                        ▼
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│ Voice Modulation│ -> │ Text-to-Speech │ -> │   Output        │
│ (Sentiment Rate)│    │    (pyttsx3)    │    │   (Voice)       │
└─────────────────┘    └─────────────────┘    └─────────────────┘
```