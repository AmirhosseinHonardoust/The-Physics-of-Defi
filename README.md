# **The Physics of DeFi: Modeling Crashes, Liquidations, and AMM Decay**

## **Introduction, Why DeFi Behaves Like a Physical System**

Over the last several years, decentralized finance (DeFi) has grown from a small niche experiment to a multi-billion-dollar economic ecosystem. Yet despite this growth, the majority of analysis still treats DeFi as if it were simply “software with money built in.” In reality, DeFi behaves more like a **physical system** than a digital product. It is governed not by user interfaces, APIs, or DevOps practices, but by **mathematical constraints, conservation laws, threshold effects, dynamic equilibria, and nonlinear feedback loops**.

The same way a bridge withstands weight until it reaches a critical load, a lending protocol remains healthy until price shocks push collateral below liquidation thresholds. The same way a thermodynamic system evolves under forces, an AMM continually adjusts its reserves to satisfy strict invariants that resemble energy conservation rules. And the same way a small shift in temperature can trigger a phase change, a slight downward move in asset prices can trigger cascading liquidations.

To understand DeFi crashes, you cannot merely read Solidity code.
You must simulate **system behavior**.

This article explores the economic physics of DeFi protocols using a crash simulation engine, modeling how AMMs decay during price shocks, how lending pools collapse under leverage pressure, and how liquidity spirals propagate through the ecosystem.

---

# **1. DeFi Protocols Are Not Apps, They Are Equations**

Traditional financial software is UI-driven. But DeFi protocols are mathematical machines. Their internal logic is **state-driven, deterministic, and governed by strict formulas**.

Examples include:

* Automated Market Makers (AMMs) → governed by **invariant equations**
* Lending Pools → governed by **collateralization thresholds**
* Liquidation Engines → governed by **health factor inequalities**
* Yield Systems → governed by **distribution functions**

These systems respond to shocks the same way physical systems respond to pressure.

---

# **2. The AMM as a Physics Engine**

Let’s begin with the simplest and most misunderstood component: the **constant-product AMM**.

The invariant:

```
x * y = k
```

behaves like a **conservation law**.
In physics, conservation laws constrain how systems evolve.
In AMMs, the invariant constrains how reserves adjust during swaps.

### **Implications of the Invariant**

1. The AMM must always rebalance to satisfy `x * y = k`.
2. Price is an *emergent property* derived from reserve ratios.
3. Value decay is unavoidable during price volatility.
4. Arbitrageurs enforce equilibrium, not stability.

This means AMMs inherently drift toward the **worst-performing asset** during shocks, just as a physical system drifts toward higher entropy.

---

# **3. Modeling the Crash Itself**

Your controlled crash simulation demonstrates this beautifully.

### **3.1 The Price Shock Curve**

This graph represents:

* a stable initial state
* a deterministic linear decline
* a smooth descent into a lower price regime

This is deliberately simple because complex dynamics become clearer when the foundational elements are pure.

A linear crash functions like a **uniform external force** applied to the system.

---

# **4. AMM Decay: Why Pool Value Falls Even If Code Is Perfect**

The AMM’s response to the crash reveals the deeper story:

Even with no arbitrage delays, no MEV attacks, and no oracle manipulations, the pool value decays. This is not accidental.
It is **mathematically inevitable**.

Let’s break it down.

---

## **4.1 Inventory Drift, The AMM Accumulates the Losing Asset**

As price crashes, arbitrageurs swap:

* the asset that is becoming more expensive
* for the asset that is becoming cheaper

Which means:

> **The AMM becomes the largest holder of the asset that is losing value fastest.**

This is the AMM equivalent of **structural stress accumulation** in physics.

---

## **4.2 Impermanent Loss, A Strict Mathematical Penalty**

Pool value:

```
V_pool = reserve0 + reserve1 * price
```

Even if the AMM stayed perfectly balanced (it won’t), divergence occurs:

* When price moves down → reserves shift up in the losing asset
* When price moves up → reserves shift up in the winning asset

But crashes cause *asymmetric exposure*:
the AMM accumulates more of the collapsing asset.

Impermanent loss is the economic equivalent of **friction**:

* it cannot be eliminated
* only minimized
* and during volatility, friction dominates dynamics

---

## **4.3 Nonlinear Decay, Why the Curve Isn’t Straight**

The AMM decay curve is **nonlinear**, even though your price curve is linear.

This is the hallmark of physical systems under constraints:

* energy decays exponentially under damping
* radioactive decay follows exponential curves
* elastic materials deform non-linearly

Likewise, AMM value decays more rapidly as price continues downward because:

```
reserve1(t) * price(t)
```

shrinks superlinearly.

---

# **5. Lending Pools: The DeFi Equivalent of Structural Load-Bearing Systems**

While AMMs decay gradually, lending pools break suddenly.

Collateralized lending is governed by:

```
health = collateral_value / debt
```

A liquidation threshold acts as a **critical failure point**, similar to:

* the load limit of a beam
* the thermal limit of a material
* the yield stress of metal

When price shocks push collateral below a threshold, the system enters a new phase:

```
healthy → at-risk → liquidated
```

This is a **phase transition**.

---

# **6. Liquidation Cascades, The Avalanche Model**

Liquidations cause:

* market sell pressure
* collateral outflows
* debt write-downs
* liquidity distortions

This creates a feedback loop:

```
price ↓
   → collateral value ↓
       → health ↓
           → liquidations ↑
               → sell pressure ↑
                   → price ↓ (again)
```

This is identical to:

* avalanches
* earthquakes
* chain reactions

Small shocks can trigger large system-wide failures.

---

# **7. When AMMs and Lending Pools Interact**

Crashes become more severe when AMMs and lending pools combine:

* AMMs lose value
* Lending collateral melts
* Liquidations accelerate
* AMMs absorb liquidation flows
* AMM decay speeds up
* Which pushes collateral lower
* Which triggers more liquidations

This is **contagion**, the core driver of DeFi systemic risk.

---

# **8. Simulation as the Only True Method of Understanding DeFi**

Static reasoning fails because DeFi systems are:

* nonlinear
* dynamic
* interconnected
* path-dependent

Simulation solves this by letting the system evolve under:

* price shocks
* liquidity stresses
* time-varying behavior
* arbitrage flows

Your simulation engine acts like a **quantitative physics lab** for DeFi:

* Solidity provides the equations
* Python provides the dynamics
* Streamlit provides the visualization

This turns DeFi from speculation into science.

---

# **9. Practical Lessons for Real DeFi Protocols**

### **9.1 AMM Design Improvements**

* Adaptive fees based on volatility
* Concentrated liquidity defense modes
* Market-maker smoothing layers

### **9.2 Lending Pool Safety**

* Dynamic LTV based on volatility
* Real-time price sensitivity measures
* Liquidation buffers

### **9.3 System-Wide Circuit Breakers**

* temporary pause mechanisms
* rate-limited liquidations
* circuit breakers triggered by volatility spikes

These aren’t hacks, they’re **engineering controls** used in physical systems.

---

# **10. Conclusion, Crashes Are Not Bugs, They’re Laws of Motion**

DeFi behaves like physics.

Crashes follow predictable patterns:

* AMM decay is inevitable under volatility
* Liquidations follow threshold rules
* Feedback loops amplify shocks
* Contagion arises from interconnected design

Understanding these patterns requires treating DeFi protocols as **mathematical ecosystems**, not as apps.

To build safer systems, we must:

* model them
* simulate them
* analyze their critical points
* design protective structures

Just like in engineering, **stress testing reveals truth**.

Your DeFi Risk Scenario Lab is not just a tool, it is a window into the economic physics driving decentralized finance.
