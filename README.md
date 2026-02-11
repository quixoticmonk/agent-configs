# Agent Configs

Sample agent configurations showcasing Terraform skills integration with Kiro CLI.

## Overview

This repository demonstrates how to leverage HashiCorp Agent Skills with Kiro CLI for infrastructure as code development. The configurations here showcase practical implementations of Terraform-focused AI agent capabilities.

## Installed Skills

The following Terraform skills are configured in `~/.kiro/skills/`:

### Core Terraform Skills
- **terraform-style-guide** - Generates Terraform HCL code following HashiCorp's official style conventions and best practices
- **terraform-test** - Comprehensive guide for writing and running Terraform tests, including creating `.tftest.hcl` files and test scenarios
- **terraform-stacks** - Complete guide for working with HashiCorp Terraform Stacks, including creating and managing `.tfcomponent.hcl` and `.tfdeploy.hcl` files

### Development & Refactoring
- **refactor-module** - Transforms monolithic Terraform configurations into reusable, maintainable modules following HashiCorp's best practices
- **terraform-skill** - General Terraform development assistance and best practices

### Discovery & Import
- **terraform-search-import** - Discover existing cloud resources using Terraform Search queries and bulk import them into Terraform management
- **find-skills** - Helps discover and install additional agent skills when you ask questions like "how do I do X" or "find a skill for X"

## Agent Configuration

The skills are integrated through a custom `iac` (Infrastructure as Code) agent configuration that combines:

- **MCP Servers**: AWS Documentation and Terraform MCP servers for enhanced context
- **Skills Resources**: Dynamic loading of skills using `skill://~/.kiro/skills/**/SKILL.md` pattern
- **Specialized Tools**: Full access to development and AWS management tools

### Key Features

- **Context-Aware Loading**: Skills are loaded dynamically when needed, preventing context overflow
- **Version-Aware Workflows**: Handles different Terraform versions and provider capabilities
- **Multi-Provider Support**: Works with AWS, AWSCC, and other Terraform providers
- **Import Automation**: Automated discovery and import of existing cloud resources

## Usage Examples

### Terraform Stacks
```bash
kiro-cli --agent iac
# Ask: "How do I create a Terraform stacks config for a VPC from my private registry?"
```

### Resource Import
```bash
# Discover and import existing S3 buckets
# Ask: "Create terraform configuration for importing S3 buckets from my AWS account"
```

### Code Generation
```bash
# Generate properly formatted Terraform code
# Ask: "Generate a secure S3 bucket configuration following HashiCorp style guide"
```

## Blog Posts

For detailed implementation guides and experiences:

- [Kiro has Terraform skills](https://manuchandrasekhar.com/posts/2026/01-27-kiro-terraform-skills/) - Initial setup and configuration of HashiCorp Agent Skills with Kiro CLI
- [Adding agent skills for Terraform](https://manuchandrasekhar.com/posts/2026/02-06-adding-tf-skills/) - Creating custom skills and using tessl for evaluation

## Skills Installation

Install HashiCorp Agent Skills:

```bash
# Install all Terraform skills
npx skills add hashicorp/agent-skills

# Or install specific skills
npx skills add hashicorp/agent-skills/terraform/code-generation/skills/terraform-style-guide
```

Configure in Kiro CLI agent:
```json
{
  "resources": ["skill://~/.kiro/skills/**/SKILL.md"]
}
```
