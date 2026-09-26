Laravel CI/CD Testing: Local Validation with Artisan and Vite

Overview

This project documents a practical approach to validating a Laravel application in a local development environment before troubleshooting or deploying through a CI/CD pipeline.

When working with CI/CD, failures can originate from different layers of an application, including the Laravel backend, frontend assets, dependencies, build processes, configuration, or the deployment environment.

Local validation helps isolate these issues before investigating the pipeline itself.

This project focuses on two common development commands:

php artisan serve

and

npm run dev

Problem

CI/CD pipelines can fail for different reasons, and not every failure is caused by the CI/CD configuration.

For example, an application may already have a problem with:

- Laravel application execution
- PHP dependencies
- JavaScript dependencies
- CSS or JavaScript assets
- Vite configuration
- Frontend build processes
- Environment configuration
- Application routes or backend functionality

Running basic local validation before investigating the pipeline can help determine whether the problem exists in the application itself or is introduced during the CI/CD process.

Why Local Validation Matters

A useful troubleshooting approach is to validate the application in stages.

Application
     |
     v
Local Validation
     |
     +---- Laravel Backend
     |
     +---- Frontend Assets
     |
     v
CI/CD Pipeline
     |
     v
Deployment

If the application does not work correctly in the local development environment, investigating the CI/CD pipeline first may lead to unnecessary troubleshooting.

Local validation provides an initial reference point.

"php artisan serve"

The following command starts Laravel's built-in development server:

php artisan serve

By default, the application becomes available at:

http://127.0.0.1:8000

This allows developers to validate the Laravel application locally.

Examples of things that can be checked include:

- Application startup
- Routes
- Controllers
- Authentication
- API endpoints
- Database interactions
- Application configuration
- Backend functionality

This command is intended for development and testing. It is not a replacement for a production web server such as Nginx or Apache with PHP-FPM.

"npm run dev"

Laravel applications using Vite commonly use:

npm run dev

This starts the Vite development environment and allows frontend assets to be processed during development.

Depending on the project configuration, this can include:

- JavaScript
- CSS
- Tailwind CSS
- Vue
- React
- Other frontend assets

It also provides a development workflow where changes to frontend files can be reflected quickly during development.

Running Both Together

During development, it is common to run both processes.

Terminal 1

php artisan serve

Terminal 2

npm run dev

The first process runs the Laravel application, while the second handles the frontend development environment.

This provides a practical way to validate both sides of the application before moving further into the CI/CD workflow.

Local Validation Workflow

A simple validation workflow can be:

1. Install dependencies
        |
        v
2. Start Laravel
        |
        v
3. Start Vite
        |
        v
4. Test application locally
        |
        v
5. Identify and fix local issues
        |
        v
6. Run CI/CD pipeline
        |
        v
7. Validate deployment

The objective is not to reproduce the entire CI/CD environment locally.

The objective is to identify basic application or frontend problems as early as possible.

Troubleshooting CI/CD Issues

When a pipeline fails, local validation can help narrow down the problem.

For example:

Application works locally
        |
        v
CI/CD fails
        |
        v
Investigate pipeline configuration,
dependencies, environment variables,
build process, runner, or deployment.

Alternatively:

Application fails locally
        |
        v
Fix application/development issue
        |
        v
Validate again
        |
        v
Run CI/CD pipeline

This approach helps separate application-level problems from pipeline or deployment problems.

Development vs Production

The commands documented here are primarily intended for development and local testing.

A production Laravel environment normally requires a different architecture, which may include:

- Nginx or Apache
- PHP-FPM
- Database services
- Process management
- Production environment variables
- Optimized Composer dependencies
- Built frontend assets
- TLS/SSL
- Monitoring and logging
- Backup and recovery procedures

For example, a production environment should not normally rely on:

php artisan serve

as its web server.

Similarly, frontend assets are generally built for production rather than relying on the Vite development server.

Scope

This project is focused on the relationship between:

- Laravel
- PHP
- Vite
- Frontend assets
- Local validation
- CI/CD troubleshooting
- Pre-deployment testing

It is intended as a practical technical reference rather than a complete Laravel or CI/CD guide.

Contributing

Contributions are welcome.

If you have improvements, corrections, additional test cases, troubleshooting scenarios, or suggestions related to Laravel, Vite, or CI/CD validation, feel free to contribute.

You can contribute by:

- Opening an issue to report a problem or suggest an improvement.
- Submitting a pull request with documentation or technical improvements.
- Sharing additional troubleshooting scenarios or validation approaches.

Before submitting a pull request, please make sure that your changes are clear, technically accurate, and relevant to the purpose of this project.

Key Takeaways

Local validation can be a useful step when troubleshooting CI/CD problems.

The commands:

php artisan serve

and

npm run dev

provide a simple way to validate the Laravel backend and frontend development environment before moving further into the CI/CD and deployment process.

The goal is simple:

«Validate early, isolate the problem, and deploy with greater confidence.»
