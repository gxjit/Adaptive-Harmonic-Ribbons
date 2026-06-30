# Adaptive Harmonic Ribbons (AHR)

Adaptive Harmonic Ribbons (AHR) is a trend and market structure indicator that replaces fixed moving-average lengths with an adaptive framework driven by the market's estimated dominant cycle.

Traditional moving-average ribbons, including GMMA-style approaches, use predefined periods such as 5, 10, 20 or 60 bars. While effective under stable conditions, these lengths represent a fixed assumption about market behaviour and must often be re-optimized when volatility or market rhythm changes.

AHR takes a different approach. Instead of using fixed lookback periods, it estimates the current dominant market cycle using a Hilbert Transform-based approach. Every moving average in the ribbon is then derived from that cycle, allowing the entire ribbon to expand and contract automatically as market conditions evolve.

Rather than changing only a single adaptive moving average, AHR adapts the entire ribbon while preserving proportional spacing through harmonic scaling. This allows the relationship between the ribbon layers to remain consistent across changing market regimes.

---

## Methodology

The indicator consists of four main components:

### 1. Dominant Cycle Estimation

The market's dominant cycle is estimated continuously using a Hilbert Transform implementation inspired by John F. Ehlers' work on digital signal processing. The measured cycle is constrained within user-defined minimum and maximum bounds to improve stability.

This dominant cycle becomes the reference period from which every ribbon length is calculated.

### 2. Harmonic Length Generation

Instead of manually specifying twelve moving-average periods, AHR generates them automatically.

Fast ribbon lengths are created by dividing the dominant cycle using a harmonic expansion factor.

Slow ribbon lengths are created by multiplying the dominant cycle by the same factor.

Because every ribbon layer is derived from the same adaptive reference, the spacing between layers remains proportional even as market conditions change.

The expansion multiplier can be adjusted to produce tighter or wider ribbon structures using relationships such as:

* Third-Octave (1.26)
* Half-Octave (1.414)
* Golden Ratio (1.618)
* Full Octave (2.0)

### 3. Adaptive Smoothing

Each ribbon layer can be calculated using one of several smoothing engines:

* SuperSmoother Filter (SSF)
* Three-Pole SuperSmoother (SSF3)
* EMA
* Double EMA (EMA2)

The adaptive framework remains unchanged regardless of the smoothing method selected.

### 4. Dynamic Ribbon Construction

The resulting fast and slow ribbon groups continuously adjust their lengths as the estimated dominant cycle changes.

Instead of requiring manual optimization for different symbols or timeframes, the ribbon geometry adapts automatically while maintaining its overall structure.

---

## Interpreting the Indicator

AHR is intended as a trend analysis and market structure tool rather than a signal generator.

Some common observations include:

**Trend Agreement**

When both ribbon groups slope in the same direction and maintain consistent separation, the market may be exhibiting directional strength.

**Compression**

When ribbon layers contract toward one another, the market may be entering a lower-volatility consolidation phase.

**Expansion**

When the ribbons begin separating after a period of compression, this may indicate increasing directional momentum.

**Pullbacks**

During established trends, price retracements into the fast ribbon or the space between ribbon groups can help traders evaluate whether trend structure remains intact.

As with any moving-average-based indicator, AHR should be used alongside broader market context and appropriate risk management.

---

## Inputs

**Source**
Price series used for all calculations.

**Minimum / Maximum Dominant Cycle**
Defines the allowable range for the adaptive cycle estimator.

**Moving Average Type**
Selects the smoothing algorithm used to construct the ribbon.

**Expansion Multiplier**
Controls the proportional spacing between ribbon layers.

**Maximum Transparency**
Adjusts the visual fading effect within each ribbon.

---

## Acknowledgements

This indicator draws inspiration from two well-established areas of technical analysis:

* John F. Ehlers' research into dominant cycle estimation, Hilbert Transform techniques and SuperSmoother filtering.
* Daryl Guppy's concept of separating market participants into fast and slow moving-average groups.

The adaptive ribbon construction, harmonic length generation, dominant-cycle-derived scaling, and dynamic ribbon framework are original components developed specifically for this implementation.
