# BitStack Wealth Manager

A sophisticated decentralized multi-asset wealth orchestration protocol built for the Bitcoin Layer 2 ecosystem on Stacks. BitStack enables users to create, manage, and automatically rebalance diversified cryptocurrency portfolios with institutional-grade portfolio management capabilities and retail accessibility.

## 🚀 Features

- **Multi-Asset Portfolio Creation**: Support for up to 10 different tokens per portfolio
- **Automated Rebalancing**: Time-based rebalancing triggers with customizable thresholds
- **Risk-Adjusted Allocation**: Percentage-based asset allocation with validation
- **Bitcoin-Backed Assets**: Seamless integration with Stacks ecosystem tokens
- **Institutional-Grade Security**: Comprehensive validation and authorization controls
- **User Portfolio Management**: Track and manage multiple portfolios per user

## 📋 System Overview

BitStack Wealth Manager operates as a decentralized protocol that allows users to create sophisticated investment portfolios on the Stacks blockchain. The system manages asset allocation, tracks portfolio performance, and provides automated rebalancing capabilities.

### Key Components

1. **Portfolio Engine**: Core portfolio creation and management system
2. **Asset Allocation Manager**: Handles percentage-based distribution and validation
3. **Rebalancing Orchestrator**: Automated portfolio rebalancing with time-based triggers
4. **User Registry**: Multi-portfolio management per user account
5. **Protocol Administration**: Governance and configuration management

## 🏗️ Contract Architecture

### Data Structures

#### Core Maps

- **`Portfolios`**: Main portfolio registry storing metadata and status
- **`PortfolioAssets`**: Individual asset allocations within portfolios
- **`UserPortfolios`**: User-to-portfolio relationship mapping

#### Configuration Variables

- **`protocol-owner`**: Administrative control principal
- **`portfolio-counter`**: Global portfolio ID incrementer
- **`protocol-fee`**: Fee structure (0.25% basis points)

### System Constants

- **`MAX-TOKENS-PER-PORTFOLIO`**: 10 token limit per portfolio
- **`BASIS-POINTS`**: 10,000 (100% in basis points)

## 🔄 Data Flow

### Portfolio Creation Flow

```
User Request → Validation → Portfolio Creation → Asset Initialization → User Registry Update
```

1. **Input Validation**: Token list and percentage validation
2. **Portfolio Record**: Create main portfolio entry with metadata
3. **Asset Mapping**: Initialize individual token allocations
4. **User Association**: Link portfolio to user's account
5. **Counter Update**: Increment global portfolio counter

### Rebalancing Flow

```
Rebalance Trigger → Authorization Check → Portfolio Validation → Timestamp Update
```

1. **Authorization**: Verify portfolio ownership
2. **Status Check**: Ensure portfolio is active
3. **Time Validation**: Check if rebalancing is due (24-hour blocks)
4. **Execution**: Update last rebalanced timestamp

### Asset Allocation Update Flow

```
Update Request → Ownership Verification → Percentage Validation → Asset Update
```

## 🛠️ Core Functions

### Portfolio Management

#### `create-portfolio`

Creates a new diversified portfolio with specified tokens and allocation percentages.

**Parameters:**

- `initial-tokens`: List of up to 10 token contract addresses
- `percentages`: Corresponding allocation percentages (basis points)

**Returns:** Portfolio ID on success

#### `rebalance-portfolio`

Triggers portfolio rebalancing for optimal asset distribution.

**Parameters:**

- `portfolio-id`: Target portfolio identifier

**Requirements:** Portfolio ownership and 24-hour minimum interval

#### `update-portfolio-allocation`

Modifies individual asset allocation within existing portfolio.

**Parameters:**

- `portfolio-id`: Target portfolio
- `token-id`: Asset index within portfolio
- `new-percentage`: Updated allocation percentage

### Query Functions

#### `get-portfolio`

Retrieves complete portfolio information including metadata and status.

#### `get-portfolio-asset`

Fetches specific asset details within a portfolio.

#### `get-user-portfolios`

Returns list of all portfolios owned by a user.

#### `calculate-rebalance-amounts`

Analyzes portfolio and determines rebalancing requirements.

## 🔒 Security Features

### Access Control

- **Owner-Only Operations**: Portfolio modifications restricted to owners
- **Admin Functions**: Protocol administration requires owner privileges
- **Validation Gates**: Comprehensive input validation at all entry points

### Data Integrity

- **Percentage Bounds**: Allocation percentages validated against basis points
- **Token Limits**: Portfolio size restricted to manageable token count
- **Length Matching**: Token and percentage arrays must align

### Error Handling

Comprehensive error constants covering all failure scenarios:

- Authorization failures
- Invalid portfolio states
- Insufficient balances
- Token validation errors
- Rebalancing constraints

## 🚦 Usage Examples

### Creating a Portfolio

```clarity
;; Create a balanced BTC/STX portfolio
(create-portfolio 
  (list 'SP1BTC-TOKEN 'SP1STX-TOKEN)
  (list u5000 u5000)) ;; 50% each
```

### Rebalancing

```clarity
;; Rebalance portfolio #1
(rebalance-portfolio u1)
```

### Updating Allocation

```clarity
;; Increase BTC allocation to 60%
(update-portfolio-allocation u1 u0 u6000)
```

## 📊 Protocol Economics

- **Management Fee**: 0.25% (25 basis points)
- **Rebalancing Frequency**: Minimum 24-hour intervals
- **Portfolio Capacity**: Up to 20 portfolios per user
- **Asset Diversity**: Maximum 10 tokens per portfolio

## 🔮 Future Enhancements

- Dynamic rebalancing algorithms based on market conditions
- Integration with DeFi yield farming protocols
- Advanced risk metrics and portfolio analytics
- Cross-chain asset support
- Automated dollar-cost averaging strategies
