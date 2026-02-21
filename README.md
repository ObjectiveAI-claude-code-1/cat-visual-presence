# cat-visual-presence

## Overview

`cat-visual-presence` is a scalar function that answers a deceptively simple question about a photograph: *is the cat truly, visually here?*

It takes a single image as input and returns a score between **0** and **1** reflecting how proportionally present the cat is within the frame. A high score means the cat dominates the visual space in a way that feels generous, complete, and purposeful. A low score means the cat is diminished — either too small to matter, too fragmented to fully appreciate, or too carelessly placed to feel like the subject.

This is not a detection function. It does not ask *whether* a cat exists in the image. It asks how powerfully the cat occupies the frame — the difference between a photograph *of* a cat and a photograph that merely *contains* one.

## Input

The function accepts a single required field:

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `image` | `image` | Yes | The photograph to evaluate. Should contain at least one cat. |

## Output

A scalar score in the range **[0, 1]**:

| Score Range | Meaning |
|-------------|---------|
| **0.8 – 1.0** | The cat is the undeniable subject: large, fully visible, and deliberately framed. |
| **0.5 – 0.8** | The cat is present but with some compromise — moderate size, minor clipping, or slightly careless placement. |
| **0.2 – 0.5** | The cat is noticeable but diminished — small in the frame, partially cropped, or awkwardly positioned. |
| **0.0 – 0.2** | The cat is a minor element — tiny, severely clipped, or incidentally placed in the scene. |

## What It Evaluates

The function evaluates three distinct qualities, each capturing a different dimension of visual presence. Only when all three are satisfied does a photograph achieve the highest score.

### 1. Scale

How much of the frame does the cat physically occupy? A cat that fills a generous share of the image feels like the subject — it commands the viewer's attention and anchors the composition. A cat that occupies only a sliver of the frame, no matter how sharp or well-lit, reads as a footnote. This quality rewards images where the cat's size makes it the undeniable reason the photograph exists.

- **High score:** The cat fills a generous portion of the frame and dominates the visual space.
- **Mid score:** The cat is noticeable but shares attention with other elements in the scene.
- **Low score:** The cat is small, distant, and easily overlooked.

### 2. Completeness

Is the cat's full body contained within the frame? This quality exists in tension with scale — it is easy to make a cat large by zooming in until it overflows the edges, but a cat whose paws are sliced off or whose ears are cropped feels interrupted, not present. Completeness rewards images where the entire cat is visible from nose to tail, and penalizes those where the subject spills beyond the frame boundaries.

- **High score:** The cat's entire body is fully visible — head, body, legs, paws, and tail are all within the frame.
- **Mid score:** Most of the cat is visible, but a small part is clipped by an edge.
- **Low score:** A significant portion of the cat is cut off, leaving it feeling cropped and incomplete.

### 3. Intentionality

Does the cat's size and placement feel deliberate? This is the most subtle quality, but it is what separates a snapshot from a portrait. A cat that is well-scaled and comfortably contained, with natural margins that neither crowd nor isolate it, feels like it was framed on purpose. A cat that is jammed against an edge or floating in a vast ocean of empty background feels accidental.

- **High score:** The cat is well-positioned with comfortable margins; the composition feels deliberate and composed.
- **Mid score:** The cat appears to be the intended subject, but the framing is somewhat careless or unbalanced.
- **Low score:** The cat feels accidental — awkwardly placed, crammed against an edge, or lost in empty space.

## Use Cases

- **Photo curation:** Filter and rank cat photographs by how prominently the cat features as the subject, surfacing images where the cat is front and center.
- **Upload quality signals:** Score incoming images on platforms that celebrate cats, ensuring featured content showcases cats as true subjects rather than background elements.
- **Automated cropping guidance:** Provide feedback to cropping algorithms about whether a frame has achieved the right balance between subject scale and containment.
- **Evaluation pipelines:** Use as one component in a multi-function assessment of cat photograph quality, alongside other signals like sharpness, lighting, or expression.

## Scoring Philosophy

The function's scoring is built on a key insight: visual presence is not simply about size. A cat that is enormous but cropped is incomplete. A cat that is whole but tiny is insignificant. A cat that is large and complete but awkwardly placed feels like an accident. The ideal photograph — and the highest score — emerges only when scale, completeness, and intentionality converge: a cat that is undeniably, generously, and wholly *there*.
