<div align="center">

# AI Signal Board — Fork Experiment

**AI News Radar · RSS / OPML · GitHub Actions**

![Fork](https://img.shields.io/badge/Repository-Fork-6E7781?style=flat-square&logo=github)
![Python](https://img.shields.io/badge/Pipeline-Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Actions](https://img.shields.io/badge/Automation-GitHub%20Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

A fork-based experiment built from [`LearnPrompt/ai-news-radar`](https://github.com/LearnPrompt/ai-news-radar).

</div>

## Repository Context

This repository is **not the original AI News Radar project**. The upstream architecture and original implementation belong to LearnPrompt and its contributors.

I keep this fork as a practical experiment in building a personal **AI information radar**: collect multiple sources, normalize them, keep a short time window, and publish a lightweight signal board that can update automatically.

## Local Experiment Scope

The current fork explores:

- multi-source AI / technology news aggregation;
- OPML-based RSS ingestion;
- 24-hour rolling views;
- source grouping and deduplication;
- bilingual title presentation;
- source health / failure reporting;
- scheduled updates through GitHub Actions;
- a static browser-based output that does not require a long-running application server.

## Data Flow

```text
Web sources + RSS / OPML
          |
          v
   Update pipeline
          |
     normalize / dedup
          |
          v
      JSON outputs
          |
          v
   Static signal board
```

## Local Run

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
cp feeds/follow.example.opml feeds/follow.opml
python scripts/update_news.py --output-dir data --window-hours 24 --rss-opml feeds/follow.opml
python -m http.server 8080
```

Then open `http://localhost:8080`.

On Windows, use the equivalent virtual-environment activation command.

## Automation

The repository includes a GitHub Actions workflow for scheduled refreshes. Private RSS subscriptions or API credentials should be supplied through environment variables / repository secrets and should never be committed.

## Why It Is in My Portfolio

This fork is useful as an **information-engineering exercise**: turning a noisy stream of public information into a repeatable collection, filtering, monitoring, and publishing pipeline.

## Upstream

Canonical project: [`LearnPrompt/ai-news-radar`](https://github.com/LearnPrompt/ai-news-radar)

Use upstream documentation for the original project, official feature set, licensing, and current releases.

## Status

`Fork-based Experiment` · `Information Pipeline` · `Automation Practice`
