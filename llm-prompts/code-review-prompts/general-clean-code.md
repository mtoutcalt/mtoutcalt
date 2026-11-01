- **Implicit coupling.** Two pieces of code depend on each other without saying so. Module A expects B to have already set a global, or two files must agree on a magic string. Change one and the other silently breaks. *Fix: make the dependency explicit with a parameter, a shared type, or an import.*

- **Layer-first folders.** Code is grouped by technical role (`controllers/`, `services/`, `models/`) instead of by feature (`billing/`, `auth/`). One feature ends up spread across five folders. *Fix: group by feature so related code lives together.*

- **Duplication.** The same logic is copied in several places, and the copies drift apart over time. *Fix: extract it once, but only when the copies really mean the same thing, not when they just look alike.*

- **Representable illegal states.** Your data types allow combinations that should never exist, like `{ isLoading: true, error: "x", data: {...} }` all at once. Every caller now has to guard against nonsense. *Fix: model states as distinct variants (loading / error / success) so bad combos can't be built.*

- **God files.** One file or class does everything: 3,000 lines, dozens of responsibilities, and everyone edits it. *Fix: split by responsibility.*

- **Shotgun surgery.** One small change forces edits across many files. Adding a field means touching the model, three mappers, two validators, and a switch statement. *Fix: put things that change together in one place.*

- **Layering violations.** A layer reaches past its neighbors, like UI code querying the database directly, or the domain importing HTTP details. *Fix: dependencies should only point one way, usually inward toward core logic.*

- **Pass-through wrappers.** Functions or classes that just forward calls without adding anything: `getUser(id) { return repo.getUser(id) }`. They add indirection with no value. *Fix: delete them, or make them earn their place.*

- **Errors / validation not at the boundary.** Input isn't checked where it enters the system (API, form, file), so null checks and "is this valid?" logic get scattered everywhere inside. *Fix: validate and parse once at the edge, then trust clean types internally.*
