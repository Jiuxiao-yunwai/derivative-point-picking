---
name: derivative-point-picking
description: Solve high-school or college-entrance-exam style math problems with grader-friendly proof writing. Use when a problem involves functions, derivatives, inequalities, parameter ranges, existence of roots/intersections, value ranges, maxima/minima, monotonicity tables, sequences, or when the user wants a solution suitable for Gaokao-style marking: analyze with limits/continuity when helpful, but present sufficiency and existence using principled point selection, sign changes, monotonicity, and the intermediate value theorem rather than relying only on asymptotic "tends to" language. When teaching students, explain where chosen points come from using tangent bounds, exponential/log inequalities, Taylor-style local estimates, quadratic fitting, or explicit threshold solving.
---

# Derivative Point Picking

## Core Principle

Use flexible analysis to find the answer, then rewrite the final proof in a marking-safe form. Limits, graphs, and intuition are allowed in scratch reasoning, but the final solution should prove existence with concrete intervals, selected points, sign changes, monotonicity, or value-range arguments that explicitly show every value is attained.

When explaining to students, never make a chosen point look magical. After the answer is discovered, show how the point is reverse-engineered from a target inequality. Common points such as \(0,1,e,2\) may be used directly when they are natural endpoints or standard comparison points; parameter-dependent points need a reason.

## Workflow

1. Translate the condition into an equation, inequality, zero of a function, or value-range problem.
2. Analyze with derivatives, monotonicity, extrema, continuity, and limits to discover the likely answer.
3. Separate necessity and sufficiency whenever the result is a parameter range.
4. For necessity, use extrema, inequalities, monotonicity, or comparison from the assumed existence.
5. For sufficiency, derive a target inequality that would make the desired sign/value true.
6. Choose points by solving or over-solving that target inequality after a suitable bound.
7. Apply continuity, monotonicity, the intermediate value theorem, or contradiction.
8. Finish with the exact parameter set and verify endpoints.

## Existence Proof Pattern

When a condition is equivalent to `F(x)=c` or `H(x)=0`:

1. Define the function on its exact domain.
2. Use derivatives to locate monotonic intervals and extrema.
3. Prove necessity from the extremum or inequality.
4. Prove sufficiency by selecting two concrete points in the same valid interval:
   - one point where the function value is above the target;
   - one point where the function value is below or equal to the target;
   - then invoke continuity and the intermediate value theorem.
5. Explain how each selected point was obtained from a bound or threshold.
6. If the endpoint itself works, state that explicitly.

Use limits only to guide the choice of the concrete point or to support a separately stated value-range theorem. Do not make the final sufficiency depend only on "as \(x\to a\), \(F(x)\to \infty\)" unless the argument explicitly says that by the definition of limit there exists a point satisfying the needed inequality.

## Point Selection Principles

Pick points by reverse-engineering the sign you need.

- Find the desired sign first: for example, to show \(H(x_0)>0\), first reduce \(H(x)\) to a simpler lower bound \(L(x)\), then choose \(x_0\) so \(L(x_0)>0\).
- Decide which term is dominant on the target interval. If \(e^x\) is too strong, replace it by a lower bound such as \(1+x\), \(x\), or a Taylor/tangent bound. If \(e^x\) is small on a negative interval, use \(0<e^x<1\). If \(x\) is the weak term compared with \(e^x\), use \(x<e^x\).
- Use tangent bounds and Taylor-style estimates as point-finding tools: \(e^x\ge 1+x\), \(e^x>x\), \(e^x\ge ex\) for \(x>0\), and local upper bounds after restricting the interval, such as \(0<x<1\Rightarrow (1+x)e^x<2e\).
- For mixed exponential, logarithmic, and polynomial expressions, consider homomorphic transformations first: substitutions such as \(u=\ln x\), rewriting \(ae^u-u^2=0\) as \(u^2e^{-u}=a\), or other "朗博同构" style reductions that turn the problem into a single-variable extremum plus sign selection.
- When one bound produces a condition like \(x\le -1/a\), \(x>\ln(3/a)\), or \(x<-a/(2e)\), choose a clean point that safely satisfies it, such as \(-1/a\), \(\ln(4/a)\), or \(t/2\) with \(t=\min(1,-a/(2e))\).
- If a parameter-dependent point looks strange, include the sentence that generated it: "It suffices to make ...; hence require ...; therefore choose ...".
- Avoid arbitrary-looking choices unless they are natural special points: endpoints, extrema, \(0\), \(1\), \(2\), \(e\), or points already appearing in the problem.

## Common Templates

Use these templates when turning analysis into teachable proof.

**Zero on both sides of an extremum.** If \(F\) has a minimum \(F(c)<0\), prove two zeros by choosing one point on each side with positive value. On each side, choose the point from a simple lower bound. Example pattern: for \(F(x)=e^x-ax\) with \(a>e\), \(F(\ln a)<0\). On the left, \(x=0\) gives \(F(0)>0\). On the right, seek a bound strong enough to make \(F(x)>0\); if \(e^x\ge 1+x\) is not enough, move to a higher-order or stronger exponential bound and solve the resulting simpler inequality.

**Find a positive value by replacing a weak term.** If \(F(x)=ae^{2x}+(a-2)e^x-x\) and \(0<a<1\), use \(x<e^x\) to get
\[
F(x)>e^x(ae^x+a-3).
\]
It suffices to make \(ae^x+a-3>0\), so require \(x>\ln((3-a)/a)\). Choose a cleaner point such as \(x=\ln(4/a)\), which gives an obviously positive margin.

**Find a negative value on a negative interval.** If \(F(x)=e^x+ax\) on \((-\infty,0)\) with \(a>0\), use \(0<e^x<1\), so
\[
F(x)<1+ax.
\]
It suffices to make \(1+ax\le 0\), hence choose \(x=-1/a\) or any smaller valid point.

**Restrict first, then bound uniformly.** If a derivative contains \((1+x)e^x+a/x\) with \(a<0\), first force \(0<x<1\), then use \((1+x)e^x<2e\). It suffices to make \(2e+a/x<0\), so require \(x<-a/(2e)\). Combine interval requirements by setting \(t=\min(1,-a/(2e))\) and choose \(x=t/2\).

**Transform variables to reveal extrema.** For logarithmic zero problems, use substitutions such as \(u=\ln x\) to turn \(ae^u-u^2=0\) into \(u^2e^{-u}-a=0\). Then study \(g(u)=u^2e^{-u}-a\), locate extrema, and choose sign-changing points by exponential/log bounds rather than by limits alone.

**Replace sequence limits with explicit large-\(n\) choices.** When a proof seems to use \(n\to\infty\) to force a constant, rewrite it as contradiction with a concrete \(n\). If \(q>2\), solve a threshold such as \(2^{n-1}\ge 3/(q-2)\) and choose
\[
n=\left[\log_2\left(\frac{3}{q-2}+1\right)\right]+1.
\]
If \(q<2\), solve the analogous threshold for \(2-q\). Use the same method for constants \(c>1\) or \(c<1\) by choosing \(n\) from inequalities such as \(2^n\ge 1/(c-1)\) or \(2^n\ge 1/(1-c)\).

## Parameter Range Checklist

- Show the domain excludes or includes boundary points correctly.
- Treat zero, equality cases, and endpoints separately.
- For "there exists" conditions, prove both directions:
  - necessary: existence implies the parameter belongs to the claimed range;
  - sufficient: every parameter in the claimed range produces an admissible solution.
- If using a transformed parameter function such as `b=phi(x)`, either prove the exact value range with continuity and monotonicity, or convert it into a zero-point proof with concrete point selection.
- Prefer the zero-point form for Gaokao-style final answers when there is any doubt about grading.

## Writing Style

Write in a concise exam-solution style:

- State definitions and domains before differentiating.
- Give derivative sign changes or a monotonicity table when useful.
- Name the theorem used for existence: usually continuity plus the intermediate value theorem.
- Avoid vague phrases like "obviously it can be reached" or "because it tends to infinity, there must be a solution" in final proof.
- In teaching mode, add one or two sentences explaining the origin of a selected point before substituting it.
- Keep scratch intuition out of the final unless the user asks for explanation.

## Example Pattern

For a problem requiring existence of \(x>0\) such that

\[
\frac{e^x}{\sqrt{x}}=b,
\]

it is fine to analyze the value range of

\[
\phi(x)=\frac{e^x}{\sqrt{x}}.
\]

But in the final answer, after finding \(\min\phi=\sqrt{2e}\), prove sufficiency as follows:

- If \(b\ge\sqrt{2e}\), then \(\phi(1/2)=\sqrt{2e}\le b\).
- Choose a point such as \(x=1/b^2\) when valid, and compute \(\phi(1/b^2)=be^{1/b^2}>b\).
- Since \(\phi\) is continuous, there exists \(x\) between these two points such that \(\phi(x)=b\).

This converts the limit/value-range insight into a concrete, grader-friendly existence proof.
