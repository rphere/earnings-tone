# Earnings call tone vs. next-day stock move

**Live dashboard: https://rphere.github.io/earnings-tone/**

How does executive tone on earnings calls relate to the next day's stock price? This dashboard checks it for big tech
companies (Apple, Microsoft, Alphabet, Amazon, Meta and Nvidia), from Q4 2023 to Q3 2026.

## What it shows

- **Headline numbers:** overall accuracy, plus how many of the next-day rises and falls the tone signal caught. These are
  compared with a baseline of always guessing that the stock would rise.
- **How often the tone called it:** a 2×2 table of tone (more or less upbeat than usual) against next-day direction (rose or fell).
- **Call by call, over time:** one bar per earnings call, grouped by the quarter it reported on. Bar height is the
  next-day move, and colour is the tone.
- **Every call:** a sortable table with a short executive quote from each call's Q&A.

You can filter every view by company.

## Method

1. **Tone:** Alpha Vantage provides earnings call transcripts with a sentiment score (−1 to +1) for each speaker turn.
   A call's tone is the average score of the executives' answers in the analyst Q&A.
2. **Compared with usual:** each call is labelled *more upbeat than usual* or *less upbeat than usual*, relative to
   that company's median score.
3. **Next-day move:** the stock's return on the first trading day after the call. That's the same day for a
   pre-market call and the following day for an after-close call.
4. **Quotes:** the snippet and summary in the table were picked by Claude Haiku from each call's Q&A.

## Caveats

- **Look-ahead in "usual":** a company's median is computed across all the calls shown, including later ones. Treat
  the results as a first look, not a tradable signal.
- **Small sample:** about a dozen calls per company. Differences of a few percentage points are well within chance.
- **Next-day moves only:** these reflect the earnings results and guidance as well as tone, and the analysis doesn't
  separate them.
- **Not investment advice.**

## About this repo

This repo holds only the published dashboard, a single self-contained `index.html` that loads Plotly from its CDN. The
data pipeline that builds the page (transcript fetching, sentiment scoring and price reactions) lives in a separate
private project. Each time the page is rebuilt with new earnings calls, the new `index.html` is committed here, and
GitHub Pages redeploys it.
