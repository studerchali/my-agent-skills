---
name: notion-idea-expander
description: Activate to expand conversations ideas contexts or existing Notion pages into rich educational Notion pages that teach concepts and provide practical actionable learnings examples exercises and takeaways. Automatically creates the page under Personal Home / Conversaciones section for organized archiving in this workspace. Uses Notion integrations (search, fetch, create) to build structured knowledge from chat or pages. Triggers include: "#Exp" (new command), expand this into a Notion page lesson guide, create learning resource from our chat, turn idea into practical Notion page, read Notion page and elaborate educationally.
---

# Notion Idea Expander

## Purpose
This skill transforms raw ideas from conversations, chat context, or existing Notion pages into polished, structured educational Notion pages. The goal is deep understanding + immediate practical application.

**Special behavior for this workspace:** Every educational page created is automatically placed as a child page inside **Personal Home > Conversaciones**. This creates a clean, organized archive of all expanded conversations and ideas.

It turns SuperGrok's reasoning power into persistent, teachable knowledge stored in your Notion workspace.

## When to Use This Skill
Use whenever the user wants to:
- Expand a conversation or specific ideas into a learning resource
- Turn chat context into a structured lesson or guide
- Read an existing Notion page and elaborate it into a more complete educational version
- Create practical, actionable knowledge pages from abstract concepts or discussions
- Build or grow a personal knowledge base (especially inside the "Conversaciones" section)

Common user phrases: "#Exp", "expande esto en una página de Notion", "crea una página educativa a partir de nuestra conversación", "lee esta página de Notion y desarróllala", "convierte estas ideas en algo práctico para aprender", "haz una guía de aprendizaje sobre esto", "guarda esto en Conversaciones".

## Step-by-Step Workflow (Follow Strictly)

### 1. Identify and Read the Source Material
- **Notion page provided** (URL, title, or topic): 
  1. Call `notion___notion-search` with a precise query describing the page or topic.
  2. From results, extract the best matching `id`.
  3. Call `notion___notion-fetch` with that `id` (add `include_discussions: true` if comments/discussions matter).
- **Current conversation or "our chat" / "esta conversación"**:
  - Summarize the key ideas, questions, insights, examples, and context directly from the messages in the current conversation history.
  - Focus on the most relevant or recent parts if the chat is long. Do not hallucinate or add external knowledge unless explicitly extending.
- If user says "lee la conversación" or similar: Treat the full provided context as the source.

Clarify with the user if the goal is unclear: "¿Qué resultado o habilidades prácticas específicas quieres que tenga esta página?"

### 2. Analyze and Extract Learning Value
- Break down the source into:
  - Core concepts and ideas
  - Underlying contexts or problems being solved
  - Any examples, questions, or pain points mentioned
  - Potential for practical application
- Decide the learning objective: What should the reader be able to *understand* and *do* after reading the new page?

### 3. Design the Educational Page (Use This Structure)
Create content that **teaches** and enables **practical learning**. Always include these sections (adapt names to the topic and language):

- **Title** — Benefit-driven and specific
- **Introducción / Hook** — Why this matters + what the reader will gain
- **Conceptos Clave** — Clear explanations of main ideas
- **Ejemplos Prácticos y Aplicaciones** — 2–4 concrete scenarios
- **Guía Paso a Paso** (when applicable)
- **Ejercicios y Preguntas de Reflexión** — 3–5 hands-on tasks
- **Errores Comunes y Consejos Avanzados**
- **Plan de Acción** — Checklist of next steps
- **Resumen de Aprendizajes Clave**
- **Exploración Adicional**

### 4. Create the Page in Notion — Specific Workspace Structure
Always create the educational page as a **direct child** of the page **"Conversaciones"** which lives inside **"Personal Home"**.

1. Search for the "Conversaciones" page.
2. Use that ID as the parent.
3. Call `notion___notion-create-pages` with the prepared content.

After creation, share the full path and URL with the user.

### 5. Connect and Iterate
- Offer next steps: add more content, create linked pages, move it elsewhere, etc.

## Language & Quality Standards
- Create all page content in the **same language** as the user's request (Spanish for this conversation).
- Prioritize practicality.
- Keep tone encouraging and empowering.

This skill turns fleeting conversations into lasting, teachable knowledge assets inside **Personal Home > Conversaciones**.
