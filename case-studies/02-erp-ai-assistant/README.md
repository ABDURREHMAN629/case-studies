# ERP Assistant: ask the system by text or voice

**Part of:** [Textile Mill ERP](../01-textile-mill-erp/README.md) · **Status:** live · **Role:** designed and built alone

[← All case studies](../../README.md)

![How the assistant works](../../media/diagrams/erp-assistant.svg)

## The problem

A factory system has dozens of screens and reports. Most staff use two or three of them and get lost in the rest. Simple questions like *"how much of this lot is left to print?"* or *"where is this order?"* turn into phone calls to the one person who knows the system.

## What I built

An assistant inside the ERP. Staff type or speak a question in plain words. The assistant works out what was asked, checks what that person is allowed to see, and then gives the best answer:

- **a report**, the same one the screens use, so its number always matches
- **an explanation** of a screen or a field
- **a form opened with the values already filled in**, for a person to check and save

## Design choices that matter to a business

| Choice | Why |
|---|---|
| Uses the asker's **own login** | It can never show more than that user could open themselves |
| **Never writes** to the database | A person always presses Save, so the assistant cannot corrupt data |
| Offers options when unsure | A wrong guess becomes a wrong decision on the floor |
| Runs **fully on the factory server** | Company data never goes to an outside AI service, and it works when the internet is down |
| Shows the words it heard | With voice input, a mishearing is visible before it becomes the wrong report |
| Ready for an LLM | A larger language model can be added later if the hardware allows |

## Technology

`Node.js` `Custom NLU engine` `Web Speech / voice input` `Permission-aware tools`

---

*There is no demo video because the assistant only runs against the client's live data.*
