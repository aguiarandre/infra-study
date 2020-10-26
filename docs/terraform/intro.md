# Terraform

## Infrastructure as Code - IaC

- Automated deployment
- Consistent environments
  - You won't forget steps
- Repeatable process
- Reusable components
  - use same configuration for a database server, for instance
- Documented architecture

### Declarative vs Imperative

#### Imperative
- step-by-step on how to create TACO
```python
def make_me_taco():
  """ Making a taco in an imperative way. """
  _get_beans()
  _get_cheese()
  _put_beans()
  _put_cheese()
```

#### Declarative
- config file containing information to create TACO
- internally, the program knows how to create TACO
- you can also explicitly bring more options on TACO creation.

```python
food taco "bean-taco" {
  ingredients = ['beans', 'cheese']
}
```

### Idempotent and consistent

If someone order me a TACO, whether I make a TACO or not depends on
the state of the person. If the person **already has** a TACO (I know 
the state of the person), I won't do it again. 

Terraform attempts to apply changes only if necessary.

### Push and Pull

#### Push
- Send configuration to the target environment (Terraform works like this)

#### Pull 
- Target environment pulls updates regularly.