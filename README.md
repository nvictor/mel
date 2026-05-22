# Melodic Engineering Language (MEL)
**Version:** 1.1.0

MEL describes melodies as motifs, transformations, and phrase roles. It captures what a melody is doing, not exact performance detail.

It captures melodic function, motivic transformations, conversational structure, and scale-degree relationships. It does not specify absolute pitch, key, exact rhythm, harmony, instrumentation, or articulation.

## Syntax

```text
MEL ::= <MotifDef>+ <Phrase>
MotifDef ::= <Identifier> ":" "[" <Degrees> "]"
Identifier ::= <Letter> ["'"]*
Phrase ::= "[" <MotifInstance>+ "]"
MotifInstance ::= <Identifier> [<Transformation>+] [<Role>]
```

Example: `A : [1 b3 4] [A? A←!]`

Motif definitions come first. The phrase then names those motifs and marks how each one behaves.

Identifiers are letters with optional apostrophe suffixes. Uppercase is standard notation; lowercase is useful for live shorthand. `A' : [4 4 4 b3 1]` defines a named variant of `A`.

The apostrophe has two meanings depending on where it appears:

- `A'←<`: motif variant `A'`, then reverse and expand.
- `A←'`: motif `A`, then reverse and vary.

## Symbols

### Degrees

Degrees describe relative pitch.

- `1`..`7`: Diatonic scale degrees.
- `b` / `#`: Chromatic alterations.
- `↓` / `↑`: Octave displacement inside a degree list.

Unicode accidentals `♭` and `♯` may be used in display notation, but ASCII `b` and `#` are the canonical forms.

### Roles

- `?`: Question, call, opening, implication.
- `!`: Answer, response, resolution.
- `~`: Comment, reflection, or meta-statement.
- `=`: Reinforce, repetition, or confirmation.

Roles are phrase-function markers. Put them at the end of a motif instance: `A←!`, `A'<=`.

### Transformations

- `'`: Variation, a small melodic change.
- `←`: Reverse, or retrograde.
- `<`: Expansion, interval stretching.
- `>`: Contraction, interval shrinking.
- `↑` / `↓`: Octave transposition when used after a motif instance.

Transformations apply left to right. `A←'` means reverse, then vary.

## Rules

- Degrees are relative to an unstated tonal center.
- Named variants such as `A'` and `B'` are distinct motifs.
- Every motif instance must reference a defined motif identifier.
- Transformations apply only to the motif instance immediately before them.
- A motif instance has at most one phrase role, written at the end.
- A phrase is assumed to form one complete musical thought.
- MEL describes pitch contour and function, not duration.
- If a distinction requires exact rhythm, harmony, articulation, or instrumentation, it is outside the scope of MEL.

## Live Mode (Shorthand)

Live mode is for quick capture while listening.

- Use lowercase identifiers for quick motif names: `a`, `b`, `c`.
- Omit brackets in simple chains if the reading is unambiguous.
- Use ASCII accidentals while typing: `b3`, `#4`.
- Keep one role per motif instance.

Example: `a:1 b3 4  a? a←!` is equivalent to `A : [1 b3 4] [A? A←!]`.

## Examples

### Calls-Responses

```text
A  : [1 b3 4]
A← : [4 b3 1]

[A? A←!]
```

Songs:
* Chorus of "Hallelujah" (Leonard Cohen)
* Chorus of "It Is Well" (Bethel Music, Kristene DiMarco)
* Verse of "Way Maker" (Leeland)

```text
A  : [1 b2 3]
A← : [3 b2 1]

[A? A←!]
```

Songs:
* Verse of "Worthy" (CeCe Winans)

```text
A  : [1 2 3]
A← : [3 2 1]

[A? A←!]
```

Songs:
* Verse and guitar riffs of "45" (Shinedown)

### The Terminator Theme

"The Terminator Theme" (Brad Fiedel):

```text
A  : [1 2 b3]
B  : [2 b7↓ b3↓]
B' : [2 b7↓ 5 4]
B' : [2 b7↓ 4↓]
A← : [b3↓ 1↓]
A← : [b3↓ 2↓ 1↓]

[A? B! A? B'! A? B'! A←> A←=]
```

## Quick Reference

- `A : [1 b3 4]`: Define motif `A`.
- `A' : [4 4 4 b3 1]`: Define motif variant `A'`.
- `A?`: Motif `A` as a question.
- `A!`: Motif `A` as an answer.
- `A~`: Motif `A` as a comment.
- `A=`: Motif `A` as reinforcement.
- `A←`: Motif `A` reversed.
- `A'←<`: Motif variant `A'`, reversed and expanded.
- `A←'`: Motif `A`, reversed and varied.
- `A↑`: Motif `A` transposed up an octave.
- `5↓`: Scale degree 5 displaced down an octave.
