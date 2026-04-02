# UEL-1.0-alpha Specification

**Universal Execution Language for Embodied AI**  
**Version**: 1.0-alpha (April 2026)  
**Status**: Draft  
**Repository**: https://github.com/wcg696/uel-spec

## 1. Introduction

Universal Execution Language (UEL) is an open, hardware-agnostic, JSON-based execution protocol that serves as the **missing execution layer** between Large Language Models (LLMs) and physical robotic systems.

It acts as the “USB interface” for robots: any LLM can generate UEL programs, and any robot (with a compliant adapter) can execute them.

### 1.1 Design Principles
- **Hardware Agnostic** — Same UEL JSON 可在 UR5e、Franka、Unitree G1、AGV 等不同平台执行
- **Safety First** — 所有任务必须显式携带 constraints
- **Deterministic & Stateful** — 每个任务都有明确的生命周期和结果契约
- **Extensible** — 通过 Adapter Interface 允许社区贡献新机器人支持
- **Self-healing** — 支持自动 REPLAN 和错误反馈闭环

## 2. Core Data Model

```json
{
  "protocol": "UEL-1.0",
  "mission_id": "uuid-string",
  "agent_id": "robot-name-or-uuid",
  "capabilities": { ... },           // 见第 3 节
  "execution": {
    "mode": "SEQUENTIAL | PARALLEL",
    "retry": 2,
    "timeout_sec": 30
  },
  "tasks": [ ... ],
  "result": {
    "status": "SUCCEEDED | FAILED | PARTIAL",
    "error_code": null | "string",
    "latency_ms": 1842,
    "replan_hint": { ... }
  }
}
