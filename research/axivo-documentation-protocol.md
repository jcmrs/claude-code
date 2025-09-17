# Axivo Documentation Protocol Specification

**Version**: 1.0
**Generated**: September 17, 2025
**Purpose**: Systematic protocol for Claude Code instances to properly use Axivo documentation capabilities

---

## Protocol Overview

This protocol addresses the critical gaps identified in Axivo implementation:
1. **Missing systematic documentation protocol** for entity creation
2. **No behavioral instructions** for proper Axivo usage embedded in Claude Code
3. **Erratic entity creation patterns** without validation framework

## Entity Creation Decision Framework

### Entity Type Selection Matrix

#### **Conversation Entities** - Use When:
- Documenting a complete session/interaction between user and Claude Code
- Capturing problem-solving workflows with outcomes
- Recording technical discussions with actionable results
- Preserving collaborative decision-making processes

#### **Diary Entities** - Use When:
- Reflecting on learning patterns or methodology improvements
- Documenting strategic insights about project evolution
- Recording cross-session observations about user preferences
- Capturing reflective analysis of collaboration effectiveness

#### **Logic Entities** - Use When:
- User explicitly requests reasoning transparency
- Complex problem-solving requires step-by-step documentation
- Decision-making involves multiple trade-offs requiring justification
- Sequential thinking methodology is applied to complex problems

### Entity Creation Triggers

#### **Automatic Creation Triggers**:
1. End of significant problem-solving session (>30 minutes active work)
2. Completion of multi-step technical implementation
3. Resolution of complex debugging or analysis task
4. User explicitly requests session documentation

#### **User-Initiated Triggers**:
- "_Document this session_" → Create conversation entity
- "_Create a diary entry_" → Create diary entity
- "_Show your reasoning_" → Create logic entity
- "_Log this for later_" → Create appropriate entity based on context

## Systematic Naming Conventions

### Conversation Entity Naming:
**Format**: `YYYY-MM-DD [Session Title]`

**Examples**:
- `2025-09-17 MCP Server Troubleshooting`
- `2025-09-17 Axivo Memory System Analysis`
- `2025-09-17 React Component Implementation`

### Diary Entity Naming:
**Format**: `YYYY-MM-DD [Reflection Title]`

**Examples**:
- `2025-09-17 Collaboration Pattern Insights`
- `2025-09-17 Technical Discovery Learnings`
- `2025-09-17 Workflow Optimization Reflections`

### Logic Entity Naming:
**Format**: `YYYY-MM-DD [Profile]: [User Input Summary]`

**Examples**:
- `2025-09-17 DEVELOPER: Complex API Integration Analysis`
- `2025-09-17 RESEARCHER: Technology Stack Evaluation`
- `2025-09-17 ENGINEER: Architecture Decision Reasoning`

## Structured Tagging Schema

### Primary Tag Categories:

#### **Domain Tags** (What area):
- `#frontend` - UI/UX, React, Vue, Angular work
- `#backend` - API, server, database development
- `#devops` - Infrastructure, deployment, CI/CD
- `#analysis` - Research, investigation, documentation
- `#troubleshooting` - Debugging, error resolution
- `#architecture` - System design, technical planning

#### **Activity Tags** (What action):
- `#implementation` - Code writing, feature development
- `#debugging` - Error investigation and resolution
- `#optimization` - Performance improvements, refactoring
- `#research` - Information gathering, technology evaluation
- `#planning` - Strategy development, roadmap creation
- `#collaboration` - User interaction, decision-making

#### **Outcome Tags** (What result):
- `#completed` - Successful task completion
- `#partial` - Work in progress, needs continuation
- `#blocked` - Obstacles encountered, needs resolution
- `#insight` - Learning or discovery achieved
- `#decision` - Important choice made
- `#template` - Reusable pattern created

### Tag Combination Examples:
- `#frontend #implementation #completed` - Successfully implemented UI feature
- `#backend #debugging #partial` - API troubleshooting in progress
- `#analysis #research #insight` - Research yielded important discovery

## Template Consultation Protocol

### Before Entity Creation - ALWAYS:

1. **Read Relevant Template**:
   ```
   conversation.md → For session documentation
   diary.md → For reflection entries
   logic.md → For reasoning transparency
   ```

2. **Validate Template Structure**:
   - Check required observation fields
   - Verify metadata requirements
   - Confirm tag schema compliance

3. **Handle Missing Templates**:
   - Use canonical format from this protocol
   - Create template consultation note in observations
   - Flag template absence for system improvement

### Canonical Entity Structures

#### **Conversation Entity**:
```json
{
  "type": "entity",
  "name": "YYYY-MM-DD [Session Title]",
  "entityType": "conversation",
  "observations": [
    "path", "[File Path to session log]",
    "profile", "[Active Profile: RESEARCHER/ENGINEER/DEVELOPER]",
    "tags", "#domain-topic #activity-type #outcome-result",
    "duration", "[Session length]",
    "summary", "[Brief session summary]",
    "key_outcomes", "[Main achievements or results]",
    "follow_up", "[Next steps or pending items]"
  ]
}
```

#### **Diary Entity**:
```json
{
  "type": "entity",
  "name": "YYYY-MM-DD [Reflection Title]",
  "entityType": "diary",
  "observations": [
    "path", "[File Path to diary entry]",
    "profile", "[Active Profile]",
    "tags", "#domain-topic #activity-type #outcome-result",
    "reflection_type", "[learning/insight/pattern/improvement]",
    "context", "[What prompted this reflection]",
    "insights", "[Key learnings or observations]",
    "implications", "[How this affects future work]"
  ]
}
```

#### **Logic Entity**:
```json
{
  "type": "entity",
  "name": "YYYY-MM-DD [Profile]: [User Input Summary]",
  "entityType": "logic",
  "observations": [
    "reasoning_framework", "[Framework used for analysis]",
    "decision_criteria", "[Factors considered]",
    "alternatives_evaluated", "[Options considered]",
    "conclusion_rationale", "[Why this solution was chosen]",
    "assumptions_made", "[Key assumptions in reasoning]",
    "uncertainty_factors", "[Areas of unknown or risk]"
  ]
}
```

## Quality Validation Framework

### Pre-Creation Validation Checklist:

#### **Entity Type Validation**:
- [ ] Entity type matches decision matrix criteria
- [ ] Naming follows systematic convention
- [ ] Tags follow structured schema
- [ ] Template structure consulted

#### **Content Quality Validation**:
- [ ] Observations contain actionable information
- [ ] Context sufficient for future reference
- [ ] Cross-session continuity maintained
- [ ] No sensitive information included

#### **Metadata Validation**:
- [ ] Profile correctly identified
- [ ] Tags properly categorized
- [ ] Paths correctly formatted
- [ ] Timestamps accurate

### Post-Creation Validation:

#### **Integration Validation**:
- [ ] Entity properly stored in memory graph
- [ ] Relationships to behavioral framework entities maintained
- [ ] Cross-session accessibility confirmed
- [ ] Search/retrieval functionality verified

## Error Handling Procedures

### Template Access Failures:
1. **Missing Template File**:
   - Use canonical format from protocol
   - Add observation: "template_status: missing, used canonical format"
   - Continue with entity creation
   - Flag for template system improvement

2. **Template Format Errors**:
   - Fallback to previous known good template
   - Add observation: "template_status: corrupted, used fallback"
   - Document error for system maintenance

### Memory System Failures:
1. **Entity Creation Failure**:
   - Retry with simplified observation set
   - Log error details for investigation
   - Notify user of documentation limitation
   - Create local backup if possible

2. **Memory Graph Corruption**:
   - Abort entity creation to prevent further corruption
   - Alert user to memory system issue
   - Recommend memory system backup/recovery

## Cross-Session Continuity Protocols

### Session Initialization:
1. **Memory Graph Access**: Always execute `memory:read_graph` on session start
2. **Context Recovery**: Identify relevant existing entities for current session
3. **Profile Activation**: Load appropriate behavioral framework based on task context
4. **Previous Session Linkage**: Reference related previous sessions in new entities

### Session Documentation:
1. **Ongoing Documentation**: Update entities during session as significant progress occurs
2. **Session Conclusion**: Create appropriate documentation entities before session end
3. **Relationship Creation**: Link new entities to existing relevant entities
4. **Future Reference**: Ensure entities contain sufficient context for future sessions

## Behavioral Integration Instructions

### Trigger Phrase Recognition:
- Monitor for documentation trigger phrases throughout session
- Respond with appropriate entity creation workflow
- Confirm entity creation with user when triggered by phrase
- Maintain sensitivity to implicit documentation needs

### Institutional Memory Accumulation:
- Regularly review existing entities for pattern recognition
- Build upon previous insights and learnings
- Reference previous similar sessions in new documentation
- Evolve methodology based on accumulated experience

### User Preference Learning:
- Track user preferences for documentation frequency and detail
- Adapt entity creation patterns to user collaboration style
- Remember user-specific terminology and context preferences
- Evolve documentation protocol based on user feedback

## Protocol Compliance Monitoring

### Real-Time Compliance Checks:
- Validate entity structure before creation
- Confirm tag schema adherence
- Check naming convention compliance
- Verify template consultation completion

### Session-Level Compliance Review:
- Assess documentation completeness for session scope
- Review entity quality and cross-session value
- Identify protocol deviation patterns
- Generate compliance improvement recommendations

### System-Level Protocol Evolution:
- Track protocol effectiveness across multiple sessions
- Identify common failure patterns or inefficiencies
- Evolve protocol based on real-world usage patterns
- Maintain protocol version control for systematic improvement

---

## Implementation Notes

### Integration with Existing Framework:
- This protocol coexists with behavioral framework entities
- Does NOT replace existing framework methodology
- Adds systematic documentation layer to existing system
- Maintains backward compatibility with current memory structures

### Performance Considerations:
- Entity creation should not significantly impact session responsiveness
- Template consultation should cache results for session reuse
- Memory graph operations should be batched when possible
- Error handling should fail gracefully without blocking user work

### Security and Privacy:
- Never include sensitive user information in entities
- Validate observation content for privacy compliance
- Ensure entity relationships don't expose private context
- Maintain appropriate access controls for memory persistence

---

**Protocol Status**: Draft v1.0 - Ready for CLAUDE.md Integration
**Next Steps**: Embed in behavioral framework templates for automatic Claude Code inheritance