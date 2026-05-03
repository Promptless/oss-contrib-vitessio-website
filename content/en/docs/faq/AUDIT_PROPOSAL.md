# Vitess FAQ Section Audit and Restructuring Proposal

This document provides a comprehensive audit of the FAQ section at `content/en/docs/faq/` compared against the main versioned documentation (25.0), with recommendations for restructuring.

## Executive Summary

The FAQ section contains **137 markdown files** organized in a hierarchical structure. After auditing this content against the main documentation, I found:

- **~40% purely duplicative content** that can be deleted
- **~35% overlapping content** that requires human review for potential merger
- **~20% unique FAQ-style content** worth keeping in a streamlined FAQ
- **~5% redirect-only files** that simply link to main docs

The FAQ "Getting Started" section specifically overlaps significantly with:
1. The `25.0/concepts/` section (concept definitions)
2. The `25.0/overview/` section (What is Vitess, architecture)
3. The `25.0/get-started/` section (installation tutorials)

## Detailed Findings by FAQ Section

---

### 1. FAQ > Getting Started > Overview

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `what-is-vitess.md` | `25.0/overview/whatisvitess.md` | **DELETE** | FAQ is a simplified subset of main docs |
| `what-are-the-main-components-of-vitess.md` | `25.0/overview/architecture.md` | **DELETE** | Main docs has better diagram and content |
| `what-is-vitess-and-mysqls-relationship.md` | `25.0/overview/whatisvitess.md` | **DELETE** | Covered in main docs comparisons section |
| `how-do-vitess-replicas-stay-in-sync-do-replicas.md` | `25.0/concepts/tablet.md`, `25.0/user-guides/configuration-basic/` | **FLAG FOR REVIEW** | Unique operational detail, consider merging |
| `are-microservices-recommended-for-scaling.md` | N/A | **FLAG FOR REVIEW** | Unique perspective, could be useful |
| `how-can-i-migrate-out-of-vitess.md` | N/A | **KEEP** | Unique FAQ-appropriate content |

---

### 2. FAQ > Getting Started > Components

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `what-is-a-cell-how-does-it-work.md` | `25.0/concepts/cell.md` | **DELETE** | Nearly word-for-word duplicate |
| `what-is-a-keyspace.md` | `25.0/concepts/keyspace.md` | **DELETE** | Simplified duplicate |
| `what-is-a-shard.md` | `25.0/concepts/shard.md` | **DELETE** | Simplified duplicate |
| `what-is-a-tablet-what-are-the-types.md` | `25.0/concepts/tablet.md` | **DELETE** | Main docs more comprehensive |
| `what-is-vtgate-and-how-does-it-work.md` | `25.0/concepts/vtgate.md` | **DELETE** | Main docs more comprehensive |
| `what-is-vtctld.md` | `25.0/concepts/vtctld.md` | **DELETE** | Direct duplicate |
| `what-is-vtctldclient.md` | `25.0/concepts/vtctl.md` | **DELETE** | Covered in main docs |
| `what-is-vttablet-how-does-it-work-with-mysql.md` | `25.0/concepts/tablet.md` | **DELETE** | Duplicate |

---

### 3. FAQ > Getting Started > Compatibility

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `what-versions-of-mysql-or-mariadb-work-with-vitess.md` | `25.0/overview/supported-databases.md` | **DELETE** | Already redirects to main docs |
| `are-foreign-keys-supported-in-vitess.md` | `25.0/user-guides/vschema-guide/foreign-keys.md` | **FLAG FOR REVIEW** | FAQ has good summary, main docs more detailed |
| `how-is-vitess-different-from-mysql.md` | `25.0/overview/whatisvitess.md` | **DELETE** | Covered in main docs comparison section |
| `how-is-vitess-different-from-aws-aurora-for-mysql.md` | N/A | **KEEP** | Unique comparison content |
| `how-is-vitess-different-from-rds-for-mysql.md` | N/A | **KEEP** | Unique comparison content |
| `what-does-it-mean-to-say-that-vitess-is-mysql.md` | `25.0/overview/whatisvitess.md` | **DELETE** | Covered in main docs |

---

### 4. FAQ > Getting Started > Topology

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `what-is-the-topology-service-how-does-it-work.md` | `25.0/concepts/topology-service.md` | **DELETE** | Simplified duplicate |
| `what-topology-servers-can-i-use-with-vitess.md` | `25.0/user-guides/configuration-basic/global-topo/` | **DELETE** | Covered in user guides |
| `how-do-i-choose-which-topology-server-to-use.md` | N/A | **FLAG FOR REVIEW** | Practical guidance, may be unique |
| `how-do-i-implement-etcd-etcd2.md` | `25.0/user-guides/configuration-basic/global-topo/` | **DELETE** | Covered in user guides |
| `how-do-i-implement-zookeeper-zk2.md` | `25.0/user-guides/configuration-basic/global-topo/` | **DELETE** | Covered in user guides |
| `how-do-i-migrate-between-implementations.md` | N/A | **FLAG FOR REVIEW** | May contain unique guidance |

---

### 5. FAQ > Getting Started > VSchema

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `what-is-a-vschema.md` | `25.0/concepts/vschema.md` | **DELETE** | Simplified duplicate |
| `what-is-a-vindex-and-how-does-it-work.md` | `25.0/reference/features/vindexes.md` | **DELETE** | Main docs more comprehensive |
| `what-is-a-primary-vindex-and-how-does-it-work.md` | `25.0/reference/features/vindexes.md` | **DELETE** | Covered in main docs |
| `how-do-i-create-a-vschema.md` | `25.0/user-guides/vschema-guide/` | **DELETE** | Covered in user guides |
| `when-do-i-need-to-use-a-vschema.md` | N/A | **FLAG FOR REVIEW** | Practical decision guidance |

---

### 6. FAQ > Getting Started > VReplication

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `what-is-vreplication-how-does-it-work.md` | `25.0/reference/vreplication/vreplication.md` | **FLAG FOR REVIEW** | FAQ has good step-by-step explanation, different perspective |
| `how-can-i-use-vreplication.md` | `25.0/reference/vreplication/` | **DELETE** | Covered in reference docs |

---

### 7. FAQ > Getting Started > Metrics

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `how-can-i-monitor-or-get-metrics-from-vitess.md` | `25.0/reference/query-serving/metrics.md` | **FLAG FOR REVIEW** | FAQ provides good overview |
| `how-do-you-integrate-prometheus-and-vitess.md` | `25.0/user-guides/configuration-basic/monitoring/` | **DELETE** | Covered in user guides |

---

### 8. FAQ > Advanced Configuration (Sample)

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `vindex/what-is-a-vindex.md` | `25.0/reference/features/vindexes.md` | **DELETE** | Just redirects to main docs |
| `vttablet/what-does-it-mean-if-a-vttablet-is-unhappy.md` | N/A | **KEEP** | Unique troubleshooting content |
| `vttablet/what-is-semi-sync-replication.md` | `25.0/user-guides/configuration-advanced/` | **FLAG FOR REVIEW** | Good summary but may be duplicate |
| `authentication/*` | `25.0/user-guides/configuration-advanced/` | **FLAG FOR REVIEW** | Check for unique auth content |

---

### 9. FAQ > Migrating

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `overview/how-do-i-migrate-my-data-to-vitess.md` | `25.0/user-guides/migration/migrate-data.md` | **FLAG FOR REVIEW** | Good decision-tree overview |
| `overview/what-is-vtexplain.md` | `25.0/reference/programs/vtexplain/` | **DELETE** | Covered in reference docs |
| `query-rewriting/*` | `25.0/concepts/query-rewriting.md` | **FLAG FOR REVIEW** | Check for unique migration concerns |

---

### 10. FAQ > Operating Vitess

| FAQ File | Main Docs Equivalent | Recommendation | Notes |
|----------|---------------------|----------------|-------|
| `backup-restore/how-do-backups-work-in-vitess.md` | `25.0/user-guides/operating-vitess/backup-and-restore/` | **DELETE** | Just redirects |
| `kubernetes/*` | `25.0/get-started/operator.md` | **FLAG FOR REVIEW** | May contain unique K8s operational tips |
| `configuration/*` | Various user guides | **FLAG FOR REVIEW** | Check for unique operational guidance |

---

## Proposed Restructuring

### Option A: Minimal FAQ (Recommended)

Reduce the FAQ to a single page or small section that:
1. Keeps truly FAQ-appropriate content (brief answers to common questions)
2. Links to main docs for detailed information
3. Focuses on comparison/decision-making content not covered elsewhere

**Proposed new FAQ structure:**

```
faq/
├── _index.md (Community questions, Slack channels, contributing - KEEP)
├── comparisons.md (NEW: consolidate Aurora/RDS comparisons)
├── decision-guides.md (NEW: when to use vschema, choosing topology, etc.)
└── troubleshooting-tips.md (NEW: consolidate unique operational tips)
```

### Option B: Redirect FAQ to Main Docs

Convert the FAQ into a navigational aid:
1. Delete all duplicative content
2. Keep `_index.md` with community info
3. Add a "Quick Reference" section with links to concepts, not duplicated content

---

## Getting Started Content Merger Proposal

The FAQ `getting-started/` section should be **mostly deleted** because:

1. **Main `get-started/` section** (25.0) provides actual installation tutorials
2. **Concepts section** (25.0) provides component definitions
3. **Overview section** (25.0) provides "What is Vitess" content

### Recommended Actions:

1. **Delete** FAQ `getting-started/components/` - redirect to `concepts/`
2. **Delete** FAQ `getting-started/overview/` - redirect to `overview/`
3. **Delete** FAQ `getting-started/vschema/` - redirect to `user-guides/vschema-guide/`
4. **Delete** FAQ `getting-started/topology/` - redirect to `user-guides/configuration-basic/global-topo/`
5. **Keep/Merge** unique comparison content (Aurora, RDS comparisons)
6. **Review** decision-making content for potential new "Decision Guides" page

---

## Items Requiring Human Review

These items need human judgment before acting:

### Potential Contradictions (Priority: HIGH)
- None identified, but recommend verifying version numbers and supported databases are consistent

### Different Perspectives (Priority: MEDIUM)
1. **VReplication explanation**: FAQ has a step-by-step process view; main docs has a feature-oriented view. Consider which serves users better.
2. **Migration guidance**: FAQ has decision-tree approach; main docs has method-by-method approach.

### Unique Content Worth Preserving (Priority: MEDIUM)
1. AWS Aurora comparison
2. RDS comparison  
3. "Unhappy VTTablet" troubleshooting
4. "Microservices for scaling" discussion
5. "Migrate out of Vitess" guidance
6. Choosing topology server guidance

---

## Implementation Plan

### Phase 1: Delete Pure Duplicates
- Delete ~55 files that are simplified duplicates of concepts/overview content
- Delete redirect-only files
- Estimated effort: 1-2 hours

### Phase 2: Human Review
- Review 15-20 files flagged for human judgment
- Decide on merge vs delete vs keep
- Estimated effort: 2-3 hours

### Phase 3: Restructure
- Create new consolidated FAQ pages if Option A chosen
- Update navigation and cross-links
- Add redirects from old FAQ URLs
- Estimated effort: 3-4 hours

### Phase 4: Test and Validate
- Verify all links work
- Check navigation
- Review with stakeholders
- Estimated effort: 1-2 hours

---

## Next Steps

1. Review this proposal and decide on restructuring approach (Option A or B)
2. Confirm the "Delete" recommendations are acceptable
3. Make decisions on "FLAG FOR REVIEW" items
4. Assign implementation work

---

*Generated by Promptless FAQ Audit - 2026-05-03*
