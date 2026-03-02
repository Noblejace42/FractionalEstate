# Contributing to FractionalEstate

Thank you for your interest in contributing to FractionalEstate! This document provides guidelines and instructions for contributing.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Pull Request Process](#pull-request-process)
- [Coding Standards](#coding-standards)
- [Testing Requirements](#testing-requirements)
- [Documentation](#documentation)

---

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment. We expect all contributors to:

- Use welcoming and inclusive language
- Be respectful of differing viewpoints
- Accept constructive criticism gracefully
- Focus on what is best for the community

---

## Getting Started

### Prerequisites

1. Fork the repository
2. Clone your fork locally
3. Set up the development environment (see README.md)
4. Create a feature branch

```bash
git clone https://github.com/YOUR_USERNAME/fractionalestate.git
cd fractionalestate
git checkout -b feature/your-feature-name
```

### Development Setup

```bash
# Install blockchain dependencies
cd blockchain && npm install

# Install frontend dependencies
cd ../frontend && npm install

# Start local blockchain
npx ganache --port 7545

# Deploy contracts
cd ../blockchain && npx truffle migrate --network development

# Start frontend
cd ../frontend && npm run dev
```

---

## Development Workflow

### Branch Naming Convention

| Type | Format | Example |
|------|--------|---------|
| Feature | `feature/description` | `feature/add-secondary-market` |
| Bug Fix | `fix/description` | `fix/dividend-calculation` |
| Refactor | `refactor/description` | `refactor/governance-hooks` |
| Docs | `docs/description` | `docs/update-api-reference` |

### Commit Message Format

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(contracts): add secondary market trading

Implements ERC-1155 share trading between investors with
platform fee collection.

Closes #42
```

```
fix(frontend): correct dividend calculation display

The dashboard was showing raw wei values instead of
formatted ETH amounts.

Fixes #123
```

---

## Pull Request Process

### Before Submitting

1. **Run all tests:**
   ```bash
   cd blockchain && npm test
   cd ../frontend && npm test
   ```

2. **Lint your code:**
   ```bash
   cd frontend && npm run lint
   ```

3. **Update documentation** if needed

4. **Add tests** for new functionality

### PR Requirements

- [ ] Descriptive title following commit convention
- [ ] Clear description of changes
- [ ] Reference related issues
- [ ] All tests passing
- [ ] No linting errors
- [ ] Documentation updated
- [ ] Screenshots for UI changes

### Review Process

1. Submit PR against `main` branch
2. Request review from maintainers
3. Address feedback
4. Maintain PR until merged

---

## Coding Standards

### Solidity

- Use Solidity 0.8.19+
- Follow [Solidity Style Guide](https://docs.soliditylang.org/en/latest/style-guide.html)
- Use NatSpec comments for all public functions
- Prefer OpenZeppelin implementations

```solidity
/**
 * @notice Purchases shares of a tokenized property
 * @dev Transfers ETH and mints ERC-1155 tokens
 * @param propertyId The ID of the property
 * @param quantity Number of shares to purchase
 */
function purchaseShares(uint256 propertyId, uint256 quantity) external payable {
    // Implementation
}
```

### TypeScript/React

- Use TypeScript strict mode
- Prefer functional components with hooks
- Use meaningful variable names
- Extract reusable logic to custom hooks

```typescript
// Good
const { data: property, isLoading } = useProperty(propertyId);

// Avoid
const x = useProperty(id);
```

### CSS/Tailwind

- Use Tailwind utility classes
- Extract repeated patterns to components
- Follow mobile-first approach
- Use design system tokens

---

## Testing Requirements

### Smart Contracts

All smart contracts must have:
- Unit tests for each function
- Integration tests for workflows
- Edge case coverage
- Gas optimization tests

```javascript
describe("FractionalEstate", function() {
  it("should allow verified investors to purchase shares", async function() {
    // Test implementation
  });
  
  it("should revert for unverified investors", async function() {
    // Test implementation
  });
});
```

### Frontend

- Component tests with React Testing Library
- Hook tests for custom hooks
- Integration tests for pages
- E2E tests for critical flows

```typescript
describe('PropertyCard', () => {
  it('displays property information correctly', () => {
    render(<PropertyCard property={mockProperty} />);
    expect(screen.getByText('Luxury Apartment')).toBeInTheDocument();
  });
});
```

---

## Documentation

### Code Documentation

- Add JSDoc comments to functions
- Document complex logic inline
- Keep README.md current
- Update API documentation

### Types of Documentation

| Document | Purpose | Location |
|----------|---------|----------|
| README.md | Project overview | Root |
| DEPLOYMENT.md | Deployment guide | /docs |
| API.md | API reference | /docs |
| ARCHITECTURE.md | System design | /docs |

---

## Questions?

- Open a [GitHub Discussion](https://github.com/your-org/fractionalestate/discussions)
- Check existing [Issues](https://github.com/your-org/fractionalestate/issues)
- Review [Documentation](./docs/)

Thank you for contributing! 🎉
