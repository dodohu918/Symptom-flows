# Symptom Flows

*A library of conversational flows for a medical symptom-checker chatbot.*

This repository holds the decision trees that guide patients from symptom description to appropriate clinical resources. Each flow is written in Traditional Chinese and contains prompts, options, and branching logic.

---

## Repository Layout

- **`flow_base.json`** – shared nodes for greeting the user, collecting location/age, and offering to find nearby clinics.
- **`flow_*symptom.json`** – individual symptom flows (over 50) covering topics like abdominal pain, cough, eye pain, and more.
- **`flow text/`** – source spreadsheets and notebooks used while creating the flows.
- **`flow_prompt.txt`** – instructions used to generate the JSON structure.

## JSON Field Reference

| Field | Description |
|------|-------------|
| `No` | Identifier for referencing a node |
| `question` | Chatbot prompt shown to the user |
| `type` | `yes_no`, `multiple_choice`, `open-ended`, `function`, or `end` |
| `next` / `nextIfYes` / `nextIfNo` | Links to subsequent nodes |
| `meta` | Optional data (e.g., recommended specialty) |

When a flow reaches a recommendation node, users can request to find a clinic. The `find_clinic` node in `flow_base.json` then helps locate clinics by geographic region.

## Intended Use

These flows form the logic for a symptom-checker chatbot that guides patients toward appropriate medical resources. The content is informational only and **not** a substitute for professional medical advice.

### Example

A simplified excerpt from `flow_base.json`:

```json
"greeting": {
  "No": "0_1",
  "question": "您好！我在這裡幫助您找到合適的診所。請問您的主要症狀是什麼？",
  "type": "open-ended",
  "next": "classify_symptom"
}
```

---

## License

[Add your license information or usage restrictions here.]
