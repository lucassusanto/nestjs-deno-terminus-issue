# nestjs-deno-terminus-issue

## Problem

- NestJS cannot resolve ModuleRef dependency after TerminusModule is added

## How To Reproduce

1. Clone the minimal reproducible project example
   ```
   git clone https://github.com/lucassusanto/nestjs-deno-terminus-issue
   ```
2. Install the dependencies
   ```
   deno install
   ```
3. Run the application
   ```
   deno run --allow-env --allow-net --allow-read src/main.ts
   ```
4. NestJS won't start

   ```
   [Nest] 13408  - 10/20/2024, 3:06:53 PM   ERROR [ExceptionHandler] Nest can't resolve dependencies of the TypeOrmHealthIndicator (?). Please make sure that the argument ModuleRef at index [0] is available in the TerminusModule context.

   Potential solutions:
   - Is TerminusModule a valid NestJS module?
   - If ModuleRef is a provider, is it part of the current TerminusModule?
   - If ModuleRef is exported from a separate @Module, is that module imported within TerminusModule?
     @Module({
       imports: [ /* the Module containing ModuleRef */ ]
     })
   ```

## Expected Result

- NestJS should run without error
  ```
  [Nest] 13531  - 10/20/2024, 3:07:54 PM     LOG [NestApplication] Nest application successfully started +7ms
  ```

## Additional Context

- Deno version
  ```
  deno 2.0.2 (stable, release, x86_64-unknown-linux-gnu)
  v8 12.9.202.13-rusty
  typescript 5.6.2
  ```
