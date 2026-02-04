# MCP Agentic-Rag-Model

This project implements a production-grade Agentic RAG system built using:

Model Context Protocol (MCP)

Qdrant Vector Database

HuggingFace Embeddings (nomic-embed-text)

Custom Retrieval Tools (FAQ RAG + BrightData Web Search)

FastMCP Tool Server

It is designed as a fully modular, scalable retrieval layer for LLM agents, suitable for ML assistants, research agents, and intelligent helpdesk systems.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python)
![MCP](https://img.shields.io/badge/Powered%20By-MCP-orange)
![Qdrant](https://img.shields.io/badge/VectorDB-Qdrant-purple?logo=qdrant)
![HuggingFace](https://img.shields.io/badge/Embeddings-HuggingFace-yellow?logo=huggingface)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Status](https://img.shields.io/badge/Status-Active-success)

<svg width="1500" height="1200" xmlns="http://www.w3.org/2000/svg">

  <!-- Styles -->
  <style>
    .box { fill:#ffffff; stroke:#000000; stroke-width:2; rx:8; ry:8; }
    .title { font-family:Arial; font-size:20px; font-weight:bold; text-anchor:middle; }
    .text { font-family:Arial; font-size:16px; text-anchor:middle; }
    .arrow { stroke:#000000; stroke-width:2; marker-end:url(#arrowhead); }
  </style>

  <!-- Arrowhead Definition -->
  <defs>
    <marker id="arrowhead" markerWidth="10" markerHeight="7" 
            refX="10" refY="3.5" orient="auto">
      <polygon points="0 0, 10 3.5, 0 7" />
    </marker>
  </defs>

  <!-- LLM / Agent -->
  <rect x="500" y="40" width="500" height="90" class="box"/>
  <text x="750" y="80" class="title">LLM / Agent</text>
  <text x="750" y="105" class="text">(OpenAI / DeepSeek / HF / Anthropic)</text>

  <!-- Arrow to MCP Server -->
  <line x1="750" y1="130" x2="750" y2="180" class="arrow"/>

  <!-- MCP SERVER -->
  <rect x="450" y="180" width="600" height="110" class="box"/>
  <text x="750" y="225" class="title">MCP Server</text>
  <text x="750" y="255" class="text">(server.py - FastMCP)</text>

  <!-- Branch Arrows -->
  <line x1="750" y1="290" x2="350" y2="350" class="arrow"/>
  <line x1="750" y1="290" x2="750" y2="350" class="arrow"/>
  <line x1="750" y1="290" x2="1150" y2="350" class="arrow"/>

  <!-- ML FAQ Retrieval Tool -->
  <rect x="200" y="350" width="300" height="140" class="box"/>
  <text x="350" y="390" class="title">ML FAQ Retrieval Tool</text>
  <text x="350" y="420" class="text">machine_learning_faq_retrieval</text>
  <text x="350" y="450" class="text">→ Qdrant RAG</text>

  <!-- BrightData Web Search -->
  <rect x="600" y="350" width="300" height="140" class="box"/>
  <text x="750" y="390" class="title">BrightData Web Search</text>
  <text x="750" y="420" class="text">bright_data_web_search_tool</text>
  <text x="750" y="450" class="text">→ Google SERP</text>

  <!-- Future Tools -->
  <rect x="1000" y="350" width="300" height="140" class="box"/>
  <text x="1150" y="390" class="title">Future Tools</text>
  <text x="1150" y="420" class="text">PDF RAG / Browser RAG</text>
  <text x="1150" y="450" class="text">Domain Agents</text>

  <!-- Arrow to Internet -->
  <line x1="750" y1="490" x2="750" y2="540" class="arrow"/>

  <!-- Internet Search -->
  <rect x="630" y="540" width="240" height="80" class="box"/>
  <text x="750" y="580" class="title">Internet Search</text>
  <text x="750" y="605" class="text">(Google via BrightData)</text>

  <!-- Arrow to RAG Pipeline -->
  <line x1="350" y1="490" x2="350" y2="540" class="arrow"/>
  <line x1="350" y1="540" x2="750" y2="675" class="arrow"/>

  <!-- RAG Pipeline -->
  <rect x="300" y="675" width="900" height="310" class="box"/>
  <text x="750" y="715" class="title">RAG Pipeline (rag_code.py)</text>

  <!-- EmbedData -->
  <rect x="350" y="750" width="300" height="120" class="box"/>
  <text x="500" y="785" class="title">EmbedData</text>
  <text x="500" y="815" class="text">HuggingFace Embeddings</text>
  <text x="500" y="840" class="text">Batch Encoding</text>

  <!-- QdrantVDB -->
  <rect x="750" y="750" width="300" height="120" class="box"/>
  <text x="900" y="785" class="title">QdrantVDB</text>
  <text x="900" y="815" class="text">Vector Storage (DOT)</text>
  <text x="900" y="840" class="text">Fast Similarity Search</text>

  <!-- Arrows between components -->
  <line x1="650" y1="810" x2="750" y2="810" class="arrow"/>

  <!-- Retriever -->
  <rect x="550" y="900" width="400" height="120" class="box"/>
  <text x="750" y="940" class="title">Retriever</text>
  <text x="750" y="970" class="text">Query Embedding → Top-K Search</text>
  <text x="750" y="995" class="text">Combines Context Chunks</text>

  <!-- Arrow back up to LLM -->
  <line x1="750" y1="1020" x2="750" y2="1100" class="arrow"/>

  <!-- Final LLM Output -->
  <rect x="500" y="1100" width="500" height="90" class="box"/>
  <text x="750" y="1140" class="title">LLM Final Answer</text>
  <text x="750" y="1170" class="text">Grounded in FAQ / Web Search</text>

</svg>

Final Output → Sent Back to LLM → High-Quality Grounded Response

