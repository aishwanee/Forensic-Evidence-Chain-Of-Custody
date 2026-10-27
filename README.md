# Forensic-Evidence-Chain-Of-Custody-System
A database system that keeps digital evidence legally defensible by proving two things: the evidence was never altered, and every person who held it is accounted for at every moment.

The Problem

Digital evidence (hard drives, phones, USB drives, log files) is admissible in court only if investigators can prove its integrity and its custody history. In practice, chain of custody is often kept in spreadsheets or paper registers that can be edited, backdated or lost without anyone noticing. Nothing detects tampering or a handover to an unauthorised person, and one unexplained gap can make crucial evidence inadmissible.

The Solution

This system records every evidence item and every handover in a database. It:

Stores a SHA-256 hash of each item at collection and re-verifies it at every transfer and after every lab analysis
Writes every action to an append-only audit log in which each entry stores the hash of the previous entry, so any edit or deletion of history breaks the chain and is detected
Raises integrity alerts automatically when something suspicious happens

Objectives

Evidence registration: record each item against its case, including who collected it, when, and its SHA-256 hash.

Custody transfers: record every handover (from, to, when, why) and reject invalid ones.

Tamper detection: compare the current hash with the hash stored at collection.

Access control: an investigator can only receive evidence at or below their clearance level.

Tamper-evident audit trail: a hash-chained log in which altering any past entry is detectable.

Automatic alerts for:
Hash mismatches
Custody gaps
Unauthorised transfers
Edits to sealed evidence

Court-ready reporting: generate a full custody report for any case.

Why Hash-Chaining?

Because each log entry includes the hash of the entry before it, changing or removing any record invalidates every record that follows. This makes silent tampering with the history detectable, which is the property a court needs from a custody record.
