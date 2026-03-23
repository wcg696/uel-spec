# UEL-1.0-alpha Specification

Universal Execution Language for Embodied AI Agents

UEL is a hardware-agnostic execution ISA bridging LLMs and robots.

## Core Features
- Capability-aware task generation
- Constraint-first execution
- Conditional logic & self-healing REPLAN
- Adapter-based hardware integration

## Basic Structure Example
```json
{
  "protocol": "UEL-1.0",
  "mission_id": "uuid",
  "capabilities": {"mobility": ["arm_6dof"], "end_effector": ["gripper"]},
  "tasks": [{"type": "MOVE", "target": {"x":0.4, "y":0.1, "z":0.3}}],
  "result": {"status": "SUCCESS"}
}
