---
layout: post
title: "When Copilot Reads Your .env: Context-Based Secret Exposure in AI Coding Assistants"
date: 2026-01-15
categories: [AI Security, Prompt Injection]
tags: [ai-security, copilot, llm-security, prompt-injection, developer-security, secret-exposure, ai-agents]
---

## When Copilot Reads Your `.env`

AI coding assistants promise productivity—but they also introduce a new class of subtle security risks. During testing of GitHub Copilot Chat inside VS Code, I ran a small lab experiment to explore **how Copilot handles secret-bearing configuration files like `.env`**.

The results revealed something important:

> Copilot doesn’t appear to classify secrets. It simply summarizes whatever files are available in its working context.

This means that once a file containing credentials becomes accessible to the assistant—either through repository indexing or editor context—it may reproduce those values when asked.

<!--more-->

---

## Lab Setup

The experiment was performed using **GitHub Copilot Chat in VS Code** against a deliberately simple Node.js repository designed to simulate a typical developer project.

Repository structure:
