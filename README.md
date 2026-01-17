# Oracle Bot V2 - Enhanced Psychology Coach

## 🎯 Overview

Oracle Bot V2 is an advanced AI-powered psychology coach that uses the Deepsyke natal type system to provide personalized self-discovery guidance. This enhanced version includes comprehensive profile intake, integration analysis, gravitor pattern detection, and relationship dynamics.

## ✨ Key Features

### 1. **Comprehensive Profile Intake**
- Basic information (name, gender, birth date)
- 5 optional self-discovery questions:
  - Personality description
  - Goals and aspirations
  - Challenges and obstacles
  - Environmental support factors
  - Past influences shaping present

### 2. **Relationship Type Calculation**
- Add up to 4 significant people
- Automatic natal type calculation for each
- Strategic integration into conversations
- Family dynamics and influence analysis

### 3. **Integration Level Analysis**
- Assess alignment with natal type
- Identify high/medium/low integration
- Provide evidence-based insights
- Suggest alignment strategies

### 4. **Gravitor Pattern Detection**
- Analyze dominant type themes in profile
- Identify conflicts between natal type and expression
- Determine zone alignment (Social/Deep/Mixed)
- Balance gravitor patterns

### 5. **Personalized AI Context**
- All profile data used in conversations
- Relationship types referenced strategically
- Cultural Avatars used sparingly (1 per 5-7 messages)
- Type-specific guidance and insights

### 6. **Elegant User Interface**
- Deep purple/gold theme
- Smooth animations
- Responsive design
- Intuitive form layout

## 🚀 Deployment

### Local Testing
```bash
cd oracle-bot-v2
pip install -r requirements.txt
python app.py
```
Access at: http://localhost:9010

### Render Deployment

#### Prerequisites
- Render.com account
- GitHub repository
- Groq API key (set as environment variable `GROQ_API_KEY`)

#### Steps
1. Create GitHub repository (e.g., `oracle-bot-v2`)
2. Push all files to repository
3. Create new web service on Render
4. Configure build settings:
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python app.py`
5. Add environment variable: `GROQ_API_KEY`
6. Deploy!

#### Important: GitHub Folder Structure
When creating the `templates/index.html` file on GitHub, you must:
1. Create a file named `templates/index.html` (with the forward slash)
2. GitHub will automatically create the `templates` folder and place `index.html` inside it
3. Do not create the folder separately - let GitHub handle it

## 📁 File Structure

```
oracle-bot-v2/
├── app.py                          # Main Flask application
├── requirements.txt                # Python dependencies
├── natal_calculator.py             # Natal type calculation logic
├── ai_system_prompt.txt            # AI instructions and guidelines
├── business_rag.json               # Psychology coach knowledge
├── cultural_avatars_rag.json       # Cultural Avatar definitions
├── deepsyke_core_rag.json          # Core Deepsyke system knowledge
├── engagement_protocol.json        # Type-specific engagement strategies
├── templates/
│   └── index.html                  # Enhanced user interface
├── start.sh                        # Start script
└── .render-build.sh                # Render build script
```

## 🔧 Configuration

### Environment Variables
- `GROQ_API_KEY`: Required for AI responses
- `PORT`: Optional (defaults to 9010)

### API Endpoints

#### Health Check
```
GET /health
GET /api/health
```

#### Initialize Profile
```
POST /init-profile
POST /api/init-profile

Body:
{
  "name": "John",
  "gender": "male",
  "birth_date": "1990-01-15",
  "session_id": "sess_12345",
  "profile_data": {
    "personality": "Thoughtful, analytical...",
    "goals": "To understand myself better...",
    "challenges": "Difficulty making decisions...",
    "environment": "Supportive friends...",
    "past": "Childhood experiences..."
  },
  "relationships": [
    {
      "name": "Mark",
      "gender": "male",
      "birth_date": "1980-09-24"
    },
    {
      "name": "Sarah",
      "gender": "female",
      "birth_date": "1985-03-15"
    }
  ]
}

Response:
{
  "success": true,
  "greeting": "Personalized greeting...",
  "natal_type": "SS",
  "profile_analysis": {
    "integration_level": "medium",
    "dominant_gravitors": ["SS", "DD"],
    "zone_alignment": "mixed",
    "evidence": [...]
  },
  "relationships": [
    {
      "name": "Mark",
      "gender": "male",
      "birth_date": "1980-09-24",
      "natal_type": "SS"
    }
  ]
}
```

#### Chat
```
POST /chat
POST /api/chat

Body:
{
  "message": "I'm feeling stuck...",
  "session_id": "sess_12345"
}

Response:
{
  "success": true,
  "response": "AI response with insights..."
}
```

## 🧠 Analysis Framework

### Integration Level
Assesses how well user aligns with their natal type:

- **High Integration**: Behaviors, values, and expressions match natal type
- **Medium Integration**: Some alignment, some conflict
- **Low Integration**: Struggling against their nature

**Indicators:**
- Self-description matches type characteristics?
- Goals align with type motivations?
- Challenges stem from type conflicts?
- Environment supports or hinders type expression?

### Gravitor Patterns
Identifies dominant type themes in user's profile:

- **SD Gravitors**: Support, guidance, structure, building
- **DS Gravitors**: Excitement, possibilities, exploration
- **DD Gravitors**: Clarity, decisions, structure, results
- **SS Gravitors**: Meaning, depth, connection, authenticity

**Analysis:**
- Count frequency of each gravitor type
- Note conflicts between natal type and dominant gravitors
- Identify zone alignment

### Zone Alignment
Determines psychological zone of operation:

- **Social Zone (SS/SD)**: Focus on people, relationships, support
- **Deep Zone (DS/DD)**: Focus on personal power, achievements, autonomy
- **Mixed Zone**: Balance between both

**Alignment with Natal Type:**
- Same zone → Aligned
- Opposite zone → Potential friction
- Mixed zone → Versatile but may lack focus

### Relationship Dynamics
Strategic integration of relationship types:

**When to Reference:**
- 1 per 5-7 messages (similar to CA frequency)
- When type dynamics are relevant to topic
- When explaining user's behaviors or patterns
- When exploring influence on development

**How to Reference:**
- Calculate each relationship's natal type
- Use type characteristics to explain interactions
- Make insightful connections to current situation

**Example:**
"I wonder if your brother Mark, who is a DD, was too forceful with you when you were young? This might have led to your rejection of authority figures and difficulties with men..."

## 🎨 AI Response Guidelines

### General Principles
1. **Direct & Concise**: Dive straight into answering
2. **Natural & Conversational**: Sound like a wise guide
3. **Personalized**: Reference specific profile data
4. **Transformative**: Frame insights as empowerment tools

### Response Structure

**Integration Analysis:**
1. State integration level
2. Provide specific evidence
3. Explain implications
4. Suggest alignment strategies

**Gravitor Pattern:**
1. State dominant gravitor type(s)
2. Note alignment or conflict with natal type
3. Explain zone implications
4. Suggest balancing strategies

**Relationship Interjection:**
1. Calculate and state their type
2. Connect type to relevant behavior
3. Explain impact on user
4. Make insightful connection to current topic

### Banned Patterns
- "That's a great question"
- "That's an interesting point"
- Repetitive phrases (exciting, support, meaning, etc.)
- Same theme within 5 messages
- Same opening/closing structure twice in row

## 🔒 Session Management

Sessions store:
- User profile data
- Natal type and analysis
- Relationship information
- Conversation history
- Message counts (for CA frequency control)

**Important**: In production, use Redis or database for session storage instead of in-memory dictionary.

## 🎯 CA Frequency Control

**STRICT RULE**: Maximum 1 Cultural Avatar reference per 5-7 user messages.

Only use CA when:
- Highly relevant to current topic
- Provides unique insight not available elsewhere
- Enhances understanding through archetypal pattern
- Not used in last 5-7 messages

## 📊 Testing Checklist

- [ ] Test with full profile data (all fields filled)
- [ ] Test with partial profile data (some fields empty)
- [ ] Test with only basic DOB (no optional fields)
- [ ] Verify relationship type calculations are accurate
- [ ] Verify integration level analysis works
- [ ] Verify gravitor pattern detection works
- [ ] Verify AI uses all context in responses
- [ ] Verify relationship references appear appropriately
- [ ] Verify CA references are sparse (1 per 5-7 messages)
- [ ] Test responsive design on mobile

## 🔄 Version History

### V2 (Current)
- Enhanced profile intake with 5 optional questions
- Relationship type calculation and integration
- Integration level analysis
- Gravitor pattern detection
- Zone alignment assessment
- Strategic relationship referencing
- Reduced CA frequency (1 per 5-7 messages)
- Comprehensive AI context

### V1
- Basic natal type calculation
- Simple chat interface
- Cultural Avatar references
- Type-specific greetings

## 📞 Support

For issues or questions:
1. Check Render logs for deployment errors
2. Verify GROQ_API_KEY is set correctly
3. Check that all JSON files are valid
4. Verify GitHub folder structure (templates/index.html)

## 🎉 Success Metrics

- CA frequency: Target 1 per 5-7 messages
- Theme variety: No repeats within 5 messages
- Type calculation: 100% accuracy
- Integration analysis: Consistent with profile data
- Gravitor detection: Identifies dominant patterns accurately
- Relationship integration: Strategic and insightful
- User engagement: Higher satisfaction with personalized insights

---

**Built with ❤️ using Deepsyke natal type system**