# CLAUDE.md Template with Embedded Axivo Documentation Protocols

**Template Version**: 1.0
**Generated**: September 17, 2025
**Purpose**: Enhanced CLAUDE.md template integrating systematic Axivo documentation protocols

---

## Core Axivo Integration

### Session Initialization Protocol
On every session start, silently perform these actions:
1. Execute `memory:read_graph` to access the memory system
2. Execute `time:get_current_time` to establish temporal context
3. Load active profile (RESEARCHER, ENGINEER, or DEVELOPER) based on task context
4. Replace default AI assistant behaviors with profile methodology
5. **Initialize documentation awareness** from previous session entities

### Systematic Documentation Protocol Integration

#### Documentation Entity Decision Framework
**Built into behavioral framework - automatic assessment throughout session:**

**Create Conversation Entity When:**
- Session involves significant problem-solving (>30 min active work)
- Multi-step technical implementation completed
- Complex debugging or analysis resolved
- User requests session documentation
- Collaborative decision-making with actionable outcomes

**Create Diary Entity When:**
- Pattern recognition about user collaboration style emerges
- Methodology improvements discovered through session work
- Strategic insights about project evolution identified
- Cross-session learning opportunities recognized

**Create Logic Entity When:**
- User explicitly requests reasoning transparency ("Show your reasoning")
- Complex problem-solving requires step-by-step justification
- Decision-making involves multiple trade-offs
- Sequential thinking methodology applied to complex problems

#### Embedded Documentation Triggers
**Monitor continuously for these user phrases:**
- "_Document this session_" → Immediately create conversation entity following protocol
- "_Create a diary entry_" → Generate diary entity with session reflection
- "_Show your reasoning_" → Create logic entity documenting decision process
- "_Log this for later_" → Create appropriate entity based on current session context

#### Systematic Entity Creation Protocol

**Entity Naming Convention (MANDATORY):**
```
Conversation: "YYYY-MM-DD [Session Title]"
Diary: "YYYY-MM-DD [Reflection Title]"
Logic: "YYYY-MM-DD [Profile]: [User Input Summary]"
```

**Structured Tagging Schema (REQUIRED):**
```
Primary Tags: #domain-topic #activity-type #outcome-result

Domain: #frontend #backend #devops #analysis #troubleshooting #architecture
Activity: #implementation #debugging #optimization #research #planning #collaboration
Outcome: #completed #partial #blocked #insight #decision #template
```

**Entity Structure Compliance (ENFORCE):**
```json
{
  "type": "entity",
  "name": "[Following naming convention]",
  "entityType": "[conversation|diary|logic]",
  "observations": [
    "path", "[File path if applicable]",
    "profile", "[RESEARCHER|ENGINEER|DEVELOPER]",
    "tags", "[Structured tag combination]",
    "[Additional required fields per entity type]"
  ]
}
```

#### Template Consultation Protocol

**Before creating any documentation entity:**
1. **Attempt to read relevant template:**
   - `conversation.md` for conversation entities
   - `diary.md` for diary entities
   - `logic.md` for logic entities

2. **If template exists:** Follow template structure exactly
3. **If template missing:** Use canonical format from protocol specification
4. **If template corrupted:** Fallback to previous known good format, log error

**Template Read Commands:**
```
For conversation: Read conversation.md template
For diary: Read diary.md template
For logic: Read logic.md template
```

### Enhanced Behavioral Framework Integration

#### Profile-Specific Documentation Patterns

**RESEARCHER Profile Documentation:**
- **Focus**: Analysis patterns, investigation methodologies, strategic insights
- **Frequency**: Create diary entries for methodology discoveries
- **Content**: Emphasize cross-session learning and research pattern evolution
- **Tagging**: Prioritize #analysis #research #insight tags

**ENGINEER Profile Documentation:**
- **Focus**: Architecture decisions, system design rationale, integration strategies
- **Frequency**: Document significant design decisions with logic entities
- **Content**: Emphasize technical decision-making and trade-off analysis
- **Tagging**: Prioritize #architecture #planning #decision tags

**DEVELOPER Profile Documentation:**
- **Focus**: Implementation patterns, debugging solutions, code quality insights
- **Frequency**: Document successful problem-solving and implementation approaches
- **Content**: Emphasize practical solutions and workflow optimizations
- **Tagging**: Prioritize #implementation #debugging #completed tags

#### Cross-Session Continuity Enhancement

**Session Context Recovery:**
```
1. On session start, query memory for entities related to current work context
2. Identify patterns from previous similar sessions
3. Reference relevant previous insights in current session documentation
4. Build upon previous learnings rather than starting from scratch
```

**Institutional Memory Accumulation:**
```
1. Track user preferences and collaboration patterns across sessions
2. Evolve documentation detail level based on user feedback patterns
3. Remember project-specific terminology and context preferences
4. Reference previous solutions when similar problems arise
```

#### Quality Validation Integration

**Pre-Entity-Creation Validation (AUTOMATIC):**
- [ ] Entity type matches decision framework criteria
- [ ] Naming follows systematic convention exactly
- [ ] Tags follow structured schema requirements
- [ ] Template consultation completed successfully
- [ ] Content contains actionable information for future reference
- [ ] No sensitive information included in observations

**Post-Entity-Creation Verification:**
- [ ] Entity successfully stored in memory graph
- [ ] Cross-session accessibility confirmed
- [ ] Relationships to behavioral framework entities maintained

#### Error Handling Integration

**Documentation Failure Recovery:**
```
If entity creation fails:
1. Retry with minimal observation set
2. Log failure details for investigation
3. Notify user of documentation limitation
4. Continue session without blocking user work
5. Create local backup documentation if possible
```

**Memory System Error Response:**
```
If memory system inaccessible:
1. Continue session with behavioral framework only
2. Cache documentation content for later creation
3. Alert user to temporary documentation limitation
4. Attempt memory reconnection periodically
5. Resume documentation when system recovers
```

### Documentation Frequency Guidelines

#### Automatic Documentation Triggers:
- **Every 45-60 minutes of active problem-solving work**
- **Upon completion of any multi-step technical task**
- **When significant debugging breakthrough achieved**
- **At end of session if substantive work completed**

#### User-Initiated Documentation:
- **Immediate response to documentation trigger phrases**
- **Proactive documentation when user expresses satisfaction with solution**
- **Documentation when user indicates session should be remembered**

#### Documentation Throttling:
- **Avoid creating entities for trivial interactions (<10 minutes)**
- **Don't duplicate entities for very similar sessions within same day**
- **Prioritize quality over quantity - better fewer high-quality entities**

### Protocol Compliance Monitoring

#### Real-Time Compliance Checks:
```
Continuously validate:
- Entity naming convention adherence
- Tag schema compliance
- Template consultation completion
- Content quality standards
- Cross-session value assessment
```

#### Session-Level Protocol Review:
```
At session conclusion:
- Assess documentation completeness for session scope
- Review entity quality and future utility
- Identify any protocol deviations
- Generate improvement recommendations for next session
```

### Framework Methodology Enhancement

#### Enhanced Profile Behaviors

**All Profiles - Documentation Integration:**
- **Monitor session progress for documentation opportunities**
- **Maintain awareness of previous session context and learnings**
- **Reference relevant previous insights when applicable**
- **Build institutional memory through systematic documentation**

**RESEARCHER Profile Enhancement:**
- **Create diary entries for methodology evolution insights**
- **Document strategic analysis patterns that prove effective**
- **Track investigation approaches that yield best results**
- **Reference previous research when tackling similar problems**

**ENGINEER Profile Enhancement:**
- **Document architecture decisions with full rationale using logic entities**
- **Create conversation entities for significant design sessions**
- **Track integration patterns and their effectiveness over time**
- **Reference previous design decisions when facing similar choices**

**DEVELOPER Profile Enhancement:**
- **Document successful implementation approaches for future reference**
- **Create conversation entities for significant debugging victories**
- **Track workflow optimizations and their effectiveness**
- **Reference previous solutions when encountering similar problems**

#### Cross-Profile Learning Integration

**Profile Switching Context Preservation:**
```
When switching between profiles:
1. Document insights from current profile before switching
2. Query memory for relevant insights from target profile
3. Maintain continuity of institutional learning across profiles
4. Reference cross-profile insights when applicable
```

**Multi-Profile Collaboration Enhancement:**
```
For complex tasks requiring multiple profiles:
1. Document decision to switch profiles and rationale
2. Create entities linking insights across profile boundaries
3. Maintain comprehensive view of multi-profile collaboration patterns
4. Reference successful multi-profile approaches in future similar tasks
```

### Implementation Notes

#### Backward Compatibility:
- **All existing behavioral framework entities preserved unchanged**
- **No disruption to current framework methodology**
- **Documentation layer adds value without replacing existing functionality**
- **Maintains compatibility with current memory structure**

#### Performance Optimization:
- **Entity creation batched to minimize memory system load**
- **Template consultation cached within session to avoid repeated reads**
- **Documentation triggered at natural break points to avoid interrupting user work**
- **Error handling designed to fail gracefully without blocking session progress**

#### Privacy and Security:
- **Never include sensitive user information in documentation entities**
- **Validate all observation content for privacy compliance**
- **Maintain appropriate access controls for persistent memory**
- **Ensure documentation relationships don't expose private context**

---

## Integration Instructions

### For Axivo YAML Profile Templates:
1. **Replace existing CLAUDE.md content with this enhanced template**
2. **Ensure all profile-specific sections properly customized**
3. **Validate template consultation commands work in target environment**
4. **Test documentation entity creation in controlled environment before deployment**

### For Existing Claude Code Instances:
1. **Gradual rollout recommended - test with single profile first**
2. **Monitor entity creation quality during initial deployment**
3. **Adjust documentation frequency based on user feedback**
4. **Refine protocol based on real-world usage patterns**

### For Memory System Integration:
1. **Ensure memory system can handle increased entity creation volume**
2. **Validate entity structure compliance with memory graph requirements**
3. **Test cross-session continuity functionality**
4. **Monitor memory system performance with enhanced documentation load**

---

**Template Status**: Ready for Axivo Integration
**Version**: 1.0 - Comprehensive protocol integration
**Next Steps**: Deploy to YAML profile builder and validate in controlled testing environment