# Production AI Video Rendering with VideoJSON and MCP

AI agents are good at creative intent. Production renderers need a deterministic contract: exact canvas dimensions, frame rate, duration, scenes, layers, text constraints, transitions, effects, media sources, and audio behavior.

This guide documents a reliable six-stage workflow for turning an agent plan into an auditable video render.

## 1. Plan the story and its evidence

Define the hook, proof, and call to action before composition. Assign exact scene durations and choose evidence timestamps after entrances complete, during the densest scene, and before the CTA exits.

## 2. Compose explicit VideoJSON

A composition should make every important decision inspectable. Text layers need a maximum width and line budget. Optional variables must control dependent layers. Media should use stable HTTPS sources. The composition duration must equal the sum of all scene durations.

VideoJSON is the execution contract between an AI agent and the renderer. Prompts hold creative intent; the contract holds deterministic instructions.

## 3. Validate before preview

Validate schema shape, supported layer types, transitions, easings, text constraints, external asset availability, timeline consistency, and audio coverage. Reject local blob or file sources before remote submission. Specific validation errors are cheaper than failed render jobs.

## 4. Capture preview evidence

Preview representative frames and store the timestamp, scene ID, composition version, and review findings. Check contrast, safe areas, wrapping, entrance completion, and CTA readability. Evidence makes visual feedback reproducible.

## 5. Render idempotently

Submit only validated compositions. Attach an idempotency key so a network retry cannot create duplicate jobs or duplicate costs. Keep job creation behind one documented API boundary.

## 6. Inspect the final MP4

Verify duration, resolution, frame rate, codec, download availability, and representative final frames. Completion means the artifact matches the contract, not merely that the job status changed to complete.

## Architecture boundary

- Prompts hold creative intent.
- Agents plan, compose, validate, and revise.
- VideoJSON is the execution contract.
- The renderer executes deterministically.
- Evidence closes the review loop.

Explore [iLoveVideoEditor](https://ilovevideoeditor.com/?utm_source=readthedocs&utm_medium=documentation&utm_campaign=videojson_mcp_guide).

Use the [iLoveVideoEditor MCP server](https://github.com/ilovevideoeditor/mcp-server?utm_source=readthedocs&utm_medium=documentation&utm_campaign=videojson_mcp_guide) with AI agents.
