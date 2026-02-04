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


                              +-----------------------------------------+
                              |                LLM / Agent              |
                              | (OpenAI / DeepSeek / Anthropic / HF)   |
                              +------------------------+----------------+
                                                       |
                                              MCP Tool Call
                                                       |
                          +----------------------------+-----------------------------+
                          |                          MCP Server                      |
                          |                        (server.py)                       |
                          +-------------+---------------------------+-----------------+
                                        |                           |
                                        |                           |
              +-------------------------+            +--------------+--------------+
              |                                      |                             |
              v                                      v                             v
   +-----------------------------+     +------------------------------+   +-----------------------------+
   |   ML FAQ Retrieval Tool     |     |   BrightData Web Search      |   |       Future Tools         |
   | machine_learning_faq_*()    |     |  bright_data_web_search()    |   | (PDF RAG / Browser RAG /   |
   | → Qdrant RAG                |     | → Google SERP via Proxy      |   |   Domain Agents etc.)      |
   +---------------+-------------+     +---------------+--------------+   +---------------+-------------+
                   |                                   |                             
                   |                                   |                             
                   |                                   |                             
                   |                                   v                             
                   |                        +-------------------------+               
                   |                        |     Internet Search     |               
                   |                        |   (Google via Bright)   |               
                   |                        +-------------------------+               
                   |                                                           
                   |                                                           
                   v                                                           
     +-----------------------------------------------------------------------------------------+
     |                                 RAG PIPELINE (rag_code.py)                              |
     |                                                                                         |
     |   +---------------------------+       +---------------------------+        +------------+|
     |   |        EmbedData          | ----> |        QdrantVDB         | <----  | Retriever || 
     |   |  HF Embeddings (Nomic)    |       |  Vector DB (DOT Sim)     |        |  Top-K     ||
     |   |  Batch Embedding          |       |  On-Disk Segments        |        |  Search    ||
     |   +---------------------------+       +---------------------------+        +------------+|
     |                                                                                         |
     +-----------------------------------------------------------------------------------------+
                                                |
                                                |  Context Returned to MCP Server
                                                v
                              +---------------------------------------------+
                              |             LLM Final Response              |
                              | Grounded in FAQ or Web Search + Reasoning  |
                              +---------------------------------------------+


Final Output → Sent Back to LLM → High-Quality Grounded Response

