# Insights: Superstore Sales Analysis

**KOUAME Koffi Fidèle** · Data Analysis Internship

Every figure below is computed in section 5 of `Task1_Sales_Analysis.ipynb`.

---

## 1. Technology leads on revenue, but Furniture is where the margin problem is

Technology carries **38.4% of total sales**, the largest of the three
categories. But the ranking changes on profitability: **Furniture has the
weakest margin at 6.9%**, roughly half of Technology's.

Furniture is therefore selling volume without converting it into profit. It is
the category to examine on pricing and discounting, not on demand. A
sales-only ranking would have marked it as healthy.

## 2. Nearly one order in four loses money

**12,544 orders out of 51,290, that is 24.5%, have negative profit.**

This is the largest finding in the dataset and it is invisible in any total,
because the profitable orders subsidise the loss-making ones. Total profit of
1.47M is a net figure that conceals a substantial gross loss.

It is also the reason negative profit was deliberately **not** removed during
cleaning. Treating it as an outlier would have inflated total profit and hidden
the problem entirely.

## 3. Sales are strongly seasonal, and the pattern is exploitable

**December is the strongest month, February the weakest, and the peak sells
about 2.5 times the trough.**

A ratio that large is not noise. It is enough to justify planning inventory,
staffing and cash flow around the seasonal shape rather than against a flat
annual average. Planning to the mean guarantees being short in December and
overstocked in February.

## 4. Revenue is spread across regions, but profitability is not

**Central leads on sales with 22% of the total. Southeast Asia converts its
revenue at a margin of only 2.0%**, against 26.6% in Canada.

A region can be busy and barely profitable. This is why Chart 5 plots sales and
margin side by side: a sales-only ranking would have presented Southeast Asia
as a success on the strength of its 7% revenue share.

## 5. Revenue is concentrated in a small part of the catalogue

The store sells **3,788 distinct products**, but revenue is concentrated in a
small minority of them.

The long tail carries inventory cost, warehouse space and administrative
overhead while returning little. It is the natural target for a
range-rationalisation exercise, and the analysis above identifies which products
would survive it.

---

## What I would do next

Three questions this analysis raises and cannot answer:

**Test whether discount explains the loss-making orders.** The full dataset
carries a Discount column that this task does not use. Correlating discount
against negative profit would turn insight 2 from a symptom into a diagnosis.

**Separate seasonality from growth.** The moving average in Chart 2 suggests
both are present. A time series decomposition would say how much of the December
peak is seasonal and how much is underlying trend.

**Check whether the loss-making orders concentrate in Furniture and in Southeast
Asia.** If insights 1, 2 and 4 are the same problem seen three different ways,
then one intervention fixes all three. If they are independent, three are needed.
