---
layout: distill
title: "Fairness Audits as Theater: When Metrics Mask Structural Harm"
description: "This blog post examines why contemporary fairness audits fail to prevent algorithmic harm, despite growing adoption. We analyze structural limitations and propose substantive alternatives grounded in participatory accountability."
date: 2025-12-07
future: true
htmlwidgets: true

authors:
- name: Anonymous

bibliography: 2025-12-07-fairness-audits.bib

toc:
- name: Introduction
- name: The Rise and Crisis of Fairness Audits
  subsections:
  - name: What Audits Promise
  - name: What Audits Deliver
- name: Why Current Audits Fail
  subsections:
  - name: Problem 1 - The Metric Selection Problem
  - name: Problem 2 - The Context Collapse Problem
  - name: Problem 3 - The Legitimation Problem
- name: Case Studies in Audit Failure
  subsections:
  - name: Amazon's Hiring Algorithm
  - name: COMPAS Recidivism Assessment
  - name: Healthcare Risk Scores
- name: Beyond Audits - Toward Substantive Accountability
  subsections:
  - name: Participatory Model Cards
  - name: Threshold Advocacy and Context Binding
  - name: Rights-Based Accountability Frameworks
- name: Implications for Practice
- name: Conclusion

---

## Introduction

Machine learning systems are everywhere—and they are broken. Across domains from criminal justice to employment screening to healthcare, algorithms have replicated, amplified, and legitimized historical inequalities. In response, the AI ethics community has converged on a solution: **fairness audits**.

Audits have become the lingua franca of algorithmic accountability. Companies commission them. Regulators expect them. Researchers publish them. The idea is straightforward: measure bias, document findings, demonstrate due diligence, proceed with deployment. Yet despite this explosion in auditing infrastructure, algorithmic harm persists.

This blog post argues that contemporary fairness audits function as **legitimation theater** rather than mechanisms of genuine accountability. We identify three structural problems that prevent audits from preventing harm, then propose alternatives grounded in substantive accountability and participatory oversight.

The stakes are high. As auditing becomes institutionalized, it risks creating a false sense of resolution while marginalizing communities most affected by algorithmic systems. Understanding why audits fail is the first step toward building accountability frameworks that actually work.

## The Rise and Crisis of Fairness Audits

### What Audits Promise

The fairness audit emerged as a response to the reproducibility and integrity crisis in machine learning. After landmark publications—Buolamwini and Gebru's *Gender Shades* (2018), ProPublica's COMPAS investigation (2016), Obermeyer et al. on medical AI (2019)—the research community recognized that algorithmic bias was not incidental but systematic.

Audits promised a solution. By treating algorithms like financial systems or medical devices, audits would:

1. **Measure bias systematically** using rigorous fairness metrics
2. **Identify disparities** before deployment
3. **Document processes** for regulatory compliance
4. **Enable accountability** by creating a paper trail

The appeal is intuitive. Audits are *objective*, *scalable*, and *defensible*. They transform the abstract problem of "fairness" into concrete numbers: disparate impact ratios, false positive rate gaps, calibration indices. A system that passes an audit appears legitimate. Checkboxes are checked. Lawyers are satisfied.

### What Audits Deliver

In practice, audits deliver legitimacy without justice.

Consider the structure of a typical audit:

> 1. A third-party firm is hired
> 2. The firm tests the algorithm against a selection of fairness metrics
> 3. The firm produces a report documenting disparities
> 4. The report is filed away or released to satisfy legal requirements
> 5. The system is deployed or continues operating

This workflow is reassuring precisely because it appears neutral. Yet each step embeds values and choices that shape whether audits actually prevent harm.

**The metric selection problem**: Which fairness metrics to test? Dozens exist, many mathematically incompatible. The choice is not technical—it is political. Testing only group fairness metrics (equal outcome across groups) may miss individual fairness concerns (similar people treated similarly). Testing only predictive parity (equal accuracy across groups) may legitimize systems that amplify existing disparities in outcomes. The audit firm—accountable to the client who hired them—selects metrics convenient to pass.

**The context collapse problem**: Audits extract algorithms from the socio-technical contexts that give them meaning. An algorithm may achieve group fairness in aggregate but fail catastrophically for specific subpopulations (intersectional groups). An algorithm may pass all fairness tests in one jurisdiction but encode biases specific to another's data distributions. Audits typically treat these as edge cases, not failures.

**The legitimation problem**: Once an audit is complete, the system becomes "certified" as fair. This certification creates a false sense of resolution. Decision-makers can point to the audit and claim due diligence was conducted. Communities affected by the system have limited recourse—the audit was done, what more can be done? The legitimacy of the audit becomes a defense against further scrutiny.

## Why Current Audits Fail

### Problem 1 - The Metric Selection Problem

Fairness metrics are not discovered; they are constructed. Each metric encodes assumptions about what fairness means and how it should be measured. The key insight is that **no single metric captures fairness completely**.

Consider a hiring algorithm. We might measure:

- **Demographic parity**: Equal hiring rates across groups (if 60% of applicants are male, hire 60% male employees)
- **Equalized odds**: Equal true positive and false positive rates across groups (equally likely to hire qualified candidates; equally unlikely to hire unqualified ones)
- **Calibration**: If the algorithm predicts someone has a 70% chance of success, they succeed 70% of the time (across groups)
- **Individual fairness**: Similar applicants get similar predictions

These metrics are mathematically incompatible. An algorithm cannot simultaneously satisfy all of them. So auditors must choose.

Who chooses? Typically, the firm conducting the audit—whose client is the company deploying the algorithm. Under this arrangement, auditors face subtle (or not-so-subtle) pressure to select metrics that reveal acceptable levels of bias. If the client is deploying an algorithm that is computationally convenient but happens to disparately impact women, auditors might prioritize demographic parity (which the algorithm likely fails) but de-emphasize calibration (which it might pass). The choice appears technical; in practice, it is strategic.

Real-world example: Amazon's hiring algorithm initially scored candidates on a 0-5 scale and automatically filtered out anyone below 4. After audit, the company discovered the algorithm systematically downscored women. Amazon then... stopped using the score. They didn't change the algorithm; they simply removed the automated filtering. The audit identified the bias but didn't prevent deployment of the underlying biased system—it just made the bias less visible.

### Problem 2 - The Context Collapse Problem

Fairness metrics assume a kind of context-free universalism. A metric is either satisfied or not. But algorithms operate in specific socio-technical contexts that metrics cannot capture.

Consider COMPAS, the recidivism assessment tool. The algorithm predicts who will reoffend based on historical criminal justice data. Audits of COMPAS have revealed:

- **Structural bias**: The algorithm inherits biases from training data shaped by racist policing practices
- **Feedback loops**: Police deploy the algorithm to target neighborhoods, resulting in more arrests in those areas, which then become training data showing higher recidivism, which triggers more enforcement
- **Differential consequences**: A high score for a Black defendant means harsher sentencing; a high score for a white defendant means increased supervision (both harmful, but differently)

No fairness metric—not demographic parity, not equalized odds, not calibration—captures these contextual harms. An algorithm can pass every fairness test while perpetuating systemic racism. This is because metrics measure **properties of the algorithm**. They do not measure **properties of the world**: historical inequalities, ongoing discrimination, power asymmetries between the algorithm and those it affects.

The context collapse problem is particularly acute for algorithmic systems that operate at the intersection of multiple domains. Consider hiring algorithms that use educational credentials as predictors. The algorithm may be internally fair (women and men with the same education are equally likely to be hired). But if the algorithm inherits biases from the educational system—where admissions, funding, and opportunities are unequally distributed—then the algorithm propagates those biases forward. An audit that ignores educational context will miss this structural propagation.

### Problem 3 - The Legitimation Problem

Perhaps the most insidious failure of audits is that they create legitimacy for systems that remain unjust.

When a company hires a reputable firm to audit an algorithm, the company gains several things:

1. **Legal protection**: If sued, the company can point to the audit as evidence of due diligence
2. **Rhetorical power**: The company can claim the system is "fair" (or "as fair as possible")
3. **Internal reassurance**: Employees can believe they are working for an ethical company
4. **Reduced scrutiny**: Once audited, the system faces less external pressure to change

For affected communities, audits often feel like performance. Researchers and advocates may have repeatedly warned about a system's harms. An audit is commissioned. A report is produced. The company claims to take findings seriously. The system remains deployed. What changed? Often, very little—except that the company now has a document testifying to awareness of the problem.

This is the legitimation trap: audits create accountability theater. They make it appear that someone is responsible for ensuring fairness. But responsibility without power is theater. Audits typically have no enforcement mechanisms. If an audit finds bias, there is no requirement to fix it. The company can acknowledge the finding, claim context makes it unavoidable, and continue deploying.

Worse, audits can *prevent* further accountability by creating a sense that the system has been properly scrutinized. Regulators who see an audit report may conclude that no further investigation is needed. Communities may be too exhausted by the audit process to push for additional changes. The audit closes the door on demanding more.

## Case Studies in Audit Failure

### Amazon's Hiring Algorithm

Amazon's recruiting tool was trained on 10 years of historical hiring data. The algorithm learned to predict who would be hired and who would succeed in the role. Like most machine learning systems trained on historical data, it learned to replicate existing hiring patterns—which historically favored men, particularly in technical roles.

An audit, conducted internally, found the algorithm systematically downscored women applicants. Amazon's response: stop using the score for final hiring decisions, but keep using it for other purposes. The algorithm remained deployed; only its application changed.

What did the audit accomplish? It created awareness of the bias (which was known to researchers and advocates beforehand). It did not prevent the bias from influencing hiring (the algorithm still scores women lower; the company just doesn't automatically reject based on the score). It did allow Amazon to claim it took fairness seriously.

The deeper issue: Amazon's hiring data reflected decades of underrepresentation of women in tech. No audit of the algorithm could fix this upstream bias. An adequate response would have required addressing why the training data was skewed—a question audits typically don't ask. An audit that examined only the algorithm and not the historical data that shaped it was always going to miss the root cause.

### COMPAS Recidivism Assessment

ProPublica's investigation of COMPAS found that the algorithm had different false positive rates for Black and white defendants: Black defendants were 45% more likely to be falsely labeled as high-risk. Despite ProPublica's analysis, Northpointe (COMPAS's developer) claimed the algorithm was fair because it had similar predictive accuracy across racial groups (calibration).

Subsequent audits found conflicting results depending on which fairness metrics were used. By some metrics, COMPAS was fair. By others, it was not. Each audit could cherry-pick metrics to support a predetermined conclusion.

Meanwhile, COMPAS remained in use across U.S. courts, influencing bail decisions, sentencing, and parole determinations. The debate over which fairness metric to use—carried out in academic papers and audit reports—had no impact on deployment. The algorithm continued to shape human lives while researchers argued about how to measure its bias.

The audit failure here was not methodological but structural. The choice of which metric to believe was decided not by auditors but by judges and policy-makers, based on which metric was most convenient. An audit that could not compel acceptance of its findings was an audit that could not prevent harm.

### Healthcare Risk Scores

Hospitals and insurance companies use algorithms to predict patient outcomes and allocate resources. One widely-used system predicted mortality risk to identify patients needing palliative care. When audited, the algorithm was found to systematically underestimate risk for Black patients.

Why? The algorithm was trained on healthcare cost as a proxy for illness severity. Since Black patients receive systematically lower healthcare spending due to structural racism in medicine, the algorithm learned to associate Blackness with lower disease severity. When exposed to Black patients with the same objective health status as white patients, the algorithm predicted better outcomes.

This bias had profound consequences: Black patients were less likely to be identified for palliative care and early intervention. The algorithm replicated and amplified existing racial disparities in healthcare.

After the audit, the algorithm was updated to remove race from the training features. But this didn't solve the problem—the bias was not in the race variable itself, but in the proxy (cost) used for the outcome. Removing race was like treating a symptom while ignoring the disease. An adequate response would have required reconstructing the outcome variable and retraining on better data, which would have required collaboration with clinicians, patients, and healthcare systems. It would have required examining why Black patients receive less healthcare spending in the first place. Instead, the quick fix was applied, the audit was completed, and the algorithm continued to encode historical bias.

## Beyond Audits - Toward Substantive Accountability

If audits fail, what works? The answer is not "better metrics" or "more rigorous audits." The answer is **participation**.

### Participatory Model Cards

Traditional audits are conducted by experts (auditors) examining systems designed by experts (engineers) based on data selected by experts (product teams). Communities affected by the systems have no role.

An alternative is participatory model cards: documents that describe the algorithm's purpose, training data, performance, limitations, and known biases—co-produced by engineers, domain experts, affected communities, and ethicists.

A participatory model card for a hiring algorithm might include:

- **Purpose**: Identify qualified candidates (written by product team)
- **Data sources**: Historical hiring records, with analysis of how the training data encodes historical biases (written collaboratively)
- **Intended use**: Initial screening to identify candidates for human review (written by HR)
- **Known failures**: The algorithm systematically downscores women with engineering backgrounds due to underrepresentation in the training data (identified by auditors and affected communities working together)
- **Conditions for deployment**: Only use the algorithm if the hiring team receives training on its limitations; only use as initial screening, never for final decisions; regularly audit for bias; create appeals process for candidates who wish to challenge the score (negotiated with affected communities)

The key difference: a participatory process creates accountability to affected communities, not just to the company deploying the system.

### Threshold Advocacy and Context Binding

Some fairness metrics may be useful not as universal measures of fairness, but as **threshold advocates**: metrics that flag when a system is clearly unacceptable.

For instance, a metric might state: "If the false positive rate for one group is more than 20% higher than for other groups, the system should not be deployed without explicit written justification." This is not claiming to measure fairness perfectly; it is drawing a line against egregious harm.

Threshold advocacy pairs metrics with **context binding**: making explicit the contexts in which the algorithm can be deployed, and the conditions under which it must be re-audited.

An algorithm might be approved for use in employment screening in one domain but not another, because the contexts are different. An algorithm might be approved conditionally, with requirements to audit quarterly, to maintain an appeals process, to involve affected communities in oversight.

This approach treats audits not as one-time certifications but as the beginning of ongoing accountability.

### Rights-Based Accountability Frameworks

Rather than asking "Is this algorithm fair?" audits could ask "Are the rights of people affected by this algorithm protected?"

A rights-based framework might include:

1. **Right to know**: Affected people should know if and how an algorithm is used to make decisions about them
2. **Right to understand**: The algorithm's logic should be explainable in terms meaningful to those affected
3. **Right to challenge**: Affected people should be able to contest algorithmic decisions and have challenges reviewed by a human with authority to override
4. **Right to remedy**: If an algorithm causes harm, affected people should have access to compensation or system change
5. **Right to participate**: Communities should have voice in decisions about whether and how algorithms are deployed

These rights cannot be verified by auditing the algorithm alone. They require examining the socio-technical system: Does the company actually tell people when algorithms are used? Can they understand the explanations provided? Can they challenge decisions? Can they receive remedy? Are they actually participating in oversight?

Rights-based audits would be messier than metric-based audits. They would require qualitative research, community engagement, and ongoing monitoring. But they would be more likely to prevent harm because they focus on what actually matters to affected communities.

## Implications for Practice

For practitioners, the message is clear: **audits alone are insufficient**. But audits are not useless—they are just incomplete.

**For companies deploying algorithms**:
- Don't use an audit as a substitute for accountability
- Commission audits, but involve affected communities in the process
- Use audit findings not as a sign the system is ready to deploy, but as the starting point for governance design
- Create accountability structures: oversight boards, appeals processes, regular re-auditing
- Be transparent about audit findings and limitations

**For auditors and researchers**:
- Be explicit about the values embedded in your choice of fairness metrics
- Consider multiple metrics and document trade-offs, not just those the algorithm passes
- Examine the socio-technical context, not just the algorithm
- Engage affected communities in auditing, not just as data subjects
- Decline to conduct audits when you lack power to ensure findings lead to change

**For regulators and policymakers**:
- Don't accept audits as evidence of compliance
- Require procedural safeguards (appeals processes, community oversight, transparency) not just technical safeguards (metrics)
- Build in incentives for companies to genuinely address audit findings, not just acknowledge them
- Support community organizations in conducting independent audits
- Create legal liability for algorithmic harms, regardless of audit status

**For affected communities**:
- Audits are not accountability—they are theater
- Demand participation in audit processes, don't accept being studied
- Push for rights-based frameworks, not metric-based ones
- Document harms and build alternative knowledge systems
- Connect with other communities affected by algorithms; collective pressure is more effective than individual appeals

## Conclusion

Fairness audits have become the default mechanism for algorithmic accountability. Yet they fail to prevent harm because they treat fairness as a technical problem solvable through measurement, when it is fundamentally a political problem requiring power-sharing.

An algorithm that measures its own fairness and declares itself fair is not making a meaningful claim. A company that audits its own algorithms and publishes findings it selects is performing transparency without practicing it. A regulator that accepts audits as evidence of compliance is delegating its authority.

The alternative is uncomfortable. It requires admitting that algorithms cannot be made "fair" if the training data encodes historical injustice. It requires involving communities in technical decisions, which is slower and messier than expertise-driven processes. It requires giving affected people power to say "no" to systems, not just to participate in their design.

But this is what genuine accountability looks like. Not audits that certify systems as fair. But systems designed with affected communities, governed by affected communities, and changed when affected communities say they're causing harm.

The work of building trustworthy AI is not the work of auditors measuring systems. It is the work of power-sharing and accountability that algorithms can only support, not substitute for.

