# 🌲 Picea

**Write your domain logic once. Run it everywhere.**

Picea is a .NET ecosystem built on the observation that MVU, Event Sourcing, and the Actor Model are all instances of the same mathematical structure — a **Mealy machine** (finite-state transducer with effects):

```
transition : (State × Event) → (State × Effect)
```

Define your pure domain logic once as a transition function. Plug it into any runtime.

## Packages

| Package | Repo | Description |
|---------|------|-------------|
| **[Picea](https://github.com/picea/picea)** | [picea/picea](https://github.com/picea/picea) | The kernel: `Automaton<>`, `Result<>`, `Decider<>`, Runtime, Diagnostics |
| **[Picea.Abies](https://github.com/picea/abies)** | [picea/abies](https://github.com/picea/abies) | Model-View-Update framework — Browser, Server, Kestrel, Analyzers, Templates |
| **[Picea.Mariana](https://github.com/picea/mariana)** | [picea/mariana](https://github.com/picea/mariana) | Resilience patterns: Retry, Circuit Breaker, Rate Limiter, Hedging, Timeout, Fallback |
| **[Picea.Glauca](https://github.com/picea/glauca)** | [picea/glauca](https://github.com/picea/glauca) | Event Sourcing: AggregateRunner, EventStore, Projections, KurrentDB adapter |
| **[Picea.Rubens](https://github.com/picea/rubens)** | [picea/rubens](https://github.com/picea/rubens) | Actor model: Actor, Address, Envelope, Reply |

## Architecture

```
Picea (kernel) ← no framework dependency
    ↑
    ├── Picea.Mariana (resilience)
    ├── Picea.Abies (MVU)
    │     ├── Picea.Abies.Browser
    │     ├── Picea.Abies.Server → Picea.Abies.Server.Kestrel
    │     └── Picea.Abies.Analyzers
    ├── Picea.Glauca (Event Sourcing)
    │     └── Picea.Glauca.KurrentDB
    └── Picea.Rubens (Actor model)
```

## The Naming

*Picea* is the genus of spruce trees. Each repo is named after a species:

| Repo | Species | Why |
|------|---------|-----|
| **picea** | *Picea* (genus) | The root — the kernel everything grows from |
| **abies** | *Abies* (sister genus) | Sister genus in subfamily Abietoideae — MVU is the sister framework |
| **glauca** | *Picea glauca* (White spruce) | Hardy, widely distributed — Event Sourcing is the proven workhorse |
| **rubens** | *Picea rubens* (Red spruce) | Grows at high altitude — Actor model scales to distributed heights |
| **mariana** | *Picea mariana* (Black spruce) | Thrives in harsh conditions — perfect for resilience patterns |

## Getting Started

```bash
dotnet add package Picea
```

See [picea/picea](https://github.com/picea/picea) for documentation, tutorials, and API reference.

## License

All Picea packages are licensed under [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0).
