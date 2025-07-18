## 📁 Project Structure

``` js
src/
├── config/              # Environment configs, DB connections
│   └── db.ts
│   └── redis.ts
│   └── env.ts
├── controllers/         # Route handlers (business logic)
│   └── user.controller.ts
├── routes/              # Express routers
│   └── user.routes.ts
├── services/            # Business logic (used by controllers)
│   └── user.service.ts
├── middlewares/         # Custom middlewares (auth, error, logger)
│   └── auth.middleware.ts
│   └── error.middleware.ts
├── models/              # DB models / schemas (Mongoose, Prisma, etc.)
│   └── user.model.ts
├── validators/          # Request validation logic
│   └── user.validator.ts
├── utils/               # Utility functions (helpers, error classes)
│   └── apiResponse.ts
│   └── logger.ts
├── types/               # Custom types/interfaces
│   └── user.d.ts
├── app.ts               # Express app initialization
├── server.ts            # Server listener
├── constants/           # Constant values, enums, etc.
│   └── roles.ts
├── package.json
├── tsconfig.json
├── .env
```

## 🔧 How It All Connects
- server.ts → imports app.ts, starts the server.
- app.ts → sets up middlewares, routes from /routes.
- Each route.ts → uses corresponding controller.ts.
- controller.ts → calls service.ts to run logic.
- service.ts → uses model.ts to access DB.
- validators/ → used as middleware for validating inputs.
- middlewares/ → handles error catching, auth, logging, etc.

## 🧠 Why This Works
- Separation of Concerns: Keeps logic, routing, validation, and database cleanly separated.
- Scalable: You can add new modules without touching old code.
- Testable: Each layer can be tested independently (e.g., service unit tests).
- Reusable: Logic in services can be reused across routes/controllers.

## 🧪 Bonus Tip – Add a `__tests__/` or `tests/` Folder
``` js
tests/
├── unit/
│   └── user.service.test.ts
├── integration/
│   └── user.routes.test.ts
```