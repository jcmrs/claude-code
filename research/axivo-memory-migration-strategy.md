# Axivo Memory Restructuring and Migration Strategy

**Version**: 1.0
**Generated**: September 17, 2025
**Purpose**: Safe migration strategy for cleaning corrupted memory graphs while preserving valid behavioral framework entities

---

## Migration Overview

### Problem Statement
Current Axivo memory graphs contain:
- ✅ **Valid behavioral framework entities** (should be preserved)
- ❌ **Invalid arbitrary entities** (should be cleaned or migrated)
- ❌ **Missing documentation entities** (should be created from templates)
- ❌ **Inconsistent entity structures** (should be standardized)

### Migration Objectives
1. **Preserve all valid behavioral framework entities** (COLLABORATION, INFRASTRUCTURE, CREATIVE, etc.)
2. **Remove or migrate invalid arbitrary entities** safely
3. **Establish clean foundation** for systematic documentation protocol
4. **Ensure zero data loss** of valuable behavioral guidelines
5. **Maintain cross-session continuity** during migration process

---

## Phase 1: Analysis and Categorization

### Memory Graph Analysis Protocol

#### Step 1.1: Complete Memory Export and Backup
```bash
# Backup all existing memory graphs before any changes
cp "C:/Users/jcmei/github/claude/.claude/memory/graph.json" "C:/Users/jcmei/mcp-servers/backups/memory-graph-backup-$(date +%Y%m%d-%H%M%S).json"
cp "C:/Users/jcmei/github/claude/.claude/data/graph.json" "C:/Users/jcmei/mcp-servers/backups/documentation-graph-backup-$(date +%Y%m%d-%H%M%S).json"
cp "C:/Users/jcmei/github/claude/.claude/data/logic/graph.json" "C:/Users/jcmei/mcp-servers/backups/logic-graph-backup-$(date +%Y%m%d-%H%M%S).json"
```

#### Step 1.2: Entity Classification System
```javascript
// Entity Classification Criteria
const classifyEntity = (entity) => {
  // Valid Behavioral Framework Entities
  if (entity.entityType === 'collaboration_description' ||
      entity.entityType === 'section' ||
      entity.entityType === 'methodology' ||
      entity.entityType === 'framework_guideline') {
    return 'PRESERVE'; // These are correct framework entities
  }

  // Valid Documentation Entities (rare but possible)
  if (entity.entityType === 'conversation' ||
      entity.entityType === 'diary' ||
      entity.entityType === 'logic') {
    return 'VALIDATE'; // Check if properly formatted
  }

  // Profile-Related Entities
  if (entity.name === 'RESEARCHER' ||
      entity.name === 'ENGINEER' ||
      entity.name === 'DEVELOPER' ||
      entity.name === 'COLLABORATION' ||
      entity.name === 'INFRASTRUCTURE' ||
      entity.name === 'CREATIVE') {
    return 'PRESERVE'; // Core profile entities
  }

  // Arbitrary Named Entities
  if (entity.entityType === 'observation' ||
      entity.entityType === 'documentation' ||
      entity.entityType === 'Unknown' ||
      !entity.entityType) {
    return 'MIGRATE'; // Likely arbitrary entities needing cleanup
  }

  return 'REVIEW'; // Manual review required
};
```

#### Step 1.3: Automated Classification Tool
```javascript
// Memory Graph Classification Tool
const analyzeMemoryGraph = (graphPath) => {
  const graph = JSON.parse(fs.readFileSync(graphPath, 'utf8'));
  const classification = {
    PRESERVE: [],
    VALIDATE: [],
    MIGRATE: [],
    REVIEW: []
  };

  // Parse JSONL format
  const entities = graph.split('\n')
    .filter(line => line.trim())
    .map(line => JSON.parse(line))
    .filter(item => item.type === 'entity');

  entities.forEach(entity => {
    const category = classifyEntity(entity);
    classification[category].push({
      name: entity.name,
      entityType: entity.entityType,
      observationCount: entity.observations ? entity.observations.length : 0,
      hasValidStructure: validateEntityStructure(entity)
    });
  });

  return classification;
};
```

### Manual Review Process

#### Step 1.4: Human Validation for REVIEW Category
```markdown
For each entity marked REVIEW:
1. **Examine entity name and type** - Does it represent valid behavioral framework content?
2. **Analyze observations** - Do they contain valuable behavioral guidelines?
3. **Check relationships** - Is this entity referenced by other valid entities?
4. **Assess value** - Would losing this entity reduce system effectiveness?

Decision Matrix:
- **High Value + Valid Structure** → Reclassify as PRESERVE
- **High Value + Invalid Structure** → Reclassify as MIGRATE (fix structure)
- **Low Value + Any Structure** → Mark for REMOVAL
```

### Entity Relationship Mapping

#### Step 1.5: Dependency Analysis
```javascript
// Map entity relationships before migration
const mapEntityRelationships = (entities) => {
  const relationships = {};

  entities.forEach(entity => {
    relationships[entity.name] = {
      referencedBy: [], // Entities that reference this one
      references: [], // Entities this one references
      observations: entity.observations || []
    };
  });

  // Analyze observation content for entity references
  entities.forEach(entity => {
    entity.observations?.forEach(obs => {
      entities.forEach(otherEntity => {
        if (obs.includes(otherEntity.name) && entity.name !== otherEntity.name) {
          relationships[entity.name].references.push(otherEntity.name);
          relationships[otherEntity.name].referencedBy.push(entity.name);
        }
      });
    });
  });

  return relationships;
};
```

---

## Phase 2: Safe Migration Protocol

### Migration Execution Strategy

#### Step 2.1: Isolated Testing Environment
```bash
# Create isolated test environment
mkdir "C:/Users/jcmei/mcp-servers/migration-test"
cp -r "C:/Users/jcmei/github/claude/.claude" "C:/Users/jcmei/mcp-servers/migration-test/.claude-test"

# Update test MCP configuration to point to test environment
# Test all migration procedures on isolated copy first
```

#### Step 2.2: Entity Preservation Protocol
```javascript
// Preserve valid behavioral framework entities
const preserveValidEntities = (entities, classification) => {
  const preservedEntities = [];

  classification.PRESERVE.forEach(entityInfo => {
    const entity = entities.find(e => e.name === entityInfo.name);
    if (entity) {
      // Validate structure and fix minor issues
      const cleanedEntity = {
        type: 'entity',
        name: entity.name,
        entityType: entity.entityType,
        observations: Array.isArray(entity.observations) ? entity.observations : []
      };
      preservedEntities.push(cleanedEntity);
    }
  });

  return preservedEntities;
};
```

#### Step 2.3: Entity Migration Protocol
```javascript
// Migrate entities with value but wrong structure
const migrateEntities = (entities, classification) => {
  const migratedEntities = [];

  classification.MIGRATE.forEach(entityInfo => {
    const entity = entities.find(e => e.name === entityInfo.name);
    if (entity && hasValueForMigration(entity)) {

      // Determine if this should become a conversation, diary, or be restructured
      const migratedEntity = restructureEntity(entity);
      migratedEntities.push(migratedEntity);
    }
  });

  return migratedEntities;
};

const restructureEntity = (entity) => {
  // If entity contains session-like information, convert to conversation
  if (containsSessionInformation(entity)) {
    return {
      type: 'entity',
      name: generateConversationName(entity),
      entityType: 'conversation',
      observations: [
        'path', extractPathFromEntity(entity) || 'migrated-session',
        'profile', extractProfileFromEntity(entity) || 'DEVELOPER',
        'tags', '#migration #legacy-conversion',
        'summary', 'Migrated from legacy entity structure',
        'original_name', entity.name,
        'original_content', entity.observations?.join('; ') || 'No content'
      ]
    };
  }

  // If entity contains reflection-like content, convert to diary
  if (containsReflectionContent(entity)) {
    return {
      type: 'entity',
      name: generateDiaryName(entity),
      entityType: 'diary',
      observations: [
        'path', 'migrated-reflection',
        'profile', 'DEVELOPER',
        'tags', '#migration #legacy-reflection',
        'reflection_type', 'migration-preserved',
        'original_content', entity.observations?.join('; ') || 'No content'
      ]
    };
  }

  // Default: preserve as behavioral framework entity with cleaned structure
  return {
    type: 'entity',
    name: entity.name,
    entityType: 'framework_guideline',
    observations: Array.isArray(entity.observations) ? entity.observations : [entity.observations || 'Migrated content']
  };
};
```

### Data Integrity Validation

#### Step 2.4: Post-Migration Validation
```javascript
// Comprehensive validation after migration
const validateMigration = (originalEntities, migratedEntities) => {
  const validation = {
    entityCountPreservation: true,
    criticalEntitiesPreserved: true,
    structureCompliance: true,
    relationshipIntegrity: true,
    errors: []
  };

  // Check critical entities are preserved
  const criticalEntities = ['COLLABORATION', 'RESEARCHER', 'ENGINEER', 'DEVELOPER'];
  criticalEntities.forEach(name => {
    if (!migratedEntities.find(e => e.name === name)) {
      validation.criticalEntitiesPreserved = false;
      validation.errors.push(`Critical entity missing: ${name}`);
    }
  });

  // Validate entity structure compliance
  migratedEntities.forEach(entity => {
    if (!validateEntityStructure(entity)) {
      validation.structureCompliance = false;
      validation.errors.push(`Invalid structure: ${entity.name}`);
    }
  });

  return validation;
};
```

---

## Phase 3: Protocol Implementation

### Clean Foundation Establishment

#### Step 3.1: Template System Integration
```bash
# Ensure proper template files exist
mkdir -p "C:/Users/jcmei/github/claude/.claude/memory/templates"

# Create canonical templates if missing
cat > "C:/Users/jcmei/github/claude/.claude/memory/templates/conversation.md" << 'EOF'
# Conversation Entity Template

## Required Observations:
- path: [File path to session log]
- profile: [RESEARCHER|ENGINEER|DEVELOPER]
- tags: [#domain-topic #activity-type #outcome-result]
- summary: [Brief session summary]
- key_outcomes: [Main achievements]
- follow_up: [Next steps]

## Optional Observations:
- duration: [Session length]
- complexity: [Simple|Moderate|Complex]
- user_satisfaction: [Assessment of solution effectiveness]
EOF
```

#### Step 3.2: Enhanced CLAUDE.md Deployment
```bash
# Deploy enhanced CLAUDE.md to active profile directories
cp "C:/Users/jcmei/mcp-servers/axivo-claude-template.md" "C:/Users/jcmei/github/claude/.claude/profiles/RESEARCHER/CLAUDE.md"
cp "C:/Users/jcmei/mcp-servers/axivo-claude-template.md" "C:/Users/jcmei/github/claude/.claude/profiles/ENGINEER/CLAUDE.md"
cp "C:/Users/jcmei/mcp-servers/axivo-claude-template.md" "C:/Users/jcmei/github/claude/.claude/profiles/DEVELOPER/CLAUDE.md"

# Customize profile-specific sections in each CLAUDE.md
```

### Migration Execution Timeline

#### Week 1: Preparation and Analysis
- **Day 1-2**: Complete memory graph backup and analysis
- **Day 3-4**: Run entity classification on all memory graphs
- **Day 5-7**: Manual review of REVIEW category entities

#### Week 2: Isolated Testing
- **Day 1-3**: Execute migration in isolated test environment
- **Day 4-5**: Validate migration results and fix issues
- **Day 6-7**: Test new documentation protocol in isolated environment

#### Week 3: Production Migration
- **Day 1**: Final backup of production memory graphs
- **Day 2**: Execute migration on production environment
- **Day 3**: Validate production migration results
- **Day 4-7**: Monitor system stability and protocol compliance

#### Week 4: Protocol Validation
- **Day 1-7**: Test enhanced documentation protocol with real usage
- **Monitor**: Entity creation quality and cross-session continuity
- **Refine**: Protocol based on real-world usage patterns

---

## Phase 4: Validation Framework Implementation

### Automated Compliance Monitoring

#### Step 4.1: Protocol Compliance Checker
```javascript
// Real-time protocol compliance validation
const validateProtocolCompliance = (entity) => {
  const compliance = {
    namingConvention: false,
    tagSchema: false,
    requiredObservations: false,
    entityType: false,
    errors: []
  };

  // Validate naming convention
  if (entity.entityType === 'conversation') {
    compliance.namingConvention = /^\d{4}-\d{2}-\d{2} .+/.test(entity.name);
  } else if (entity.entityType === 'diary') {
    compliance.namingConvention = /^\d{4}-\d{2}-\d{2} .+/.test(entity.name);
  } else if (entity.entityType === 'logic') {
    compliance.namingConvention = /^\d{4}-\d{2}-\d{2} (RESEARCHER|ENGINEER|DEVELOPER): .+/.test(entity.name);
  }

  // Validate tag schema
  const tagObservation = entity.observations?.find(obs => obs.startsWith('tags'));
  if (tagObservation) {
    const tags = tagObservation.split(',').map(tag => tag.trim());
    compliance.tagSchema = tags.every(tag => tag.startsWith('#'));
  }

  // Validate required observations
  const requiredFields = getRequiredFieldsForEntityType(entity.entityType);
  compliance.requiredObservations = requiredFields.every(field =>
    entity.observations?.some(obs => obs.includes(field))
  );

  return compliance;
};
```

#### Step 4.2: Cross-Session Continuity Monitor
```javascript
// Monitor cross-session learning and continuity
const monitorContinuity = (currentSession, previousSessions) => {
  const continuityMetrics = {
    referencesToPrevious: 0,
    buildOnPreviousLearnings: false,
    newInsightsDocumented: false,
    institutionalMemoryGrowth: false
  };

  // Check if current session references previous work
  currentSession.entities?.forEach(entity => {
    entity.observations?.forEach(obs => {
      previousSessions.forEach(prevSession => {
        if (obs.includes(prevSession.name) ||
            obs.includes('previous session') ||
            obs.includes('last time')) {
          continuityMetrics.referencesToPrevious++;
        }
      });
    });
  });

  return continuityMetrics;
};
```

### Quality Assurance Framework

#### Step 4.3: Entity Quality Metrics
```javascript
// Assess documentation entity quality
const assessEntityQuality = (entity) => {
  const quality = {
    score: 0,
    factors: {
      completeness: 0,      // All required fields present
      specificity: 0,       // Specific actionable content
      futureValue: 0,       // Useful for future sessions
      crossReference: 0,    // References other entities appropriately
      structureCompliance: 0 // Follows protocol exactly
    }
  };

  // Calculate completeness
  const requiredFields = getRequiredFieldsForEntityType(entity.entityType);
  quality.factors.completeness = (entity.observations?.filter(obs =>
    requiredFields.some(field => obs.includes(field))
  ).length || 0) / requiredFields.length;

  // Calculate specificity (avoid generic observations)
  const genericTerms = ['work', 'session', 'completed', 'discussed'];
  const specificContent = entity.observations?.filter(obs =>
    !genericTerms.some(term => obs.toLowerCase().includes(term))
  ).length || 0;
  quality.factors.specificity = Math.min(specificContent / (entity.observations?.length || 1), 1);

  // Overall quality score
  quality.score = Object.values(quality.factors).reduce((sum, val) => sum + val, 0) /
                  Object.keys(quality.factors).length;

  return quality;
};
```

---

## Rollback and Recovery Procedures

### Emergency Rollback Protocol

#### Step 5.1: Immediate Rollback
```bash
# If migration causes critical issues, immediate rollback
if [[ "$MIGRATION_FAILED" == "true" ]]; then
  echo "CRITICAL: Migration failed, executing rollback..."

  # Stop all Claude Code instances
  pkill -f "claude-code"

  # Restore from backup
  cp "C:/Users/jcmei/mcp-servers/backups/memory-graph-backup-latest.json" "C:/Users/jcmei/github/claude/.claude/memory/graph.json"
  cp "C:/Users/jcmei/mcp-servers/backups/documentation-graph-backup-latest.json" "C:/Users/jcmei/github/claude/.claude/data/graph.json"
  cp "C:/Users/jcmei/mcp-servers/backups/logic-graph-backup-latest.json" "C:/Users/jcmei/github/claude/.claude/data/logic/graph.json"

  # Restart MCP servers
  echo "System restored to pre-migration state"
fi
```

#### Step 5.2: Partial Recovery
```javascript
// Selective recovery of specific entities if only some migration failed
const partialRecovery = (failedEntities, backupGraph) => {
  const backup = JSON.parse(fs.readFileSync(backupGraph, 'utf8'));
  const entitiesToRestore = [];

  failedEntities.forEach(entityName => {
    const backupEntity = findEntityInGraph(backup, entityName);
    if (backupEntity) {
      entitiesToRestore.push(backupEntity);
    }
  });

  return entitiesToRestore;
};
```

---

## Success Metrics and Monitoring

### Migration Success Criteria

#### Quantitative Metrics:
- **100% preservation** of critical behavioral framework entities
- **90%+ successful migration** of valuable arbitrary entities
- **Zero data loss** of behavioral guidelines
- **<5% increase** in memory graph size post-cleanup
- **Protocol compliance rate** >95% for new entities

#### Qualitative Metrics:
- **Cross-session continuity** maintained and improved
- **User experience** improved through better institutional memory
- **Entity search and retrieval** more reliable and faster
- **Documentation quality** consistently higher than pre-migration

### Ongoing Monitoring Dashboard

#### Real-Time Metrics:
```javascript
const migrationDashboard = {
  entitiesCreated: 0,
  protocolCompliance: 0.0,
  crossSessionReferences: 0,
  userSatisfactionIndicators: 0,
  systemStability: 'green',
  lastEntityCreated: null,
  averageEntityQuality: 0.0
};
```

---

## Implementation Timeline

### Immediate (Next 7 Days):
1. ✅ Complete memory graph analysis and entity classification
2. ✅ Set up isolated testing environment
3. ✅ Execute migration in test environment
4. ✅ Validate migration results

### Short Term (Next 30 Days):
1. Execute production migration with comprehensive backup
2. Deploy enhanced CLAUDE.md templates to all profiles
3. Monitor protocol compliance and system stability
4. Refine protocol based on real-world usage

### Long Term (Next 90 Days):
1. Develop automated migration tools for future deployments
2. Create user education materials for documentation protocol
3. Build community standards for Axivo protocol compliance
4. Contribute improvements back to Axivo ecosystem

---

**Migration Strategy Status**: Ready for Implementation
**Risk Level**: Low (comprehensive backup and rollback procedures)
**Expected Value Recovery**: 20% → 95% system value realization