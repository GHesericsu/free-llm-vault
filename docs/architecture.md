# FreeRouter Architecture

## Concept
A composable layer that aggregates multiple free LLM API providers into a single OpenAI-compatible endpoint.

## Layers
1. **API Surface**: OpenAI-compatible (v1/chat/completions).
2. **Middleware**: Logic for tier classification, quota gating, and provider selection.
3. **Provider Pool**: The collection of free API keys (Groq, Cerebras, Mistral, etc.).
4. **Health Monitor**: Tracks 429s and timeouts to manage "cool down" periods for providers.

## Virtual Model Aliases
- `free/heavy`: Smartest available (e.g., Qwen-3-235B, Llama 3.3 70B).
- `free/light`: Fastest/highest volume (e.g., Llama 3.1 8B, Gemini Flash-Lite).
- `free/coding`: Code-optimized (e.g., Qwen3-Coder).
