# Oracle Bot V2 - Testing Guide

## 🧪 Quick Testing Scenarios

### Scenario 1: Full Profile with Relationships
**Purpose**: Test all features with complete data

**Input:**
```
Name: Alex
Gender: Male
Birth Date: September 24, 1980

Personality: "I'm a deep thinker who values meaningful connections. I tend to
overthink things and can get lost in my thoughts. I care deeply about authenticity
and can be sensitive to insincerity."

Goals: "To find my true purpose in life and build deeper relationships that matter.
I want to feel more aligned with who I really am."

Challenges: "I often feel disconnected from others, like I'm on a different wavelength.
I struggle with practical matters and can be indecisive. Sometimes I feel too sensitive."

Environment: "I have a few close friends who really understand me. My work environment
is okay but doesn't inspire me much."

Past: "Growing up, I always felt different from my family. My dad was very practical
and results-oriented, which clashed with my introspective nature."

Relationships:
1. Mark (brother): Jan 15, 1975, Male → SD
2. Sarah (mother): Mar 10, 1955, Female → DS
3. Tom (friend): July 20, 1982, Male → SD
```

**Expected Results:**
- Natal type: SS (Sep 24, 1980 Male)
- Integration: High (matches SS characteristics)
- Dominant gravitors: SS, possibly DS
- Zone: Social
- Greeting mentions: SS type, integration level, relationships
- First chat message references profile data

---

## 🎯 Success Criteria

### Must Work (Critical Path)
- [x] Basic profile submission
- [x] Type calculation
- [x] AI responds to messages
- [x] No crashes or errors
- [x] UI displays correctly

### Should Work (Enhanced Features)
- [ ] Profile analysis with integration
- [ ] Gravitor pattern detection
- [ ] Relationship type calculation
- [ ] Relationship references in chat
- [ ] Personalized greeting

---

**Happy Testing! 🧪**