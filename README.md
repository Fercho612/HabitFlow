# HabitFlow

Dashboard personal de productividad para registrar hábitos diarios, planificar la semana en bloques horarios y seguir la constancia con estadísticas.

Es un proyecto de portfolio desarrollado con **Spec-Driven Development** y un agente de IA (Claude Code) como asistente de programación.

## Funcionalidades

**Hábitos**
- Crear, editar y borrar hábitos, con frecuencia por día de la semana.
- Matriz semanal para marcar cada día como hecho o no hecho, con navegación entre semanas.
- Cumplimiento de hoy, racha actual, racha récord y consistencia de los últimos 30 días.
- Reordenar la lista arrastrando con mouse o con el dedo, o con botones Subir/Bajar desde el teclado.

**Calendario semanal**
- Semana tipo armada con bloques de tiempo (time-blocking).
- Categorías con color, franja horaria configurable y resumen de horas por categoría.
- Hábitos asignados a cada bloque, con aviso si un hábito no corresponde a ese día.

**Estadísticas**
- Tasa de cumplimiento del período (semana, mes o 90 días) comparada con el período anterior.
- Mejor racha, días perfectos, mapa de calor de 17 semanas y ranking de hábitos.
- Filtro para analizar un solo hábito.

**Datos**
- Se guardan en `localStorage`, con versión de formato y migración (`v1` → `v2`).
- Un dato guardado corrupto nunca se sobrescribe sin leerlo antes.

## Tecnologías

- React 19 + Vite
- JavaScript y CSS escrito a mano (sin librerías de componentes)
- Vitest para tests unitarios
- Git + GitHub con ramas por funcionalidad y pull requests

## Cómo ejecutarlo

Requisito: una versión LTS reciente de [Node.js](https://nodejs.org/).

```bash
git clone https://github.com/Fercho612/HabitFlow.git
cd HabitFlow/frontend
npm install
npm run dev
```

Otros comandos (dentro de `frontend/`):

| Comando | Qué hace |
| --- | --- |
| `npm test` | Corre los tests unitarios con Vitest |
| `npm run build` | Genera la versión de producción |
| `npm run preview` | Sirve localmente la versión de producción |

## Cómo se desarrolló

Cada funcionalidad pasó por el mismo ciclo: **spec → plan → tareas → código → revisión**.

- [`docs/constitution.md`](docs/constitution.md): principios del proyecto (stack mínimo, spec antes que código, lógica separada de la interfaz, tests, cuidado de los datos del usuario).
- [`docs/specs/`](docs/specs/): una spec por funcionalidad, con historias de usuario y requisitos; las más grandes incluyen su `plan.md` y `tasks.md`.
- [`AGENTS.md`](AGENTS.md): reglas de trabajo para el agente de IA, que asiste y explica pero no reemplaza las decisiones del autor.
- Commits pequeños con formato `feat:`, `fix:` y `docs:`, y cada funcionalidad integrada por pull request.

## Estructura

```
frontend/src/
├── components/        # Componentes compartidos (Sidebar)
├── features/
│   ├── habits/        # Hábitos: matriz semanal, formulario, métricas
│   ├── schedule/      # Calendario semanal en bloques
│   └── stats/         # Estadísticas y gráficos
├── lib/dates.js       # Utilidades de fechas en hora local
└── styles/            # Tokens de diseño y estilos globales
```

La lógica vive en módulos `.js` puros con sus tests (`*.test.js`), la persistencia en los hooks `use*.js` y los componentes `.jsx` solo muestran datos.

## Próximos pasos

- Backend con Python, FastAPI y PostgreSQL, levantado con Docker.

## Autor

Fernando Pereyra Galetti · [GitHub](https://github.com/Fercho612)
