1️⃣6️⃣ Workflow Call (Reusable Workflows)


Real-World Example:

Imagine your company has 20 microservices:

insurance-api
claims-api
customer-api
payment-api
notification-api

Every repository needs:

1.Checkout code
2.Build application
3.Run tests
4.Build Docker image
5.Push image to registry

Without reusable workflows:

insurance-api   -> same pipeline code
claims-api      -> same pipeline code
customer-api    -> same pipeline code
payment-api     -> same pipeline code

Lots of duplicate YAML.


Instead:

Central DevOps Repository
      |
      |---- reusable-build.yml
      |
      +---- reusable-deploy.yml

All Applications
      |
      +---- Call reusable workflow


## Project Structure

# Repository 1

github-actions-templates
│
└── .github
    └── workflows
         └── reusable-build.yml

Contains common build workflow

# Repository 2

insurance-api
│
└── .github
    └── workflows
         └── ci.yml

Calls reusable workflow